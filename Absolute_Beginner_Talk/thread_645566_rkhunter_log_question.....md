---
title: "rkhunter log question....?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-12-20
i got some more warnings than the usual...:
probably it is something usual but im not sure.
```
.......................
[13:58:48] /bin/egrep                                        [ OK ]
[13:58:48] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[13:58:49] /bin/fgrep                                        [ OK ]
[13:58:49] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[13:58:49] /bin/grep                                         [ OK ]
[13:58:49] /bin/ip                                           [ OK ]
[13:58:49] /bin/kill                                         [ OK ]
..............................
13:58:50] /bin/which                                        [ OK ]
[13:58:50] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[13:58:50] /bin/dash                                         [ OK ]
[13:58:51] /usr/bin/awk                                      [ OK ]
[13:58:51] /usr/bin/basename                                 [ OK ]
...............................
[13:58:52] /usr/bin/GET                                      [ OK ]
[13:58:52] /usr/bin/groups                                   [ OK ]
[13:58:52] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[13:58:52] /usr/bin/head                                     [ OK ]
................................
[13:58:52] /usr/bin/ldd                                      [ OK ]
[13:58:52] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[13:58:52] /usr/bin/less                                     [ OK ]
..............................
[13:58:53] /usr/bin/lynx                                     [ Warning ]
[13:58:53] Warning: The file '/usr/bin/lynx' exists on the system, but it is not present in the rkhunter.dat file.
[13:58:53] /usr/bin/md5sum                                   [ OK ]
[13:58:53] /usr/bin/newgrp                                   [ OK ]
.................................
[13:58:55] /usr/bin/lwp-request                              [ OK ]
[13:58:55] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[13:58:55] /usr/bin/lynx.stable                              [ Warning ]
[13:58:55] Warning: The file '/usr/bin/lynx.stable' exists on the system, but it is not present in the rkhunter.dat file.
[13:58:55] /usr/bin/w.procps                                 [ OK ]
................................
[13:58:57] /usr/sbin/adduser                                 [ OK ]
[13:58:57] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[13:58:57] /usr/sbin/chroot                                  [ OK ]
...............................
13:59:15]   Performing check for possible rootkit strings
[13:59:15] Info: Starting test name 'possible_rkt_strings'
[13:59:15] Warning: Checking for possible rootkit strings    [ Warning ]
[13:59:15]          No system startup files found.
...............................
[13:59:24] Info: Starting test name 'startup_malware'
[13:59:24]   Checking for local startup files                [ Warning ]
[13:59:24] Warning: No local startup files found.
.................................
[13:59:26] Info: Starting test name 'filesystem'
[13:59:26] Info: SCAN_MODE_DEV set to 'THOROUGH'
[13:59:35]   Checking /dev for suspicious file types         [ Warning ]
[13:59:35] Warning: Suspicious file types found in /dev:
[13:59:35]          /dev/shm/ATISHM00: data
[13:59:36]   Checking for hidden files and directories       [ Warning ]
[13:59:36] Warning: Hidden directory found: /etc/.java
[13:59:36] Warning: Hidden directory found: /dev/.static
[13:59:36] Warning: Hidden directory found: /dev/.udev
[13:59:36] Warning: Hidden directory found: /dev/.initramfs
..................................


```

---

### Post by wormser on 2007-12-26
I know there are some warnings that are false positive with rkhunter.  I ran it and yours looked a bit different.  Here are my warnings.

>  Performing filesystem checks

    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]



Install chkrootkit and see what it says.  Post the results.

---

