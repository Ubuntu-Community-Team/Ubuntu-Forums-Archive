---
title: "Can't start programs under System/Administrators"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by kjelle392 on 2007-05-07
Hello

I'm having big troubles with Feisty. I can not start applications under System/Administration any more! Guess I did something wrong when editing my groups file...

Anyhow; what happens is that the first time I try to access those programs, I give in the superuser-password, but nothing happens! Next time I try to start a program, all I can see is XXXX is starting up - and after 2-3 secs the message disapears.

How can I fix this? I'm very new at Linux :)

---

### Post by uchuunoyanushi on 2007-05-07
What did you change in the groups file?  It sounds like you edited yourself out of the ability to become a superuser.

---

### Post by kjelle392 on 2007-05-07
I THINK I put my user in the root-group initially.. because I am the only user and want to have all the rights. Guess that wasn't the best thing to do...
The strange part is that sudo works in consol - but it seems that starting admin-programs from menu doesn't

---

### Post by uchuunoyanushi on 2007-05-07
> **kjelle392 said:**
> I THINK I put my user in the root-group initially.. because I am the only user and want to have all the rights. Guess that wasn't the best thing to do...

If you were the first user created, you should have been automatically granted admin privileges, which you need in order to do anything that changes the system (like updates).  If you changed your user settings somehow you may have changed it so you no longer have admin privileges, which means that you aren't allowed to access anything in the system -> administration menu.  Did you ever go into System->Administration->Users and Groups and change anything?

---

### Post by kjelle392 on 2007-05-07
> **uchuunoyanushi said:**
> If you were the first user created, you should have been automatically granted admin privileges, which you need in order to do anything that changes the system (like updates).  If you changed your user settings somehow you may have changed it so you no longer have admin privileges, which means that you aren't allowed to access anything in the system -> administration menu.  Did you ever go into System->Administration->Users and Groups and change anything?

yes.... I did... Because I was tired to always type password when working with sudo, I though that adding myself to the root-group would be a nice thing to do. The problems started then. I have edited /etc/group and deleted myself from the root-group, but it seems that is not enough.

Is re-installation the only hope...?

---

### Post by uchuunoyanushi on 2007-05-07
> **kjelle392 said:**
> yes.... I did... Because I was tired to always type password when working with sudo, I though that adding myself to the root-group would be a nice thing to do. The problems started then. I have edited /etc/group and deleted myself from the root-group, but it seems that is not enough.

Is re-installation the only hope...?

Don't give up yet. ^^

The root group (fyi) is the group for the user 'root', like you have a group named whatever your user name is.  Can you put the contents of your /etc/group file here?

---

### Post by kjelle392 on 2007-05-07
> **uchuunoyanushi said:**
> Don't give up yet. ^^

The root group (fyi) is the group for the user 'root', like you have a group named whatever your user name is.  Can you put the contents of your /etc/group file here?

Here it is:

[HTML]root:x:0:root
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:kjelle392
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,kjelle392
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,kjelle392
floppy:x:25:haldaemon,kjelle392
tape:x:26:
sudo:x:27:
audio:x:29:kjelle392
dip:x:30:kjelle392
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:kjelle392
sasl:x:45:
plugdev:x:46:haldaemon,kjelle392
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
ssl-cert:x:104:cupsys
crontab:x:105:
ssh:x:106:
messagebus:x:107:
avahi:x:108:
lpadmin:x:109:kjelle392
haldaemon:x:110:
scanner:x:111:cupsys,hplip,kjelle392
slocate:x:112:
gdm:x:113:
kjelle392:x:1000:kjelle392
admin:x:114:kjelle392
postfix:x:115:
postdrop:x:116:
fuse:x:117:kjelle392
mysql:x:118:
nvram:x:119:
powerdev:x:120:haldaemon
avahi-autoipd:x:121:
netdev:x:122:
clamav:x:123:[/HTML]

---

### Post by uchuunoyanushi on 2007-05-07
Hmm, you still have admin privileges, so that's good.  Is it only when you're trying to open something from the menus that requires a password that you can't open?

---

### Post by kjelle392 on 2007-05-07
> **uchuunoyanushi said:**
> Hmm, you still have admin privileges, so that's good.  Is it only when you're trying to open something from the menus that requires a password that you can't open?

Yes that's right. Now I can't even open a terminal! Seems like it grows worse and worse.

EDIT: Now Gnome chashed too and I can't get in anymore... :-(     Had to boot Windows to write this.

---

### Post by uchuunoyanushi on 2007-05-07
> **kjelle392 said:**
> Yes that's right. Now I can't even open a terminal! Seems like it grows worse and worse.

Hmm, seems like there's a problem with the gnome panel, but I honestly have no idea what it could be.  I'd start by restarting the computer and see if you can access programs from the menu when it comes back up.

Sorry, wish I had a better idea. >.<

---

### Post by kjelle392 on 2007-05-07
> **uchuunoyanushi said:**
> Hmm, seems like there's a problem with the gnome panel, but I honestly have no idea what it could be.  I'd start by restarting the computer and see if you can access programs from the menu when it comes back up.

Sorry, wish I had a better idea. >.<

Me too... Do you think repairing the installation will success? I have a dual-boot system with Ubuntu and Windows XP, and I don't want to mess up the Windows-installation aswell.

---

### Post by kjelle392 on 2007-05-08
Can't anyone help me? :(

---

