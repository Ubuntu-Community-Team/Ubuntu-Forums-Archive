---
title: "Something wrong with my username and passwords for access"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2008-03-12
This is my /etc/passwd
> root: x:0:0:root:/root:/bin/bash
daemon: x:1:1:daemon:/usr/sbin:/bin/sh
bin: x:2:2:bin:/bin:/bin/sh
sys: x:3:3:sys:/dev:/bin/sh
sync: x:4:65534:sync:/bin:/bin/sync
games: x:5:60:games:/usr/games:/bin/sh
man: x:6:12:man:/var/cache/man:/bin/sh
lp: x:7:7:lp:/var/spool/lpd:/bin/sh
mail: x:8:8:mail:/var/mail:/bin/sh
news: x:9:9:news:/var/spool/news:/bin/sh
uucp: x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy: x:13:13:proxy:/bin:/bin/sh
www-data: x:33:33:www-data:/var/www:/bin/sh
backup: x:34:34:backup:/var/backups:/bin/sh
list: x:38:38:Mailing List Manager:/var/list:/bin/sh
irc: x:39:39:ircd:/var/run/ircd:/bin/sh
gnats: x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody: x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp: x:100:101::/nonexistent:/bin/false
syslog: x:101:102::/home/syslog:/bin/false
klog: x:102:103::/home/klog:/bin/false
messagebus: x:103:109::/var/run/dbus:/bin/false
hplip: x:104:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd: x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi: x:106:114:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon: x:107:116:Hardware abstraction layer,,,:/home/haldaemon:/bin/false
gdm: x:108:118:Gnome Display Manager:/var/lib/gdm:/bin/false
disappearedng: x:1000:65534:disappearedng,,,:/media:/bin/bash
sshd: x:109:65534::/var/run/sshd:/usr/sbin/nologin
ftp: x:111:65534::/home/ftp:/bin/false
statd: x:112:65534::/var/lib/nfs:/bin/false


This is my /etc/group
```
root: x:0:
daemon: x:1:
bin: x:2:
sys: x:3:
adm: x:4:disappearedng
tty: x:5:
disk: x:6:
lp: x:7:
mail: x:8:
news: x:9:
uucp: x:10:
man: x:12:
proxy: x:13:
kmem: x:15:
dialout: x:20:disappearedng
fax: x:21:
voice: x:22:
cdrom: x:24:haldaemon,disappearedng
floppy: x:25:haldaemon,disappearedng
tape: x:26:
sudo: x:27:
audio: x:29:disappearedng
dip: x:30:disappearedng
www-data: x:33:
backup: x:34:
operator: x:37:
list: x:38:
irc: x:39:
src: x:40:
gnats: x:41:
shadow: x:42:
utmp: x:43:
video: x:44:disappearedng
sasl: x:45:
plugdev: x:46:haldaemon,disappearedng
staff: x:50:
games: x:60:
users: x:100:
nogroup: x:65534:
dhcp: x:101:
syslog: x:102:
klog: x:103:
scanner: x:104:hplip,disappearedng
nvram: x:105:
fuse: x:106:
ssl-cert: x:107:
lpadmin: x:108:disappearedng
messagebus: x:109:
admin: x:110:disappearedng
crontab: x:111:
ssh: x:112:
avahi-autoipd: x:113:
avahi: x:114:
netdev: x:115:disappearedng
haldaemon: x:116:
powerdev: x:117:haldaemon,disappearedng
gdm: x:118:
slocate: x:119:
disappearedng: x:1000:
nobody: x:1001:
user-mp3: x:1002:
searchengine: x:1004:
alex: x:1003:
manel: x:1005:

```

I realize that there are a lot of redundancy  and repetitions for groups when I use the GUI but not here so I guess i shouldn't be worried by the GUI?

What is /bin/false? I added there when I was following a guide with proftpd. How do i remove it?

How do I delete the groups fast and how do I add a new account for FTP so that my friends can access my ftp server with usernames and passwords?
Do I just create a new group called ftp and then add users under that group and just use that for my proftpd configuration? Does proftpd reads information from this file? (because I can't get my server to work apparently due to a "login error" so I guess that's has to be something related to usernames and passwords here.

THx

---

### Post by Iowan on 2008-03-12
The **/bin/false** takes the place of the user's shell - meaning the user cannot execute shell commands. I presume you could edit the passwd file with: ```
sudo nano /etc/passwd 
```
There is a **delgroup**  (and **groupdel**) command to quickly eliminate groups. **man delgroup** (or **man groupdel**) for more information. 
Creating groups would be **groupadd** or **addgroup** (don't remember which is preferred).
**man usermod** gives details for adding users to groups.

---

