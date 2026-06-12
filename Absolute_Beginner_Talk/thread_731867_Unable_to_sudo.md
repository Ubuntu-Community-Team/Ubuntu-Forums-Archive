---
title: "Unable to sudo"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by gvhg on 2008-03-22
I've just installed kde over ubuntu cli and the system refuses to accept my password when i attempt to sudo using GUI (for eg, KPackage does not accept my pwd when it asks for it). I am however still able to sudo in terminal.

I've checked the sudoers and group file and they appear to be normal 

```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:user
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
ucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:user
fax:x:21:
voice:x:22:
cdrom:x:24:user,haldaemon
floppy:x:25:user,haldaemon
tape:x:26:
sudo:x:27:
audio:x:29:user
dip:x:30:user
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:user
sasl:x:45:
plugdev:x:46:user,haldaemon
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:user
nvram:x:105:
fuse:x:106:
crontab:x:107:
ssh:x:108:
user:x:1000:
lpadmin:x:109:user
admin:x:110:user
messagebus:x:111:
haldaemon:x:112:
powerdev:x:113:haldaemon
saned:x:114:

```

Any help there? Thanks!

---

### Post by (((X))) on 2008-03-22
Hi,
Use kdesu instead
[http://ubuntuforums.org/showthread.php?t=730315](http://ubuntuforums.org/showthread.php?t=730315)

---

### Post by jken146 on 2008-03-22
> **gvhg said:**
> I've just installed kde over ubuntu cli and the system refuses to accept my password when i attempt to sudo using GUI (for eg, KPackage does not accept my pwd when it asks for it). I am however still able to sudo in terminal.

Are you using **kdesu** ?

---

### Post by gvhg on 2008-03-22
Sry how to use kdesu?

---

### Post by Bachstelze on 2008-03-22
In a terminal or the Run dialog:

```
kdesu kpackage
```

---

### Post by gvhg on 2008-03-22
kbuildsycoca running...
sudo: kpackage: command not found

Er I got this...

---

### Post by gvhg on 2008-03-22
The thing is that whenever I try to open a program using GUI, it will always reject my pwd whenever it asks for it

---

### Post by cmnorton on 2008-03-22
> **(((X))) said:**
> Hi,
Use kdesu instead
[http://ubuntuforums.org/showthread.php?t=730315](http://ubuntuforums.org/showthread.php?t=730315)

Is this post about needing to run the kde equivalent of gksudo or needing to run sudo out of an xterm?

I understand why kde would have an gksudo equivalent but not why sudo would not work.

tnx
cmn

---

### Post by gvhg on 2008-03-22
Yea the problem is the latter, I cant run sudo out of xorg

---

### Post by cmnorton on 2008-03-22
Now, I am completely confused. Why won't sudo work with KDE?

---

### Post by gvhg on 2008-03-22
Ok. When I execute the GUI of kpackage, it says that the action requires root privileges and it asks you for the root password. When I type my password in however, nothing happens and the window asking for the root password keeps popping up.

---

### Post by (((X))) on 2008-03-22
Because I been told running kde with root priveleges will destroy everything.
Just look at the default background for root user in Mepis distribution.

---

### Post by gvhg on 2008-03-22
So what do I have to do?

---

