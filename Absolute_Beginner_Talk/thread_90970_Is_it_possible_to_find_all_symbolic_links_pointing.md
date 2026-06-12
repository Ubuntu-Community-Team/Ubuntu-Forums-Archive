---
title: "Is it possible to find all symbolic links pointing to a particular file?"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by Akhran on 2005-11-16
Is there a way to find all symbolic links pointing to a particular file? Eg. /test/filea -> /etc/init.d/testfile
/bin/fileb -> /etc/init.d/testfile
/etc/init.d/rC.d/filec -> /etc/init.d/testfile

filea, fileb and filec are symbolic links all pointing to the same file /etc/init.d/testfile. Is there any command to find all the symbolic links (filea, fileb and filec in this case)that are pointing to testfile?

Thanks !

---

### Post by oskude on 2005-11-16
very interesting question...
i assume that a file doesnt know who has a link to it...
so i came up with this dirty one-liner```
sudo ls -lR / 2>/dev/null | grep "/etc/init.d/testfile"
```
it lists all files recursively from / (error messages are send to /dev/null),  and grep only output lines containing "/etc/init.d/testfile"

cheers
osku[de]

---

### Post by oskude on 2005-11-16
doh,

my one-liner dont show the path to the found file and i started to think that "find" should be able to do this... "man find"...
```
sudo find / -lname /etc/init.d/testfile
```

:rolleyes:

---

### Post by Akhran on 2005-11-19
working directory : /etc/
lrwxrwxrwx 1 root root 15 2005-11-06 10:35 S19slapd -> ../init.d/slapd

When I do a find with

find / -mount -lname /etc/init.d/slapd

there is no result returned.

[QUOTE=oskude]doh,

my one-liner dont show the path to the found file and i started to think that "find" should be able to do this... "man find"...
```
sudo find / -lname /etc/init.d/testfile
```

:rolleyes:[/QUOTE]

---

### Post by oskude on 2005-11-19
[QUOTE=Akhran]working directory : /etc/
lrwxrwxrwx 1 root root 15 2005-11-06 10:35 S19slapd -> ../init.d/slapd

When I do a find with

find / -mount -lname /etc/init.d/slapd

there is no result returned.[/QUOTE]
"/etc/init.d/slapd" is NOT the same as "../init.d/slapd"
if that "S19slapd" was made by an official ubuntu package, contact the author and tell him/her to NOT to use relative paths ;)

or maybe its a "bug", or we need "feature request" for "find" to allso find relative paths where the destination match the -lname...

