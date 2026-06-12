---
title: "/tmp"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by slrafal on 2007-01-23
How come my /tmp folder is at 33MB at reboot?

When I was on 5.10 it was a megabyte at best.

Can someone please help

---

### Post by tonyr1988 on 2007-01-23
Open a Terminal.

> cd /tmp
ls -la

Post the output here.

---

### Post by slrafal on 2007-01-23
sorry, how do I post the terminal output?

---

### Post by aysiu on 2007-01-23
> **slrafal said:**
> sorry, how do I post the terminal output?
Highlight, right-click, copy, click, right-click, paste.

---

### Post by slrafal on 2007-01-23
slrafal@rafLinux:~$ cd /tmp
slrafal@rafLinux:/tmp$ ls -la
total 7265
drwxrwxrwt 15 root    root        568 2007-01-22 23:11 .
drwxr-xr-x 23 root    root        632 2007-01-14 16:06 ..
drwxrwxrwt  2 slrafal slrafal      72 2007-01-22 23:03 .esd-1000
drwx------  2 slrafal slrafal      48 2007-01-22 23:03 .exchange-slrafal
-rw-------  1 slrafal slrafal 7426048 2007-01-22 23:10 FlashjtLPtt
drwx------  2 root    root         48 2007-01-22 23:11 gconfd-root
drwx------  3 slrafal slrafal      72 2007-01-22 23:03 gconfd-slrafal
srw-rw-rw-  1 root    root          0 2007-01-22 23:03 .gdm_socket
drwxrwxrwt  2 root    root         72 2007-01-22 23:03 .ICE-unix
drwx------  2 slrafal slrafal      72 2007-01-22 23:03 keyring-pcYrke
srwxr-xr-x  1 slrafal slrafal       0 2007-01-22 23:03 mapping-slrafal
drwx------  2 root    root         48 2007-01-22 23:11 orbit-root
drwx------  2 slrafal slrafal    1104 2007-01-22 23:11 orbit-slrafal
drwx------  2 slrafal slrafal      80 2007-01-22 23:03 ssh-qAaOyT4457
drwx------  2 slrafal slrafal      48 2007-01-22 23:03 virtual-slrafal.Xm3qVX
-r--r--r--  1 root    root         11 2007-01-22 23:03 .X0-lock
drwxrwxrwt  2 root    root         72 2007-01-22 23:03 .X11-unix


Thank You for the fast response! :)

---

### Post by tonyr1988 on 2007-01-23
If I'm reading it right, this looks like the biggest culprit:

> -rw------- 1 slrafal slrafal 7426048 2007-01-22 23:10 FlashjtLPtt

Would you have any idea what FlashjtLPtt is? A quick Google isn't showing anything...have you installed anything since you've noticed this change?

Also, copy / paste the output of:

> ls -la ~/.config/autostart

EDIT: It looks like the total size of the /tmp folder is 7265 kb = 7MB. It's still quite a bit, but it's under 33MB. Did you happen to do anything different?

EDIT2: I believe it's safe to remove anything and everything from your /tmp folder. I think it's just an extension of /home to anyone can read/write to for temporary space and it'll all be deleted eventually. But don't go and do that until someone like aysiu confirms this.

---

### Post by slrafal on 2007-01-23
Could it be the Flash player? I do remember installing a Flash player through the Ubuntu guide.

2. I get no such directory error

---

### Post by slrafal on 2007-01-23
slrafal@rafLinux:/tmp$ ls -la ~/.config/autostart
ls: /home/slrafal/.config/autostart: No such file or directory


slrafal@rafLinux:/tmp$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda10            2.8G  338M  2.5G  12% /
varrun                237M   96K  236M   1% /var/run
varlock               237M     0  237M   0% /var/lock
procbususb             10M  136K  9.9M   2% /proc/bus/usb
udev                   10M  136K  9.9M   2% /dev
devshm                237M     0  237M   0% /dev/shm
lrm                   237M   18M  219M   8% /lib/modules/2.6.17-10-generic/volatile
/dev/hda2              23M  9.5M   12M  46% /boot
/dev/hda9             5.9G  2.3G  3.6G  39% /home
/dev/hda1              25G   18G  6.5G  74% /media/hda1
[COLOR="Red"]/dev/hda5              40M   40M  4.0K 100% /tmp[/COLOR]
/dev/hda7             3.5G  1.8G  1.7G  52% /usr
/dev/hda6             495M  481M   14M  98% /var

---

