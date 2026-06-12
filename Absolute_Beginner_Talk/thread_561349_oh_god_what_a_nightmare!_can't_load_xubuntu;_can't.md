---
title: "oh god what a nightmare!: can't load xubuntu; can't boot from CD"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by alanapost on 2007-09-27
Hello, I am posting in this forum instead of install/ugrade because I am an absolute beginner with linux, and the solution to my problem will probably require a bunch of terminal commands that I am unfamiliar with (which is what got me into trouble in the first place).

I have created a ridiculous problem via carelessness in two matters:

-first, installing LILO via package manager and closing the 'package installation terminal details' window without noting what commands to run post-install
-second, messing up trying to modify a blacklisting record to get my broadcom wifi card working

**Stats:**
xubuntu fiesty
gateway notebook
1G intel celeron
2G RAM
80G HD w/ "default xubuntu recommended install partitions"

In the course of trying to follow tutorials to get the broadcom wifi card working, I tried to blacklist using this sort of method (I can't locate the exact post):

> - go to a terminal window (applications/accessories/terminal)
- gksudo gedit /etc/modprobe.d/blacklist
- go to the bottom of the file and add the following:

# default Broadcom driver, no firmware
blacklist bcm43xx

- save the file and exit
- reboot

unfortunately, I somehow managed to mess up this edit, probably because vi frightens and confuses me, and now i get an error message about that blacklist entry when i try to load xubuntu. it then skips the error, displays the usual xubuntu kernal/drivers/system loading screen, and then flashes an error message, asks if i would like to view debug information. i select 'yes' and get a screen that is blank except for a border of miscellaneous letters and symbols, with the option <OKAY>. if i hit enter i get to a terminal prompt.

i have tried to input a few commands to get information on the problem, but it asks me for a password, and when i put in my root/sudo password it says my login is incorrect.

it would obviously be helpful if i had the laptop with me so that i could post the exact error messages, but i'm hoping that someone could just tell me how to start from scratch.

WORST OF ALL, i have already tried to boot from my xubuntu liveCD (...and a knoppix livecd, and a windows xp install cd, and a regular ubuntu liveCD, and so on) to either repair my xubuntu installation or completely reinstall ANY OS (all my files are on an external so i don't care about wiping the internal HD) but the cdrom is bypassed when the system loads (probably a result of trying to install LILO, something else that i should not have bothered attempting, since GRUB was previously fine. if I F2 on startup, BIOS boot order is cd, usb, external, HD).

does anyone know what might be going wrong? i mean, somehow did i destroy the MBR? and what commands i should put in at the terminal to force my system to boot from cd instead of GRUB, or reset xubuntu's defaults?

i'll update later with specifics of the error messages if there's no catch-all solution for restoring cdrom boot (or repairing xubuntu)

---

### Post by alanapost on 2007-09-27
also: should i try the x-server help tutorials first, or is my issue more complicated and trying to go through those steps might just dig me in deeper?

---

### Post by Terl on 2007-09-27
First, VI is intimidating at times.  Where you use vi <filename> try nano <filename>.  Nano is much easier to use.  Hopefully it is there.

Is it the xserver that is not starting?

---

### Post by alanapost on 2007-09-27
yeah after i get the error about the blacklist entry for my broadcom card and xubuntu tries to load, i get an x-server error and it asks me to restart or relaunch or something after it's been properly configured.

the walkthroughs for reconfiguring x-server seem focused on video card problems. will the reconfiguration steps for x-server be different for me since my problem doesn't involve my video card?

---

### Post by Terl on 2007-09-27
I would run the the reconfigure anyway, especially since it seems to be asking for that.  IIRC it is:  sudo dpkg-reconfigure xserver-xorg

After that is done try a startx and see what goes.

---

### Post by alanapost on 2007-09-27
ok i will give it a go when i get a chance here, and this time i will try not to proceed using the "frustrated guesswork" method. replacing it with the "post on forums" method :oops:

---

### Post by Terl on 2007-09-27
Don't be afraid to try things, just be cautious.  I have destroyed my installs and will probably cock something up again.  :)  The fun is in digging your way back out.  I keep a notebook next to my pc so I can jot notes as I learn new things (or break stuff).  I write down what I did when I try something new so I can use it later as a guide or as part of a repair process.

Curious though, what made you want to try Lilo?  It is nice, I have used it myself with other distros.  I think you can make Grub look nicer and it works well so I just stay with it.  Was Grub not working the way you wanted?

---

### Post by JBAlaska on 2007-09-27
Sooner than later your going to need to boot from your CD drive, Try setting your boot order to CD, HD and leave your external HD unplugged.

Make sure your IDE mode is set to "Both" and your CD drive detect is set to "auto"

You should have your HD on IDE0 (jumper set to master)
and your CD drive on IDE1 (Jumper set to master)

If your system still skips the CD, try Unpluging your HD ribbon cable and boot the live CD that way, at least that will prove that your CD drive is reading properly.

---

### Post by alanapost on 2007-09-30
> **Terl said:**
> I would run the the reconfigure anyway, especially since it seems to be asking for that.  IIRC it is:  sudo dpkg-reconfigure xserver-xorg

After that is done try a startx and see what goes.

ok here is the status on my issue:

after booting into recover mode:

```
root@alana-laptop:~# dpkg-reconfigure xserver-xorg
dpkg-reconfigure: cannot connect to X server
debconf: unable to initialize frontend: Kde
debconf: (DISPLAY problem?)
debconf: falling back to frontend: Dialog
/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed
root@alana-laptop:~#
```

what's the next step? i searched forums for "xserver-xorg is broken" but the results were people with different situations/setups and i don't want to follow instructions that might end up making it harder to fix

---

### Post by alanapost on 2007-09-30
> **JBAlaska said:**
> Sooner than later your going to need to boot from your CD drive, Try setting your boot order to CD, HD and leave your external HD unplugged.

Make sure your IDE mode is set to "Both" and your CD drive detect is set to "auto"

You should have your HD on IDE0 (jumper set to master)
and your CD drive on IDE1 (Jumper set to master)

If your system still skips the CD, try Unpluging your HD ribbon cable and boot the live CD that way, at least that will prove that your CD drive is reading properly.

my boot order is proper in the BIOS and the cdrom is mechanically fine, it's only being skipped over right now because of my problems with xubuntu. GRUB is preceding, or overruling, my BIOS settings (something that happened to me quite a while ago when i put a boot loader application on a computer that subsequently got a rootkit and was extremely difficult to salvage as a result of skipping to HD on boot)

---

### Post by alanapost on 2007-09-30
more info

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225290 bytes

Device         Boot           Start            End             Blocks        Id         System
/dev/hda1   *                      1          9331        74951226      83          Linux
/dev/hda2                     9332          9729          3196935        5          Extended
/dev/hda5                     9332          9729          3196903+   82          Linux swap / Solaris

```

---

### Post by louieb on 2007-09-30
> **alanapost said:**
> my boot order is proper in the BIOS and the cdrom is mechanically fine, it's only being skipped over right now because of my problems with xubuntu. GRUB is preceding, or overruling, ...
The inability to boot to a CD has nothing to do with GRUB or LILO or xUbuntu. (not going to get technical here) 
How do you know your CD drive is ok?  IF BIOS is set to **boot to the CD 1s**t and you have **bootable CD** in the drive - then it should boot to the CD. 

I take it from your fdisk post you can boot to the hard drive.  Just wondering what would happen if you put in a music CD will it play it? Not olny will it play it but will if play from start to finish. I had to replace an older CD drive the other day somewhere in the middle of reading a CD it would scramble some bits - not a good thing.

---

### Post by alanapost on 2007-09-30
firstly, i'm a "linux beginner", not "computer beginner".

secondly, as a technician i don't believe in coincidences. the drive's been fine with bootable/livecd, dvd, cd, cdr media for 2 years of windows xp, and 2 months of ubuntu, and spins when something's inserted, and shows up in the device manager, and then all of a sudden it stops working as expected *immediately after* some xubuntu package changes/additions are applied, i am inclined (crazy as it may sound) to think that it's not a problem with the hardware.

---

