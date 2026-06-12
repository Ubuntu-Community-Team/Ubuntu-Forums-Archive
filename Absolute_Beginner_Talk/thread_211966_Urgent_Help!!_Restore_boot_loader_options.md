---
title: "Urgent Help!! Restore boot loader options"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by hellmet on 2006-07-09
Dear all,
I just installed Fedora Core on my computer..
It asked me if it wanted to installits GRUB
I said yes and named "other" to Ubuntu.
But I can no longer load into Ubuntu

This is what I get when I try to 
load into Ubuntu

rootnoverify (hd0,5)
chainloader +1


This is my menu.lst in GRUB of my FC install

#boot=/dev/hdb
default=1
timeout=5
splashimage=(hd0,0)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora Core (2.6.15-1.2054_FC5smp)
	root (hd0,0)
	kernel /boot/vmlinuz-2.6.15-1.2054_FC5smp ro root=LABEL=/ rhgb quiet
	initrd /boot/initrd-2.6.15-1.2054_FC5smp.img
title Ubuntu
	rootnoverify (hd0,5)
	chainloader +1

I am only trying FC5..
Ubuntu is my default OS.
I need to work on it fast..
So please help me soon
thanks
-Sanjay

---

### Post by parkash on 2006-07-09
That lines:

[CODE]
rootnoverify (hd0,5)
chainloader +1
[/CODES]

Are intended for a Windows Partition

I suggest you should boot into Fedora, mount Ubuntu's root partition (or boot) and look into /boot/grub/menu.lst

Then copy the appropriate lines for booting into Ubuntu.

---

### Post by Iarwain ben-adar on 2006-07-09
Hi hellmet,
here's my menu.lst (the ubuntu part)

```

title		Ubuntu, kernel 2.6.15-25-386
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdd7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

```

Just replace the kernel version with your own, and the root location ;)


Iarwain

---

### Post by hellmet on 2006-07-09
> **Iarwain ben-adar said:**
> Hi hellmet,
here's my menu.lst (the ubuntu part)

```

title		Ubuntu, kernel 2.6.15-25-386
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdd7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

```

Just replace the kernel version with your own, and the root location ;)


Iarwain
wow..quick one..
but hey..how do I know the (hdx,y) values??
and if possible..does anyone know how to mount a drive in FC
or is it the same as in Ubuntu??
I'll try anyway

---

### Post by Iarwain ben-adar on 2006-07-09
> Once started, GRUB will show the command-line interface . First, set the GRUB's root device1 to the boot directory, like this:
grub> root (hd0,1)
If you are not sure which partition actually holds these files, use the command find, like this:
grub> find /boot/grub/stage1
This will search for the file name /boot/grub/stage1 and show the devices which contain the file. 
[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

And for the mounting, i assume that it's the same in FC than in Ubuntu.
```
sudo mount /dev/hda
```
Replace hda with your correct drive ;)


Iarwain

---

### Post by parkash on 2006-07-09
If you know the sizes of your Hd's... Maybe you can take a guess by looking at /proc/partitions

```

$sudo cat /proc/partitions

```

And...  That's whay I suggested looking into menu.lst in your Ubuntu partition...

Mounting a volume is easy: 
```

$sudo mount /dev/hda1 /windows/C -o umask=0000

```
That's an example to mount a windows partition with read & write permissions for all users in the /windows/C directory. /dev/hda1 is the disk we're mounting. That's not the best thing to do... But it'l help you now.

---

### Post by hellmet on 2006-07-09
cool...I did it people..
am now typing from my sweet li'l OS
Thanks a ton for all your help..

Hey I also posted a thread :: I broke my theme
can u be of some help??
[http://ubuntuforums.org/showthread.php?t=211583](http://ubuntuforums.org/showthread.php?t=211583)

thanks again..

p.s:: FC5 is so similar to Ubuntu..
Its the only other Linux OS I have tried
apart from Ubuntu and RH(RH was looong back)

---

### Post by hellmet on 2006-07-09
btw THREAD READY FOR DELETION

I have been doing this ever since I got to know that
server is being maintained by some kind hearted individuals
and not canonical
I don't want to waste their money..

---

### Post by Iarwain ben-adar on 2006-07-09
No problem :D

Can you tell us how you exactly fixed it? (Future reference and stuff :D )


Iarwain

---

### Post by parkash on 2006-07-09
Perhaps would you like to try linux...  Gentoo is a good one to start with. FC5 is not what I'd call a proper system to learn linux.

---

### Post by hellmet on 2006-07-09
larwain..i did it like this..

nothing different from what u and others suggested

I tried various hda/hdb values to load the Ubuntu drive
First, foolishly I mounted the sameFC5 drive..
but later was able to mount the Ubuntu drive..
then I checked out the Linux loader options
in its menu.lst

Opened FC5 menu.lst
and added Ubuntu Linux loader lines into 
this menu.lst.

Worked perfectly..
Thank God FC5 is so similar to Ubuntu
Else I wud have had a tough time..

Prakash I'll try that out man..

I had actually tried Xandros and Linspire but
never tried them out they are so much diferent
from FC5 and Ubuntu

---

