---
title: "Init file not found"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by phil66 on 2007-05-18
Ubuntu 6.06 lts

When booting I got the error message "INIT: No init file found then I get "Enter run level:"

I can not enter a number in the run level.

I get the same error in recovery mode and still cannot enter a number

Have live cd with install function. Ubuntu install on 80 gb sata hardrive using ext 3 for file system

What is my next step?

Thanks
Ray

---

### Post by vtel57 on 2007-05-19
Was this a recent install? Did it ever work?

---

### Post by phil66 on 2007-05-19
This original post should of said "init:no initbat file found

This is a dual boot system with WindowsXP home. Ubuntu is on a 2nd harddrive by itself.

This distro was install a few months ago. All updated included Firefox 2.0.0.3 and Thunderbird 2.0
KMoney and some other small programs from synpathic.

Distro working fine opened nautilus to remove Panda and same closed and error came up.

Distro now tries to boot but after showing root file system ok it goes to error and the keyboard and mouse are locked up. Unable to enter run level as requested. The same happens in recovery mode.

From grub menu I can open a command line but it shows GRUB> and I cannot find a command to go any further.

Thanks for the help and any suggestions you may have.

Ray

---

### Post by vtel57 on 2007-05-19
If you still have your Ubuntu Live CD, you can attempt to boot to the CD and mount the / root partition of your installation from there to make any corrections. 

I believe the file that is giving you the error is called inittab, not init bat. You can edit your inittab file from the Live CD terminal as Root. 

If you don't know how to do this, let me know... I'll try to walk you through it.

You'll need to know what partition your / root file system is installed on. If you boot to the Live CD and open a terminal, you can enter this command:

```
$ sudo fdisk -l
```

This will give you a listing of your hard drive partitions. Please post that output by COPY/PASTING it here. It will look something like this:

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       30400   213471720    f  W95 Ext'd (LBA)
/dev/sda5            3825        7648    30716248+   7  HPFS/NTFS
/dev/sda6            7649       17209    76798701    7  HPFS/NTFS
/dev/sda7           17210       30400   105956676    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sdb2            3825       30400   213471720    f  W95 Ext'd (LBA)
/dev/sdb5            3825        7648    30716248+   7  HPFS/NTFS
/dev/sdb6            7649       17209    76798701    7  HPFS/NTFS
/dev/sdb7           17210       30400   105956676    7  HPFS/NTFS

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1275    10241406   83  Linux
/dev/hda2            1276        3188    15366172+  83  Linux
/dev/hda3            3190       30401   218580390    5  Extended
/dev/hda5            3190        4464    10241406   83  Linux
/dev/hda6            4465        6376    15358108+  83  Linux
/dev/hda7   *        6378        7652    10241406   83  Linux
/dev/hda8            7653        9564    15358108+  83  Linux
/dev/hda9            9566       10840    10241406   83  Linux
/dev/hda10          10841       12752    15358108+  83  Linux
/dev/hda11          12754       14028    10241406   83  Linux
/dev/hda12          14029       15940    15358108+  83  Linux
/dev/hda13          15942       17216    10241406   83  Linux
/dev/hda14          17217       19128    15358108+  83  Linux
/dev/hda15          19130       20404    10241406   83  Linux
/dev/hda16          20405       22319    15382206   83  Linux
/dev/hda17          22321       22575     2048256   82  Linux swap / Solaris
/dev/hda18          22577       30401    62854281    b  W95 FAT32


Probably not as large as this, though. This is the output of that command on my own system.

Once we know what partition you have your Ubuntu installed on, we can access it with the Live CD session and begin to troubleshoot your inittab problems.

---

### Post by phil66 on 2007-05-19
First the file is "INITTAB"

The windows partition are:

/dev/sda1 Dell Utility
/dev/sda2 Hpfs/ntfs

The Ubuntu partions are:

Device         Start  End    Blocks            ID    System
/dev/sdb1       1     9352  751199084   83     Linux

/dev/sdb2    9353   9729  3028252       5      Extended

/dev/sdb5    9353    9729  3028221      82     Linux swap

Ubuntu,Kernel 2.6.15-28-386
/boot/vmlinz-2.6.15-28-386
root=/dev/sdb1 ro quite  splash

If more info is needed let me know.
I appreciate your help with instructions as this is a new problem 

Ray

---

### Post by vtel57 on 2007-05-19
OK, while you're still in your LIVE CD session, you need to open the Terminal and mount the Ubuntu / (root) partition using this command:

```
$ sudo mount /dev/sdb1 /mnt
```

This will temporarily mount (and give you access to) the / (root) partition within the /mnt directory. Let's now navigate our way to that directory.

