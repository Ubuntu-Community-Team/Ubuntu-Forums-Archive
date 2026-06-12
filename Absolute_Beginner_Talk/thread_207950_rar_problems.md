---
title: "rar problems"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by CAX on 2006-07-02
I had some problems that I couldn't open rar files. So I downloaded rarlinux-3.6.b4.tar.gz I extracted the file and supposedly it should be enough to copy the rar file to /usr/bin/ but I get the message that I haven't got the permission to write to /usr/bin/ . I have added my name to the group of administrator (well I think, see below) What am I doing wrong?

my username is cax if that is not clear

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:cax
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,cax
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,cax
floppy:x:25:haldaemon,cax

cdrom:x:24:haldaemon,cax
floppy:x:25:haldaemon,cax
tape:x:26:
sudo:x:27:
audio:x:29:cax
dip:x:30:cax
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:cax
sasl:x:45:
plugdev:x:46:haldaemon,cax
staff:x:50:

plugdev:x:46:haldaemon,cax
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
crontab:x:104:
ssh:x:105:
lpadmin:x:106:cax
messagebus:x:107:
haldaemon:x:108:
slocate:x:109:
scanner:x:110:cupsys,cax
cax:x:1000:
admin:x:111:cax

---

### Post by Jagot on 2006-07-02
You don't need to do that to add rar support - see here:

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_RAR_Archiver_.28rar.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_RAR_Archiver_.28rar.29)

---

### Post by CAX on 2006-07-02
well maybe it is not neccessary but it should do the trick no? I have tried the other way as well but then I get the following reply:
 
cax@cax-laptop:~$ sudo apt-get install rar
Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate


I updated before. I read somewhere that the way I am trying to do it should have a bit better compatiility  with different rar-filer but getting it done anyway would be nice :)

---

### Post by Jagot on 2006-07-02
rar and unrar are in the multiverse repository which is not enabled by default.  See here to enable it:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I still recommend doing it the way I've said to enable rar support, but in your original post you talk about the tar.gz file - you did compile it correctly right?  Moving the file to /usr/bin isn't enough.  See here about it if you're not sure:

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

Also, with the user permissions to write to /usr/bin just hit alt+f2 and type:

```
gksudo nautilus
```

The file browser will open as root allowing you to move files anywhere.

---

### Post by CAX on 2006-07-02
thanks I added the multiverse repository. I thought it was under un-free repository which I had added.  I used your recommended way now after adding the right repopsitory and everything works now. Thanks a lot!

---

