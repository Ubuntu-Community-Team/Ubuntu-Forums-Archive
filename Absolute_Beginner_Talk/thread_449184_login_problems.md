---
title: "login problems"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by angry tuna on 2007-05-20
ok, I'm going to try to explain my problem, if I'm not precise on the terminology, forgive me.  when I start the computer I get a log in screen. I type in the name and password, screen goes black for a second then pops back to the log in screen.  this happened once before after trying to update when I was told the "disk was full".  I was able to fix that problem by hitting ctrl + alt + F1 then sudo apt-get clean.  I tried another update and this "fix" doesn't work.  

I've tried searching through the forums, but most of the posts assume knowledge about the system that I don't have. I can't find any that give suggestions for the fix and an "oh, by the way, if you're new to linux, you might need to check out..." I have my computer set up to dual boot and I wasn't able to connect to the internet through ubuntu (the wifi didn't work), so I have to go back and forth between vista to look for a solution, then reboot to ubuntu to try it.

at this point, i just want to get my files and either try to reinstall, install 7.04 (I have 6.10 now) or give up and suffer through vista.  can someone just help me get my spreadsheets back?

thanks

---

### Post by taurus on 2007-05-20
Are you sure your disk is not full again?  Log in to a console, <Ctrl><Alt>F2, and post the output of this command here.

```
df -h
```

---

### Post by angry tuna on 2007-05-20
> **taurus said:**
> Are you sure your disk is not full again?  Log in to a console, <Ctrl><Alt>F2, and post the output of this command here.

```
df -h
```


I will give it a try, as soon as I can switch back over to ubuntu.  Is there anyway to increase the disk size?  I know the main partition can't be full, I allocated 50 gigs for ubuntu.  But I remember needing to partition 2 smaller sections when I preped for install.  My guess is the updates and downloads are filling these up.  Is there a way to increase these?

thanks for getting back to me

---

### Post by taurus on 2007-05-20
You can use GParted LiveCD to resize your partitions.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by angry tuna on 2007-05-20
ok, here's what I get:

FILE SYST-      size-     used-     avail-     use%-     mounted on

/dev/sda-       2.9G    -2.8G         -0       -100%          -/
varrun-          501M     -88K    -501M          -1%         -/var/run
varlock-         501M       -0K    -501M          -0%         -/var/lock
procbususb-    10M   -100K      -10M          -1%         -/proc/bus/usb
udev-              10M   -100K      -10M          -1%         -/dev
devshm-        501M       -0K    -501M          -0%        -/dev/shem
/rm-               501M    -18M    -484M          -4%        -/lib/modules/2.6.17-10/generic/volatile
/dev/sda1-      49G     -29G      -20G         -60%       -/media/sda
/dev/sda2-     6.6G   -5.9G    -690M         -90%       -/media/sda



thanks for the help

---

### Post by taurus on 2007-05-20
> **angry tuna said:**
> ok, here's what I get:

FILE SYST-      size-     used-     avail-     use%-     mounted on

/dev/sda-       2.9G    -2.8G         -0       -100%          -/
varrun-          501M     -88K    -501M          -1%         -/var/run
varlock-         501M       -0K    -501M          -0%         -/var/lock
procbususb-    10M   -100K      -10M          -1%         -/proc/bus/usb
udev-              10M   -100K      -10M          -1%         -/dev
devshm-        501M       -0K    -501M          -0%        -/dev/shem
/rm-               501M    -18M    -484M          -4%        -/lib/modules/2.6.17-10/generic/volatile
/dev/sda1-      49G     -29G      -20G         -60%       -/media/sda
/dev/sda2-     6.6G   -5.9G    -690M         -90%       -/media/sda

thanks for the help

You leave only 3.0GB for /.  Gnome would take up almost 2.5GB right there so anything else like log files and what not after that would require more space.

Also, why are you mounting both /dev/sda1 & dev/sda2 to the same mounting point, /media/sda (or is that just a typo)?

What's the output of this command?

```
sudo fdisk -l
```

---

### Post by angry tuna on 2007-05-20
> **taurus said:**
> You leave only 3.0GB for /.  Gnome would take up almost 2.5GB right there so anything else like log files and what not after that would require more space.

