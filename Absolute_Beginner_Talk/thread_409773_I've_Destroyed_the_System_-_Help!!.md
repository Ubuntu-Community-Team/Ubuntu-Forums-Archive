---
title: "I've Destroyed the System - Help!!"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-04-14
I accidentally shifted a script file using the mv command into the /bin/sh directory and it has completely corrupted the system. Ubuntu no longer starts up. I have tried putting in the Live CD to no avail. Help!! What do I do? How do I either recover the system or delete the hard disk to start again?

---

### Post by N Clement on 2007-04-14
I assume that you don't want to rescue anything that was on the Ubuntu partition.

What happens when you put in the Ubuntu install CD?  Do you have the boot sequence set correctly in your BIOS to try the CD drive first?

---

### Post by Wake Rider on 2007-04-15
I decided to do a full re-install and lose the data on the hard disk

---

### Post by N Clement on 2007-04-15
I'm sorry to hear that.  Good luck with the fresh install.  If you want a great tutorial on getting a nice clean desktop up and running, I highly suggest [this one,]("http://www.howtoforge.org/the_perfect_desktop_ubuntu6.10") even if you have done it before.

---

### Post by Austin_KW on 2007-04-15
Boot the cd, mount your root partitions and just restore the file you overwrote

---

### Post by Tundro Walker on 2007-04-15
You should be able to solve this by booting from a LiveCD, any distro LiveCD in fact (Knoppix, Mepis, Damn Small Linux, etc).  However, I recommend a Xubuntu LiveCD, since it boots fast and is pretty familiar looking / working.  For Linux noobies, I don't recommend using a Damn Small Linux (DSL) LiveCD, because, while it may boot fast, it's somewhat difficult to use for beginners due to the FluxBox desktop and funky file-manager.

Using a X/K/Ubuntu LiveCD, you'll likely need to mount your HDD first.  The following should help...

1) boot from LiveCD

2) open a terminal screen and type...

```
sudo -i
```...to put yourself into super-user mode (to save you from tying sudo in front of all the next things)

3) make a mount point for your HDD by typing...

```
mkdir /media/ubu
```4) next, get a list of your HDD to figure out which one has your Ubuntu install on it...

```
fdisk -l
```...you should get something back like this...

```
Disk /dev/hda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
[COLOR=Red]**/dev/hda1   *           1        3582    28772383+  83  Linux**[/COLOR]
/dev/hda2            3583        3738     1253070    5  Extended
/dev/hda5            3583        3738     1253038+  82  Linux swap / Solaris
```Tthe main install will generally be lower on HDA#  list, with the higher HDA stuff being the "extended" partition that houses the "linux swap" file.

5) once you figure out which one you're mounting, type...

```
mount /dev/hda1 /media/ubu
```You'd replace "hda1" with whichever hda# has your installation on it.

6) now crank up your distro's file-manager from the terminal so it'll run in super-user mode by typing...

Ubuntu...

```
nautilus
```Kubuntu...

```
konqueror
```Xubuntu...

```
thunar
```7) In the file-manager, surf to the **/media/ubu** folder, then surf around for whatever you hosed up.  If it's a text-config file, you can open it from file-manager as super-user, letting you correct whatever hosed up.  If you need to replace some file, you can jog back over to the live CD files, get whatever you need, then jog back to /media/ubu and plop it in.

EG: A while back, I was messing around with the /boot/grub/menu.lst file, and commented out the "initrd" lines (don't ask).  It totally hosed up my computer, preventing GRUB from loading any OS.  I, however, knew what I did wrong, and knew I could just boot from LiveCD and fix it.  I did the steps above, hopped into my /media/ubu/boot/grub/menu.lst file, fixed it, and then rebooted to save the day.

---

### Post by Austin_KW on 2007-04-15
Now that was a lot more helpful than my post. The file you 'destroyed' is just a link to another file.
I should be ```
$ ls -l /bin/sh
lrwxrwxrwx 1 root root 9 2007-03-13 18:17 /bin/sh -> /bin/dash
 
```

So following the steps in the above post, just change directory and fix the link
```
cd /media/ubu/bin
ln -s dash sh
chmod 777 /bin/sh

```

I realise that you may have reinstalled but in general this is not necessary. You can often boot single user and fix problems or failing that boot a live cd and fix the problems. Everything in unix based syestem is just a file (inc. programs, configuration, users, passwords, drivers, devices ...) If you can boot even a live CD and mount the filesystem you (with help) can fix it.

---

