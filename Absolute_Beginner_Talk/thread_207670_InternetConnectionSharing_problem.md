---
title: "InternetConnectionSharing problem"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by kalata on 2006-07-02
I'm trying to set up Internet Connection Sharing using the guide here :

[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

when I do echo 1 > /proc/sys/net/ipv4/ip_forward
I get this error :
bash: /proc/sys/net/ipv4/ip_forward: Permission denied
 
when I "sudo" it I get the same 
```
~$ sudo echo 1 > /proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permission denied

```

```
$ ls -la  /proc/sys/net/ipv4/ip_forward
-rw-r--r-- 1 root root 0 2006-07-02 15:31 /proc/sys/net/ipv4/ip_forward
```

what am I doing wrong?

---

### Post by richbarna on 2006-07-02
Take a look here, it took a while but I managed to dig it out of google ;)
[http://marc.abramowitz.info/archives/2006/05/17/su-su-sudo-oh-no/]("http://marc.abramowitz.info/archives/2006/05/17/su-su-sudo-oh-no/")

---

### Post by steve.horsley on 2006-07-02
Bash is interpreting this as trying to take the output of "sudo echo 1" and write that to the file. It is trying to open the output file with your permissions, before running sudo.

A real shell expert will know how to do it beter, but I don't. I do it this way:
> steve@dingly:~$ sudo su
root@dingly:/home/steve# echo 1 > /proc/sys/net/ipv4/ip_forward
root@dingly:/home/steve# exit
exit
steve@dingly:~$

P.S.
look at file **/etc/sysctl.conf** - this is the one to edit to enable forwarding every time you boot up.

---

### Post by kalata on 2006-07-02
thanks... I did it by running the "root terminal" in the aps/system tools ...
it is working ok now. 

> P.S.
look at file /etc/sysctl.conf - this is the one to edit to enable forwarding every time you boot up.
that was heplfull too

---

