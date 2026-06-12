---
title: "Boot time?"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-11-22
Well, I'm not sure if booting Ubuntu is extremely slow for everyone, but I have to ask. It usually takes about 5 to 10 minutes from the time I hit the power button, until I finally get to my desktop. I googled it and found some site that got hacked or defaced or something: 

*** Delete due to lanugage ***

Anyone have some tweaks or tricks to speed up my boot process without compromising the normal speed of my computer?

---

### Post by taurus on 2006-11-22
Are you using Dapper or Edgy and what is the spec of your machine?  It shouldn't take that long to boot either one (I think Edgy boots a little faster than Dapper).  What is the step that you see on the monitor when it takes the longest to process?  Is it something about mounting root filesystem?

p.s.  I've decided to remove your link because I don't that is an appropriate language here in these forums...

---

### Post by voodoonirvana on 2006-11-22
Sorry about the link. I'm running Dapper on a Gateway SOLO 5350, the longest part is the very first (out of 3) steps when it says that it is unloading/unpacking the GRUB. I have a 20 gig HD and 256 MB or RAM. I'm not even using a whole lot of my HD space either, still have about 13 gigs free.

---

### Post by zekonology on 2006-11-22
Hi taurus, i also have the same problem coz my ubuntu takes about 1 minutes to boot up.. it stop a while at "Checking file system".. seems like it currently mounting file system.. do you know how to speed up this? I'm using a laptop with 1.6GHz Intel Centrino, 512MB DDR2 and Intel 915GM. Thankss

---

### Post by voodoonirvana on 2006-11-22
> **zekonology said:**
> Hi taurus, i also have the same problem coz my ubuntu takes about 1 minutes to boot up.. it stop a while at "Checking file system".. seems like it currently mounting file system.. do you know how to speed up this? I'm using a laptop with 1.6GHz Intel Centrino, 512MB DDR2 and Intel 915GM. Thankss

Did you mean 10 minutes? 1 minute is not a long boot time.

---

### Post by taurus on 2006-11-22
> **zekonology said:**
> Hi taurus, i also have the same problem coz my ubuntu takes about 1 minutes to boot up.. it stop a while at "Checking file system".. seems like it currently mounting file system.. do you know how to speed up this? I'm using a laptop with 1.6GHz Intel Centrino, 512MB DDR2 and Intel 915GM. Thankss
I don't think it would take more than a 1 minute.  Next time when you boot, use a watch to see how long does it take to pass the "Checking file system..." step?  In the meantime, I would like to see the outputs of these three commands from a terminal, Applications -> Accessories -> Terminal.

```
sudo fdisk -l
cat /etc/fstab
cat /boot/grub/menu.lst  <-- you don't have to show the whole thing if you don't want; just the part about your kernel, first entry...
```

---

### Post by voodoonirvana on 2006-11-22
Did my thread just get hi-jacked, or were you asking *me* for those outputs of those commands?:confused:

---

### Post by taurus on 2006-11-22
For both of you...  ;)

---

### Post by voodoonirvana on 2006-11-22
> **taurus said:**
> For both of you...  ;)

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2342    18812083+  83  Linux
/dev/hda2            2343        2432      722925    5  Extended
/dev/hda5            2343        2432      722893+  82  Linux swap / Solaris

-----------------------------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

------------------------------------------------------------------------

# kernel        /vmlinuz root=/dev/hda2 ro

------------------------------------------------------------------------

I'm not sure which part about the kernel you wanted so I assumed it was the first one.

---

### Post by taurus on 2006-11-22
If you scroll down (/boot/grub/menu.lst) to about two screens, you will get to the section where there are no #s in front.  It should say something like

title   Ubuntu (blah blah blah...)
root (hd0,0)
kernel  /boot/vmlinuz-blah-blah-blah...
initrd  /boot/initrd-blah-blah-blah...
blah blah blah...
blah blah blah...

That's what I want to see.

---

### Post by voodoonirvana on 2006-11-22
title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash elevator=cfq
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash elevator=cfq
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash elevator=cfq
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
----------------------------------------------------------------------------------

That what you wanted to see?:-k

---

### Post by taurus on 2006-11-22
What if you remove the "elevator=cfq" at the end of the kernel line?  Reboot and see if it speeds up the booting process...

```
gksudo gedit /boot/grub/menu.lst
```
```

title Ubuntu, kernel 2.6.15-27-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-386
savedefault
boot

```

---

