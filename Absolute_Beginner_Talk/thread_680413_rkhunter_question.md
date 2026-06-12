---
title: "rkhunter question?"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2008-01-27
rkhunter terminal:
 /bin/uname                                               [ OK ]
    /bin/which                                               [ OK ]
    /bin/dash                                                [ OK ]
    /usr/bin/awk                                             [ Warning ]
    /usr/bin/basename                                        [ OK ]
    /usr/bin/chattr                                          [ OK ]
    /usr/bin/cut                                             [ OK ]
    /usr/bin/diff                                            [ OK ]
    /usr/bin/dirname                                         [ OK ]
    /usr/bin/dpkg                                            [ OK ]
    /usr/bin/dpkg-query                                      [ OK ]
    /usr/bin/du                                              [ OK ]
    /usr/bin/env                                             [ OK ]
    /usr/bin/file                                            [ OK ]
    /usr/bin/find                                            [ OK ]
    /usr/bin/GET                                             [ OK ]
    /usr/bin/groups                                          [ OK ]
    /usr/bin/head                                            [ OK ]
    /usr/bin/id                                              [ OK ]
    /usr/bin/killall                                         [ OK ]
    /usr/bin/last                                            [ OK ]
    /usr/bin/lastlog                                         [ OK ]
    /usr/bin/ldd                                             [ OK ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/locate                                          [ OK ]
    /usr/bin/logger                                          [ OK ]
    /usr/bin/lsattr                                          [ OK ]
    /usr/bin/lsof                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pstree                                          [ OK ]
    /usr/bin/rkhunter                                        [ OK ]
    /usr/bin/runcon                                          [ OK ]
    /usr/bin/sha1sum                                         [ OK ]
    /usr/bin/size                                            [ OK ]
    /usr/bin/slocate                                         [ OK ]
    /usr/bin/sort                                            [ OK ]
    /usr/bin/stat                                            [ OK ]
    /usr/bin/strace                                          [ OK ]
    /usr/bin/strings                                         [ OK ]
    /usr/bin/sudo                                            [ OK ]
    /usr/bin/tail                                            [ OK ]
    /usr/bin/test                                            [ OK ]
    /usr/bin/top                                             [ OK ]
    /usr/bin/touch                                           [ OK ]
    /usr/bin/tr                                              [ OK ]
    /usr/bin/uniq                                            [ OK ]
    /usr/bin/users                                           [ OK ]
    /usr/bin/vmstat                                          [ OK ]
    /usr/bin/w                                               [ OK ]
    /usr/bin/watch                                           [ OK ]
    /usr/bin/wc                                              [ OK ]
    /usr/bin/wget                                            [ OK ]
    /usr/bin/whatis                                          [ OK ]
    /usr/bin/whereis                                         [ OK ]
    /usr/bin/which                                           [ OK ]
    /usr/bin/who                                             [ OK ]
    /usr/bin/whoami                                          [ OK ]
    /usr/bin/gawk                                            [ Warning ]
    /usr/bin/lwp-request                                     [ OK ]
    /usr/bin/w.procps                                        [ OK ]
    /sbin/depmod                                             [ OK ]
    /sbin/ifconfig                                           [ OK ]
    /sbin/ifdown                                             [ OK ]
    /sbin/ifup                                               [ OK ]
    /sbin/init                             
........[/CODE]

and the log...
[```

[05:14:46] /bin/su                                           [ OK ]
[05:14:46] /bin/touch                                        [ OK ]
[05:14:46] /bin/uname                                        [ OK ]
[05:14:46] /bin/which                                        [ OK ]
[05:14:46] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[05:14:46] /bin/dash                                         [ OK ]
[05:14:46] /usr/bin/awk                                      [ Warning ]
[05:14:46] Warning: The file properties have changed:
[05:14:46]          File: /usr/bin/awk
[05:14:46]          Current hash: 7bd14d67ff98ae633f95ef985fa944c1a9904bf5
[05:14:46]          Stored hash : 1a77edf9273da7a55843f941002f480fbada42de
[05:14:46] /usr/bin/basename                                 [ OK ]
[05:14:46] /usr/bin/chattr                                   [ OK ]
[05:14:46] /usr/bin/cut                                      [ OK ]
[05:14:46] /usr/bin/diff                                     [ OK ]
[05:14:47] /usr/bin/dirname                                  [ OK ]
[05:14:47] /usr/bin/dpkg                                     [ OK ]
[05:14:47] /usr/bin/dpkg-query                               [ OK ]
[05:14:47] /usr/bin/du                                       [ OK ]
[05:14:47] /usr/bin/env                                      [ OK ]
[05:14:47] /usr/bin/file                                     [ OK ]
[05:14:47] /usr/bin/find                                     [ OK ]
[05:14:47] /usr/bin/GET                                      [ OK ]
[05:14:47] /usr/bin/groups                                   [ OK ]
[05:14:47] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[05:14:47] /usr/bin/head                                     [ OK ]
[05:14:47] /usr/bin/id                                       [ OK ]
[05:14:48] /usr/bin/killall                                  [ OK ]
[05:14:48] /usr/bin/last                                     [ OK ]
[05:14:48] /usr/bin/lastlog                                  [ OK ]
[05:14:48] /usr/bin/ldd                                      [ OK ]
[05:14:48] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[05:14:48] /usr/bin/less                                     [ OK ]
[05:14:48] /usr/bin/locate                                   [ OK ]
[05:14:48] /usr/bin/logger                                   [ OK ]
[05:14:48] /usr/bin/lsattr                                   [ OK ]
[05:14:48] /usr/bin/lsof                                     [ OK ]
[05:14:48] /usr/bin/md5sum                                   [ OK ]
[05:14:48] /usr/bin/newgrp                                   [ OK ]
[05:14:49] /usr/bin/passwd                                   [ OK ]
[05:14:49] /usr/bin/perl                                     [ OK ]
[05:14:49] /usr/bin/pstree                                   [ OK ]
[05:14:49] /usr/bin/rkhunter                                 [ OK ]
[05:14:49] /usr/bin/runcon                                   [ OK ]
[05:14:49] /usr/bin/sha1sum                                  [ OK ]
[05:14:49] /usr/bin/size                                     [ OK ]
[05:14:49] /usr/bin/slocate                                  [ OK ]
[05:14:49] /usr/bin/sort                                     [ OK ]
[05:14:49] /usr/bin/stat                                     [ OK ]
[05:14:49] /usr/bin/strace                                   [ OK ]
[05:14:50] /usr/bin/strings                                  [ OK ]
[05:14:50] /usr/bin/sudo                                     [ OK ]
[05:14:50] /usr/bin/tail                                     [ OK ]
[05:14:50] /usr/bin/test                                     [ OK ]
[05:14:50] /usr/bin/top                                      [ OK ]
[05:14:50] /usr/bin/touch                                    [ OK ]
[05:14:50] /usr/bin/tr                                       [ OK ]
[05:14:50] /usr/bin/uniq                                     [ OK ]
[05:14:50] /usr/bin/users                                    [ OK ]
[05:14:50] /usr/bin/vmstat                                   [ OK ]
[05:14:50] /usr/bin/w                                        [ OK ]
[05:14:51] /usr/bin/watch                                    [ OK ]
[05:14:51] /usr/bin/wc                                       [ OK ]
[05:14:51] /usr/bin/wget                                     [ OK ]
[05:14:51] /usr/bin/whatis                                   [ OK ]
[05:14:51] /usr/bin/whereis                                  [ OK ]
[05:14:51] /usr/bin/which                                    [ OK ]
[05:14:51] /usr/bin/who                                      [ OK ]
[05:14:51] /usr/bin/whoami                                   [ OK ]
[05:14:51] /usr/bin/gawk                                     [ Warning ]
[05:14:51] Warning: The file '/usr/bin/gawk' exists on the system, but it is not present in the rkhunter.dat file.
[05:14:51] /usr/bin/lwp-request                              [ OK ]
[05:14:51] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[05:14:51] /usr/bin/w.procps                                 [ OK ]
[05:14:51] /sbin/depmod                                      [ OK ]
[05:14:52] /sbin/ifconfig                                    [ OK ]
[05:14:52] /sbin/ifdown                                      [ OK ]
[05:14:52] /sbin/ifup                      
```

probably nothing to worry but what is it?

---

### Post by gvartser on 2008-01-28
Have you updated installed between rkhunter executions?

I'm thinking of awk and gawk.

Best regz,
/g

---

### Post by NickD-NLUG on 2008-03-07
I've just had this too, with the same hashes... either we've been compromised by the same attack or are encountering the same error.

Did you find a solution?

---

### Post by NickD-NLUG on 2008-03-07
Sigh, I'm sorry for posting so rashly, I've looked at this for about a minute and think I've figured out what's happened.  ( My error is doubly compounded as I asked this question in another thread ).

Looking at the program in question, /usr/bin/awk, it's actually a symbolic link to /etc/alternatives/awk :

root@host:/usr/bin# ls -l awk
lrwxrwxrwx 1 root root 21 2007-03-06 06:13 awk -> /etc/alternatives/awk

This in turn in a symbolic link to /usr/bin/gawk

root@host:/usr/bin# ls -l /etc/alternatives/awk
lrwxrwxrwx 1 root root 13 2008-03-06 09:52 /etc/alternatives/awk -> /usr/bin/gawk

So that any program or user using the default "awk" program actually ends up using gawk.

Looking at the man page of rkhunter it uses "SHA-1" hashes by default, so I can use "sha1sum" to see the hashes that rkhunter uses of the relevant files in /usr/bin :

root@host:/usr/bin# sha1sum ./*awk*
7bd14d67ff98ae633f95ef985fa944c1a9904bf5  ./awk
7bd14d67ff98ae633f95ef985fa944c1a9904bf5  ./gawk
335d763a47b86f61ea957735829ffa1048f3fa8f  ./igawk
1a77edf9273da7a55843f941002f480fbada42de  ./mawk
7bd14d67ff98ae633f95ef985fa944c1a9904bf5  ./nawk
790d4a0fe7da96b3f4df4fc8a94f1d9d60eaf9e5  ./pgawk

gawk and awk have the same SHA-1 hash, because awk just points to gawk.  nawk points to /etc/alternatives/awk too, which is why that also has the same output.

Looking at the original error:

Warning: The file properties have changed:                                                                                                                                                     
         File: /usr/bin/awk                                                                                                                                                            
         Current hash: 7bd14d67ff98ae633f95ef985fa944c1a9904bf5                                                                                                                              
         Stored hash : 1a77edf9273da7a55843f941002f480fbada42de

You'll see that the old hash was 1a77edf..... and if you look at the sha1sum output above, that's the SHA-1 hash for mawk.

So what's happened if that for our systems the symbolic link for /etc/alternatives/awk used to point to /usr/bin/mawk, but something ( I don't know what ) changed that symbolic link to point to /usr/bin/gawk.  As /usr/bin/awk points to /etc/alternatives/awk, that means that the hash for /usr/bin/awk has changed.  However because of the symbolic links the reason for the change is hidden from rkhunter, so it reports that the actual program has changed.

Nothing to worry about, ignore the error *as long as you've got the hashes above*.

There... once I looked at it properly it took me longer to write this up than figure out what the problem was.... ;)

---

