# jmore(8)
FreeBSD Jail listing and managing utility.

## FAQ

### Why `jmore(8)` name?
Initially it was named `jless(8) and below is the reasoning for that choice ...

Because that is the closest thing to FreeBSD base system `jls(8)` command and it has some reference for other known `less(8)` command.

But **seschwar** from `lobste.rs` page made me aware that there already is a `jless` project available - command line JSON viewer written in Rust - thank You for that.

So as `less(8)` is `more(8)` and `more(8)` is `less(8)` - I took the decision to rename it from `jless(8)` to `jmore(8)` to avoid confusion.


### Why another `jail(8)` containers listing/managing tool?
Because builtin `jls(8)` is very limited and does not display VNET IP(s) and interfaces.

Also because - if You do now want to use full blown `jail(8)` manager such as BastilleBSD - which is very good by the way - the base system tools are just too limited for comfort work.

I also needed a tool that will allow me to fast start/stop/restart FreeBSD `jail(8)` containers with minimal typing - more time to focus on what matters.

### Does it support listing BastilleBSD Jails?

Yes - it reads `/usr/local/etc/bastille/bastille.conf` config and also checks `BAST_DIR` for `jail(8)` containers.

### Is it tested?

Yes - its a modified and improved version of `https://github.com/vermaden/scripts/blob/master/jails.sh` that I already used for quite some time.


## Description

Usage `help` info from the `jmore(8)` command below.

```
% jmore help
usage:
  jmore            list jail(8) containers
  jmore -a         list jail(8) containers with all IP(s)
  jmore -h         show help
  jmore --help     show help
  jmore help       show help
  jmore version    show version

manage:
  jmore <JAILNAME> start
  jmore <JAILNAME> restart
  jmore <JAILNAME> stop
  jmore <JAILNAME> status
  jmore <JAILNAME> console
  jmore <JAILNAME> shell
  jmore <JAILNAME> jexec

shorts:
  jmore <JAILNAME> u   UP ------> alias for start
  jmore <JAILNAME> d   DOWN ----> alias for stop
  jmore <JAILNAME> r   RESTART -> alias for restart
  jmore <JAILNAME> c   CONSOLE -> alias for console|shell|jexec
  jmore <JAILNAME> s   STATUS --> alias for status
```

... and some fancy ASCII logo.

```
% jmore help
                                          __ ____ __
        ___                              / //    \\ \
       /__/__ __ _   ____   __ __ ____  / //  /  / \ \
      /  //       \ /    \ /  /_//  _ \/ / \     \ / /
     /  //  /  /  //  /  //  /  /  ___/\ \ /  /  // /
  __/  //__/__/__/ \____//__/   \____/  \_\\____//_/
 /____/

jmore(8) 0.1 2024/11/22

```

Example output from `jmore(8)` listing usage.

```
% jmore
JAIL       JID  TYPE  VER     DIR                    IFACE     IP(s)
----       ---  ----  ---     ---                    -----     -----
classic    5    std   13.2-R  /jail/classic          em0       10.0.0.199/32
fbsdjail   -    std   13.1-R  /jail/fbsdjail         wlan0     10.0.0.43
ctld-two   -    vnet  13.2-R  /jail/ctld-two         ${if}b    -
ctld       -    vnet  13.2-R  /jail/ctld             ${if}b    -
iscsi      -    vnet  13.2-R  /jail/iscsi            ${if}b    -
minecraft  -    std   -       [GONE]/jail/minecraft  em0       10.0.0.210
minio      -    std   14.0-R  /jail/minio            em0       10.0.0.133
nfsd       3    vnet  14.1-R  /jail/nfsd             epair99b  10.1.1.99/24
other      -    std   14.1-R  /jail/other            em0       10.0.0.199
sambajail  -    vnet  14.1-R  /jail/sambajail        ${if}b    -
unfs3      -    vnet  14.1-R  /jail/unfs3            ${if}b    -

```

EOF