Also, why are you mounting both /dev/sda1 & dev/sda2 to the same mounting point, /media/sda (or is that just a typo)?

What's the output of this command?

```
sudo fdisk -l
```

ok,  /dev/sda1 & dev/sda2 are mounted on /media/sda1 and /media/sda2 respectively (my typo in the original post).  I followed the partition instructions before installing 6.10 and thought that my memory allocation would be ok. I'm downloading the GParted program you suggested and will check the output of sudo fdisk -l when I can get back into ubuntu.

thanks!

---

### Post by angry tuna on 2007-05-20
the output of sudo fdisk -l is:

[COLOR="DarkGreen"]Disk /dev/sda: 120.0GB, 120034123776
255 heads, 63 sectors/track, 14593 cylinders
units = cylinders 0f 16065 * 512 = 82252280 bytes

Device Boot - Start - End - Blocks - ID - System
/dev/sda1 - 1 - 6344 - 50950421 - 7 - HPFS/NTFS
/dev/sda2 - 13738 - 14593 - 7 -  HPFS/NTFS
/dev/sda3 - 6345 - 6725 - 3060382+ - Linux
/dev/sda4 - 6726 - 6796 - 570307+ - Linux

Partition Table entries are not in disk order
[/COLOR]

thanks for the help

---

### Post by nerdman978 on 2007-05-20
> **angry tuna said:**
> suffer through vista
NOOOO!
Stay away from vista!

---

### Post by taurus on 2007-05-20
> **angry tuna said:**
> the output of sudo fdisk -l is:

[COLOR="DarkGreen"]Disk /dev/sda: 120.0GB, 120034123776
255 heads, 63 sectors/track, 14593 cylinders
units = cylinders 0f 16065 * 512 = 82252280 bytes

Device Boot - Start - End - Blocks - ID - System
/dev/sda1 - 1 - 6344 - 50950421 - 7 - HPFS/NTFS
/dev/sda2 - 13738 - 14593 - 7 -  HPFS/NTFS
/dev/sda3 - 6345 - 6725 - 3060382+ - Linux
/dev/sda4 - 6726 - 6796 - 570307+ - Linux

Partition Table entries are not in disk order
[/COLOR]

thanks for the help

So, you can use GParted LiveCD to boot from it.  Then, decrease the size of /dev/sda2 and transfer that space to /dev/sda3, increasing / to give you more space.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by angry tuna on 2007-05-20
> **taurus said:**
> So, you can use GParted LiveCD to boot from it.  Then, decrease the size of /dev/sda2 and transfer that space to /dev/sda3, increasing / to give you more space.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

ok, I'll give it a try.  according to the df -h output I have 690M left unused on /dev/sda2. how much can I safely transfer to /dev/sda3? and how much do you think I need in that partition to avoid future problems?

thanks.

---

### Post by taurus on 2007-05-20
Looks like your /dev/sda2 is filled up too.  Therefore, you need to use the free space from /dev/sda1 instead.  depends on how much stuff you plan to install on Ubuntu, 10GB should be good enough for a while (unless you start to download a bunch of stuff).

---

### Post by angry tuna on 2007-05-20
> **nerdman978 said:**
> NOOOO!
Stay away from vista!

[COLOR="Navy"]I want nothing more than to stay away from vista, trust me.  I'm coming to "pc land" after many relatively happy years with macs. I like the open source ethos, but am out of the loop technically, so if I find the support understandable, I'm in the pool!
[/COLOR]

---

### Post by angry tuna on 2007-05-20
> **taurus said:**
> Looks like your /dev/sda2 is filled up too.  Therefore, you need to use the free space from /dev/sda1 instead.  depends on how much stuff you plan to install on Ubuntu, 10GB should be good enough for a while (unless you start to download a bunch of stuff).

I followed your advice and I'm able to log into nautilus, woohoo.  I had some issues with GParted and the sda1 (which needed a chkdsk run before GParted would let me free some space for the sda3), but the "how to" was explained in the LiveCD session.

Thanks Again!

Can't wait until I can get connected to the web through ubuntu to finally do away with vista!

---