edit:
found a "workaround", first get your inode number of of the target file```
ls -i /etc/init.d/slapd
```
and then find with that inode number```
find / -follow -inum <inode number>
```
but beware, we should somehow exclude /dev and /proc dirs ! see my test```
osku@klotz:~$ ls -i testfile
146576 testfile
osku@klotz:~$ find / -follow -inum 146576 2>/dev/null
/dev/fd/3/bar1/bar2/fileb
/dev/fd/3/bar1/filea
/dev/fd/3/bar1/relative-link
/dev/fd/3/testfile
/.dev/fd/3/bar1/bar2/fileb
/.dev/fd/3/bar1/filea
/.dev/fd/3/bar1/relative-link
/.dev/fd/3/testfile
/home/osku/bar1/bar2/fileb
/home/osku/bar1/filea
/home/osku/bar1/relative-link
/home/osku/testfile
/proc/self/task/10586/fd/3/bar1/bar2/fileb
/proc/self/task/10586/fd/3/bar1/filea
/proc/self/task/10586/fd/3/bar1/relative-link
/proc/self/task/10586/fd/3/testfile
/proc/self/fd/3/bar1/bar2/fileb
/proc/self/fd/3/bar1/filea
/proc/self/fd/3/bar1/relative-link
/proc/self/fd/3/testfile
/proc/7927/task/7927/cwd/bar1/bar2/fileb
/proc/7927/task/7927/cwd/bar1/filea
/proc/7927/task/7927/cwd/bar1/relative-link
/proc/7927/task/7927/cwd/testfile
/proc/7927/cwd/bar1/bar2/fileb
/proc/7927/cwd/bar1/filea
/proc/7927/cwd/bar1/relative-link
/proc/7927/cwd/testfile
/proc/7981/task/7981/cwd/bar1/bar2/fileb
/proc/7981/task/7981/cwd/bar1/filea
/proc/7981/task/7981/cwd/bar1/relative-link
/proc/7981/task/7981/cwd/testfile
/proc/7981/cwd/bar1/bar2/fileb
/proc/7981/cwd/bar1/filea
/proc/7981/cwd/bar1/relative-link
/proc/7981/cwd/testfile
/proc/7983/task/7983/cwd/bar1/bar2/fileb
/proc/7983/task/7983/cwd/bar1/filea
/proc/7983/task/7983/cwd/bar1/relative-link
/proc/7983/task/7983/cwd/testfile
/proc/7983/cwd/bar1/bar2/fileb
/proc/7983/cwd/bar1/filea
/proc/7983/cwd/bar1/relative-link
/proc/7983/cwd/testfile
/proc/7990/task/7990/fd/38/bar1/bar2/fileb
/proc/7990/task/7990/fd/38/bar1/filea
/proc/7990/task/7990/fd/38/bar1/relative-link
/proc/7990/task/7990/fd/38/testfile
/proc/7990/fd/38/bar1/bar2/fileb
/proc/7990/fd/38/bar1/filea
/proc/7990/fd/38/bar1/relative-link
/proc/7990/fd/38/testfile
/proc/8022/task/8022/cwd/bar1/bar2/fileb
/proc/8022/task/8022/cwd/bar1/filea
/proc/8022/task/8022/cwd/bar1/relative-link
/proc/8022/task/8022/cwd/testfile
/proc/8022/cwd/bar1/bar2/fileb
/proc/8022/cwd/bar1/filea
/proc/8022/cwd/bar1/relative-link
/proc/8022/cwd/testfile
/proc/8024/task/8024/cwd/bar1/bar2/fileb
/proc/8024/task/8024/cwd/bar1/filea
/proc/8024/task/8024/cwd/bar1/relative-link
/proc/8024/task/8024/cwd/testfile
/proc/8024/cwd/bar1/bar2/fileb
/proc/8024/cwd/bar1/filea
/proc/8024/cwd/bar1/relative-link
/proc/8024/cwd/testfile
/proc/8032/task/8032/cwd/bar1/bar2/fileb
/proc/8032/task/8032/cwd/bar1/filea
/proc/8032/task/8032/cwd/bar1/relative-link
/proc/8032/task/8032/cwd/testfile
/proc/8032/cwd/bar1/bar2/fileb
/proc/8032/cwd/bar1/filea
/proc/8032/cwd/bar1/relative-link
/proc/8032/cwd/testfile
/proc/8034/task/8034/cwd/bar1/bar2/fileb
/proc/8034/task/8034/cwd/bar1/filea
/proc/8034/task/8034/cwd/bar1/relative-link
/proc/8034/task/8034/cwd/testfile
/proc/8034/task/8048/cwd/bar1/bar2/fileb
/proc/8034/task/8048/cwd/bar1/filea
/proc/8034/task/8048/cwd/bar1/relative-link
/proc/8034/task/8048/cwd/testfile
/proc/8034/task/8073/cwd/bar1/bar2/fileb
/proc/8034/task/8073/cwd/bar1/filea
/proc/8034/task/8073/cwd/bar1/relative-link
/proc/8034/task/8073/cwd/testfile
/proc/8034/task/8076/cwd/bar1/bar2/fileb
/proc/8034/task/8076/cwd/bar1/filea
/proc/8034/task/8076/cwd/bar1/relative-link
/proc/8034/task/8076/cwd/testfile
/proc/8034/task/8077/cwd/bar1/bar2/fileb
/proc/8034/task/8077/cwd/bar1/filea
/proc/8034/task/8077/cwd/bar1/relative-link
/proc/8034/task/8077/cwd/testfile
/proc/8034/cwd/bar1/bar2/fileb
/proc/8034/cwd/bar1/filea
/proc/8034/cwd/bar1/relative-link
/proc/8034/cwd/testfile
/proc/8042/task/8042/cwd/bar1/bar2/fileb
/proc/8042/task/8042/cwd/bar1/filea
/proc/8042/task/8042/cwd/bar1/relative-link
/proc/8042/task/8042/cwd/testfile
/proc/8042/cwd/bar1/bar2/fileb
/proc/8042/cwd/bar1/filea
/proc/8042/cwd/bar1/relative-link
/proc/8042/cwd/testfile
/proc/8044/task/8044/cwd/bar1/bar2/fileb
/proc/8044/task/8044/cwd/bar1/filea
/proc/8044/task/8044/cwd/bar1/relative-link
/proc/8044/task/8044/cwd/testfile
/proc/8044/cwd/bar1/bar2/fileb
/proc/8044/cwd/bar1/filea
/proc/8044/cwd/bar1/relative-link
/proc/8044/cwd/testfile
/proc/8314/task/8314/cwd/bar1/bar2/fileb
/proc/8314/task/8314/cwd/bar1/filea
/proc/8314/task/8314/cwd/bar1/relative-link
/proc/8314/task/8314/cwd/testfile
/proc/8314/task/8328/cwd/bar1/bar2/fileb
/proc/8314/task/8328/cwd/bar1/filea
/proc/8314/task/8328/cwd/bar1/relative-link
/proc/8314/task/8328/cwd/testfile
/proc/8314/task/8330/cwd/bar1/bar2/fileb
/proc/8314/task/8330/cwd/bar1/filea
/proc/8314/task/8330/cwd/bar1/relative-link
/proc/8314/task/8330/cwd/testfile
/proc/8314/cwd/bar1/bar2/fileb
/proc/8314/cwd/bar1/filea
/proc/8314/cwd/bar1/relative-link
/proc/8314/cwd/testfile
/proc/9400/task/9400/cwd/bar1/bar2/fileb
/proc/9400/task/9400/cwd/bar1/filea
/proc/9400/task/9400/cwd/bar1/relative-link
/proc/9400/task/9400/cwd/testfile
/proc/9400/task/9403/cwd/bar1/bar2/fileb
/proc/9400/task/9403/cwd/bar1/filea
/proc/9400/task/9403/cwd/bar1/relative-link
/proc/9400/task/9403/cwd/testfile
/proc/9400/cwd/bar1/bar2/fileb
/proc/9400/cwd/bar1/filea
/proc/9400/cwd/bar1/relative-link
/proc/9400/cwd/testfile
/proc/9402/task/9402/cwd/bar1/bar2/fileb
/proc/9402/task/9402/cwd/bar1/filea
/proc/9402/task/9402/cwd/bar1/relative-link
/proc/9402/task/9402/cwd/testfile
/proc/9402/cwd/bar1/bar2/fileb
/proc/9402/cwd/bar1/filea
/proc/9402/cwd/bar1/relative-link
/proc/9402/cwd/testfile
/proc/10586/task/10586/fd/3/bar1/bar2/fileb
/proc/10586/task/10586/fd/3/bar1/filea
/proc/10586/task/10586/fd/3/bar1/relative-link
/proc/10586/task/10586/fd/3/testfile
/proc/10586/fd/3/bar1/bar2/fileb
/proc/10586/fd/3/bar1/filea
/proc/10586/fd/3/bar1/relative-link
/proc/10586/fd/3/testfile

```
lol, omg, so many links to my file :)

hard links get own inode number, right ? so this works only on soft links...

hmm, are we the onlyones here interested on this topic :confused:

---

