---
title: "resolv.conf permissions"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by zekopeko on 2006-10-16
hi, 

just need the default permissions of the etc/resolv.conf

thnx

---

### Post by ebutton on 2006-10-16
ebutton@ubuntu:~$ ls -al /etc/resolv.conf
-rw-r--r-- 1 root root 23 2006-10-16 16:52 /etc/resolv.conf
ebutton@ubuntu:~$


Is that it?

Ed

---

### Post by zekopeko on 2006-10-16
hmmmm... thats strange. i sudoed mine to 444 so that i don't lose my DNS after reboot but i didn't restart the machine because i found a more elegant fix. now mine says this(didn't change them from 444 or restarted):

zekopeko@leviathan:~$ ls -al /etc/resolv.conf
lrwxrwxrwx 1 root root 31 2006-09-26 01:42 /etc/resolv.conf -> /etc/resolvconf/run/resolv.conf

well i'll try your's. hope i don't mess something up :-D

---

### Post by stream303 on 2006-11-12
/etc/resolv.conf gets overwritten by dhclient so altering permissions rarely works in the long run.  Maybe this will help:

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

---