```
$ cd /mnt/etc
```

This command, cd, changes the working directory to /mnt/etc, so now you're working from within  the /etc directory on your Ubuntu / (root) partition. Let's look at inittab.

```
$ sudo gedit inittab
```

This will open the inittab file in the Gedit editor (with Root privileges, so be CAREFUL). It will look something like this:

```
# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
[COLOR="Red"]id:2:initdefault:[/COLOR]

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
# Normally not reached, but fallthrough in case of emergency.
z6:6:respawn:/sbin/sulogin

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

# Action on special keypress (ALT-UpArrow).
#kb::kbrequest:/bin/echo "Keyboard Request--edit /etc/inittab to let this work."

# What to do when the power fails/returns.
pf::powerwait:/etc/init.d/powerfail start
pn::powerfailnow:/etc/init.d/powerfail now
po::powerokwait:/etc/init.d/powerfail stop

# /sbin/getty invocations for the runlevels.
#
# The "id" field MUST be the same as the last
# characters of the device (after "tty").
#
# Format:
#  <id>:<runlevels>:<action>:<process>
#
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

# Example how to put a getty on a serial line (for a terminal)
#
#T0:23:respawn:/sbin/getty -L ttyS0 9600 vt100
#T1:23:respawn:/sbin/getty -L ttyS1 9600 vt100

# Example how to put a getty on a modem line.
#
#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3


```

Please COPY/PASTE your inittab here. Also, note the area I've highlighted in [color=red]red[/color] above. You should have a very similar entry in your inittab.

Standing by...

---

### Post by phil66 on 2007-05-19
I was able to mount root 

Cd /mnt  changed as entered

Then tried mounting /etc

But cannot mount /etc no such file or directory

Seems like I have lost /etc

Can it be moved  from live cd?

---

### Post by phil66 on 2007-05-19
That should be changed directory to /mnt and then tried changing to /etc no such file or directory

---

### Post by vtel57 on 2007-05-19
OK, Ray...

Open the Terminal once again and mount the / (root) partition. Once you've done that, do this:

```
$ ls -a /mnt
```

Post the output of that command here, please.

[COLOR="Red"]EDIT:[/COLOR] I see what you did wrong in your command above.

After you mount the / (root) partition, you want to change to the /etc directory with just one step, like this:

```
$ cd /mnt/etc
```

Or, you can do it in two steps, like this:

```
$ cd /mnt
```

then...

```
$ cd etc
```
*Note: no / before the etc.

You just committed a minor syntax error. No big deal. Try again to change directory to the /etc directory and then post your inittab here.

Standing by...

---

### Post by phil66 on 2007-05-20
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
mount: /dev/sdb1 already mounted or /mnt busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt

ubuntu@ubuntu:~$ ls -a /mnt
.    boot   home        initrd.img.old  media  proc  srv  usr      vmlinuz.old
..   cdrom  initrd      lib             mnt    root  sys  var
bin  dev    initrd.img  lost+found      opt    sbin  tmp  vmlinuz
ubuntu@ubuntu:~$

ubuntu@ubuntu:~$ cd /mnt
ubuntu@ubuntu:/mnt$ cd etc
bash: cd: etc: No such file or directory
ubuntu@ubuntu:/mnt$

What do I do about the etc folder which is not in /mnt

---

### Post by vtel57 on 2007-05-20
Well, you've got a **[COLOR="Red"]problem[/COLOR]**, Ray. :( Somehow, whatever you did originally to create this mess also deleted your /etc directory, which contains a vast amount of necessary configuration and preferential data for your operating system.

We are now approaching the outer limits of my knowledge, hence further assistance from me would just be speculative. I think that it may be possible to restore an /etc directory from your installation CD. However, you'd have to manually modify many files to get your system to operate. 

At this point, you have two options: 1. reinstall your OS or 2. see if someone with more GNU/Linux experience will come here and possibly offer another suggestion. I'll try to alert an Admin to your thread. Maybe someone on the Ubuntu Forums staff will have a solution for you.

Sorry about the bad news, my friend. :(

Luck with it!

~Eric

---

### Post by phil66 on 2007-05-20
Eric

Many thanks for the help

Reinstalling not a big chore just time consuming.
I had the feeling a few days ago that reinstall was the only solution

Again thanks for your help

Ray

---

### Post by vtel57 on 2007-05-20
You're welcome, Ray.

A reinstall is not ALL a bad thing. Not only is it a learning experience, but it's an opportunity to correct some things about the first install that you didn't like... new partitions, partition sizes, etc.

We're here if you have any problems...

Luck!

~Eric

---