### Post by voodoonirvana on 2006-11-22
> **taurus said:**
> What if you remove the "elevator=cfq" at the end of the kernel line?  Reboot and see if it speeds up the booting process...

```
gksudo gedit /boot/grub/menu.lst
```
```

title Ubuntu, kernel 2.6.15-27-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-386
savedefault
boot

```

Cool, that seemed to cut my boot time down by about half. Would it be possible to briefly explain what exactly you had me do, and how that worked. Thanks a lot by the way.

---

### Post by taurus on 2006-11-22
Personally, I have never seen that option, elevator=cfq, in the kernel before so I need to look it up to see exactly what it does.  Just so you know, I am still learning so don't expect I know everything, not even close.  

Now that it takes a little less time to boot Ubuntu, I guess you are happy!  ;)

---

### Post by K.Mandla on 2006-11-22
> **zekonology said:**
> Hi taurus, i also have the same problem coz my ubuntu takes about 1 minutes to boot up.. it stop a while at "Checking file system".. seems like it currently mounting file system.. do you know how to speed up this? I'm using a laptop with 1.6GHz Intel Centrino, 512MB DDR2 and Intel 915GM. Thankss
One minute for a 1.6Ghz sounds about right if it's running straight Ubuntu, in my experience.

---

### Post by K.Mandla on 2006-11-22
> **taurus said:**
> Personally, I have never seen that option, elevator=cfq, in the kernel before so I need to look it up to see exactly what it does.  
It's an [IO queueing tweak]("http://www.ubuntuforums.org/showthread.php?t=119546"). On some systems it improves start times. And it seems on some systems, it makes them worse. ;)

---

### Post by voodoonirvana on 2006-11-22
> **taurus said:**
> Personally, I have never seen that option, elevator=cfq, in the kernel before so I need to look it up to see exactly what it does.  Just so you know, I am still learning so don't expect I know everything, not even close.  

Now that it takes a little less time to boot Ubuntu, I guess you are happy!  ;)

I see, but yes I'm very thankful for all the help I've gotten here. Thanks.

---

### Post by voodoonirvana on 2006-11-22
Hey, I just found this:
[https://launchpad.net/distros/ubuntu/+ticket/2485](https://launchpad.net/distros/ubuntu/+ticket/2485)

It told me to remove the "quiet" and the "splash", so I did that and I'm about to reboot right now. I'll keep you updated on how it goes.

---

### Post by voodoonirvana on 2006-11-22
Okay, well I just rebooted with the new changes and they didn't seem to really do anything at all. One weird thing though was that instead of going into that tan screen withe loading bar after it loads the GRUB, it did it all in one screen, and just showed all the things being loaded one by one. Pretty weird.

---

### Post by K.Mandla on 2006-11-23
That's what it should do. As I understand it, "quiet" masks some of the output to the screen, while "splash" shows you the familiar brown splash screen. So removing those from the boot line gave you the background messages that occur during boot.

---

### Post by taurus on 2006-11-23
> **voodoonirvana said:**
> Okay, well I just rebooted with the new changes and they didn't seem to really do anything at all. One weird thing though was that instead of going into that tan screen withe loading bar after it loads the GRUB, it did it all in one screen, and just showed all the things being loaded one by one. Pretty weird.
Actually, I like the system to tell me what is being loaded in case there is a problem, I know exactly which process causes it...

---

### Post by zekonology on 2006-11-26
> **K.Mandla said:**
> One minute for a 1.6Ghz sounds about right if it's running straight Ubuntu, in my experience.

Sorry for not being around days ago.. I don't have internet connection at home. 1 minute is quite long compare to my windows.. my xp boots faster than my edgy.. I'll try remove that option "elevator=cfq" first and see if this works for me.. thanks anyway guys...

---

### Post by zekonology on 2006-11-26
hello.. correction here.. my xp takes 31 sec to boot while my edgy takes 1 min 50 sec. Plus, i don't have that "elevator=cfq" inside my menu.1st. Anyone?

---

### Post by zekonology on 2006-12-02
hi everyone, i already knew what caused my edgy to boot very slow. fsck forced to check my drives everytimes i boot so i just disabled it inside my fstab and my edgy boot really fast..

---

### Post by handaxe on 2006-12-07
Disabling fsck at boot is all very well, but then remember to run fsck on the drive on occasion. It is safer that way, as fsck is in at boot for a reason other than slowing it down:).

A cron job should do... (on drives that you can unmount whilst running, that is).

I too have fsck every boot rather than every 30 (blast!) ... investigating.
HA

---

