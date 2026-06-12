---
title: "[SOLVED] How do i change user groups from the treminal?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by lunamystry on 2007-08-27
I need a way to change my user groups from the the terminal or safe mode. I naively changed the user group to root and now I can't use anything that needs sudo. That means i cant install anything on my PC.

PLEASE HELP ME!!!:(

---

### Post by Ubuntized! on 2007-08-27
I am not criticising, but i didn't get what you meant! :) How did u do that group change?

---

### Post by Hospadar on 2007-08-27
I believe you'll need to edit the /etc/group file, something like ```
sudo nano /etc/group
``` in the terminal  google about to see in detail how to edit this file properly (it's relatively self-evident, but you may want some extra help)

---

### Post by lunamystry on 2007-08-27
I was trying to install something then and i was following instructions from a read me file. The instaructions said i should extract one of the files into /usr/bin. When itried to do that i was told I dont have the permission to. I thought if I was in the controling groups maybe it would work. So I changed my group from the user settings in system settings. I was not sure which group and I just took root. i tried to extract again but still could not. I then tried to change my group back to lunamystry but it got a message that su returned an error. Now I cant use any sudo things. Thus sudo nano / etc/groups does not work. Check the screen shot for what happens...

---

### Post by bodhi.zazen on 2007-08-27
Since you lost root access you will need to boot to recovery mode

Either :

1. ```
adduser <username> admin
```

<username> = your log in user name ...

2. edit /etc/groups (nano /etc/groups) and add your user to the admin group

Reboot ...

You can then access sudo again

=========

To sys admin use sudo <command> or to become root sudo -i

---

### Post by lunamystry on 2007-08-28
> **bodhi.zazen said:**
> 

2. edit /etc/groups (nano /etc/groups) and add your user to the admin group


I don't think I can add my group to the admin group via terminal, will it be just addding a name to a line or will I have to add more stuff?

I have never done anything in safemode except enter help then reboot. 
The only two commands I know for the safe mode.

---

### Post by Ubuntized! on 2007-08-28
IMHO it may be easy! the file /etc/group looks like this

```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:andrea
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,andrea
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,andrea
floppy:x:25:haldaemon,andrea
tape:x:26:
sudo:x:27:
audio:x:29:andrea
dip:x:30:andrea
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:andrea
sasl:x:45:
plugdev:x:46:haldaemon,andrea
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:cupsys,hplip,andrea
nvram:x:105:
messagebus:x:106:
ssl-cert:x:107:cupsys
crontab:x:108:
ssh:x:109:
avahi-autoipd:x:110:
avahi:x:111:
netdev:x:112:andrea
lpadmin:x:113:andrea
haldaemon:x:114:
powerdev:x:115:haldaemon,andrea
slocate:x:116:
admin:x:117:andrea
gdm:x:118:
fuse:x:119:
andrea:x:1000:

```

I think it should be easy!
I'd trust in bodhi.zazen to the death! :lolflag:

---

### Post by lunamystry on 2007-08-28
I did it and it appears to have worked. I Logged in in the safe mode then I entered ```
 adduser lunamystry admin
``` then I think it added my lunamystry account to the admin group. I then did ```
nano /etc/groups 
``` I was not sure for what, i could not do much so I decided to exit with F2 and saved nothing. I rebooted and changed my primary group to lunamystry 

Thank you for your help.

---

### Post by lunamystry on 2007-08-28
> **Ubuntized! said:**
> IMHO it may be easy! the file /etc/group looks like this

```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:andrea
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,andrea
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,andrea
floppy:x:25:haldaemon,andrea
tape:x:26:
sudo:x:27:
audio:x:29:andrea
dip:x:30:andrea
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:andrea
sasl:x:45:
plugdev:x:46:haldaemon,andrea
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:cupsys,hplip,andrea
nvram:x:105:
messagebus:x:106:
ssl-cert:x:107:cupsys
crontab:x:108:
ssh:x:109:
avahi-autoipd:x:110:
avahi:x:111:
netdev:x:112:andrea
lpadmin:x:113:andrea
haldaemon:x:114:
powerdev:x:115:haldaemon,andrea
slocate:x:116:
admin:x:117:andrea
gdm:x:118:
fuse:x:119:
andrea:x:1000:

```

I think it should be easy!
I'd trust in bodhi.zazen to the death! :lolflag:

My groups file when i was in safe mode did not look like that! was I suppose to enter something to view that maybe? I am ussuming that to go into the groups file I use nano /etc/groups.

---

### Post by lunamystry on 2007-08-28
This is what i get when I use nano /etc/groups (screenshot)

i am worried should there be more things in my groups file or is the reason it is empty because i only have one account on my PC?

---

### Post by schorsch on 2007-08-28
The file is called /etc/group without the last "s". When you try "nano /etc/groups" you create a new empty file in memory but I doubt that you can write it to disk when not having root privileges. So you have to use
```
sudo nano /etc/group
``` when changing group permissions.

---

### Post by Ubuntized! on 2007-08-28
Exxxxactly!!! Schorsch said right!!!
You misspelled! It's /etc/group, not /etc/groups!!!!

Very happy to be useful!!

---

### Post by lunamystry on 2007-08-29
it worked. 

Thank you very much

---

### Post by schorsch on 2007-08-29
Glad to hear that. Could you please mark this thread as solved as it may help others, too?

---

