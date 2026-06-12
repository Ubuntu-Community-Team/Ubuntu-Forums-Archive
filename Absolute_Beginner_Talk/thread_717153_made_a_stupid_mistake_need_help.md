---
title: "made a stupid mistake need help"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by ginronin on 2008-03-06
I just install unbuntu 7.10 and i was playing around with my user groups. i changed my user's group to root and now i can't access the user group tool in my system/administration menu  to change it back is there anyway i can do it from the terminal? 

much thanks in advance

---

### Post by smurphy_it on 2008-03-06
Did you try rebooting your machine and go into your grub boot menu on boot (hit escape when displayed on the screen) and choose recovery mode, then try your users' and groups.

---

### Post by cmnorton on 2008-03-06
First, you will have to know something about how /etc/group is set up.

Second, Boot your system in recovery mode. Press ESC at the grub prompt, so you can select recovery mode.

Edit /etc/group and look for your username and hopefully you are the user who installed.

Say your username is ted:

Your entry in /etc/group should look like this:

ted:x:1001:

Before you change anything, I recommend posting here what your group entry looks like before you change it. However, if you go ahead without posting here, please make a copy of /etc/group before you change it 
(cp /etc/group /etc/group.not_working).

---

### Post by ginronin on 2008-03-06
here is what is in the file
```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon
floppy:x:25:haldaemon
tape:x:26:
sudo:x:27:
audio:x:29:
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:thejps
sasl:x:45:
plugdev:x:46:haldaemon
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:hplip
nvram:x:105:
fuse:x:106:
ssl-cert:x:107:
lpadmin:x:108:thejps
messagebus:x:109:
admin:x:110:
crontab:x:111:
ssh:x:112:
avahi-autoipd:x:113:
avahi:x:114:
netdev:x:115:thejps
haldaemon:x:116:
powerdev:x:117:haldaemon,thejps
gdm:x:118:
slocate:x:119:
thejps:x:1000:
```
my username is thejps

---

### Post by taurus on 2008-03-06
You need to add your login name, thejps, to groups adm & admin.

You can edit /etc/group in recovery mode with 

```
nano -B /etc/group
```
Save you have made the changes, save it with <Ctrl>o and exit with <Ctrl>x.

Then, reboot and see if you can use sudo/gksudo again.

```
shutdown -r now
```

---

### Post by ginronin on 2008-03-06
thank you very much you guys are great

---

