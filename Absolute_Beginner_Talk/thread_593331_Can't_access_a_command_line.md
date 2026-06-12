---
title: "Can't access a command line"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by bethebunny on 2007-10-27
Ok, so I completely n00bed out my first Ubuntu install. I get it all set up and partitioned nicely (though I haven't gotten GRUB on the machine yet, so I still boot to Ubuntu using the live-boot disk). I set up a single user. Unfortunately, booting to Ubuntu now boots to the login screen, CTRL-ALT-F1 gets me to a text output screen but no REPL, and as far as I can tell I misspelled the username when I was typing it in. Any ideas short of making a boot disk of another implementation?

---

### Post by taurus on 2007-10-27
Can you boot into recovery mode with the CD?  Otherwise, boot from the LiveCD and mount it partition where / is.  Then, look in /home to see exactly what is your login name.

---

### Post by bethebunny on 2007-10-27
No, there's no recovery on the boot disk. And I'm not quite sure exactly what you're saying I do with mounting the LiveCD, but I also have no idea how I'd go about that without access to a command line.

---

### Post by taurus on 2007-10-27
Can you boot from a LiveCD?  If yes, then open a terminal and post the output of this command here.

```
sudo fdisk -l
```
That is a lower case letter l, not number 1.

---

### Post by bethebunny on 2007-10-27
No, I can't. When I try to open the LiveCD it boots Ubuntu to the GUI login screen, where I can do nothing. CTRL-ALT-F1 at this point doesn't yield a command line.

---

### Post by taurus on 2007-10-27
Is Ubuntu the only OS on that machine?  Do you have Windows running on it as well?

---

### Post by bethebunny on 2007-10-27
Yes, it has a Windows XP Home Edition in another partition. I don't have GRUB set up yet, which I probably should have done before installing Ubuntu, but I can still boot to my Ubuntu partition using the LiveCD.

---

### Post by taurus on 2007-10-27
Boot your Windows.  Then, install this little program so you can view ext3 filesystem.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Now, navigate to where /home is and look to see what is your username.

---

### Post by bethebunny on 2007-10-27
Hrm... that's an amazing application. Oddly enough, I don't appear to have any files in my /home file yet. Is it possible the Ubuntu installation didn't actually add the main user?

---

### Post by taurus on 2007-10-27
Impossible!  If you don't mind, post the /etc/passwd here and we will see if there is an actual user on your Ubuntu system.

---

### Post by bethebunny on 2007-10-27
```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:100:101::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
messagebus:x:103:106::/var/run/dbus:/bin/false
avahi-autoipd:x:104:110:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:105:111:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
cupsys:x:106:113::/home/cupsys:/bin/false
haldaemon:x:107:114:Hardware abstraction layer,,,:/home/haldaemon:/bin/false
hplip:x:108:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:109:118:Gnome Display Manager:/var/lib/gdm:/bin/false
```

---

### Post by taurus on 2007-10-27
Looks like there is no user on your machine and since you can't boot into recovery mode so you could create one, I guess you just have to reinstall!

---

### Post by bethebunny on 2007-10-27
Yeacch. Thanks for all the help :) Is it fine to uninstall it by simply using windows through that Ext3 browsing application to delete all information on the partition?

---

### Post by taurus on 2007-10-27
Yeah.  Or you can reformat it to ntfs or fat32 if you wish if you don't plan to reinstall Ubuntu on it.

---

### Post by bethebunny on 2007-10-27
Thanks a lot :) I don't think I'm going to give up on Ubuntu just yet ;)

---

