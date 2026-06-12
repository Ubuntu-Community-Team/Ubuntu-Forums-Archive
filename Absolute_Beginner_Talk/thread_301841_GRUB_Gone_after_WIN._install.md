---
title: "GRUB Gone after WIN. install"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by sindrum_murdnis on 2006-11-17
I just reinstalled windows XP and grub boot loader is no longer popping up asking me which OS to use. Any  help would be much appreciated.

---

### Post by bodhi.zazen on 2006-11-17
> **sindrum_murdnis said:**
> I just reinstalled windows XP and grub boot loader is no longer popping up asking me which OS to use. Any  help would be much appreciated.

[Recovering Ubuntu After Installing Windows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by turbojugend_gr on 2006-11-17
You should install windows first, cause if windows are installed after grub, they wipe it out.

You have to re-install grub. Use this [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by turbojugend_gr on 2006-11-17
Ahh, bodhizazen beat me to it.... ;).

---

### Post by Swab on 2006-11-17
Let us know if it works out, or if you need any more help.

---

### Post by sindrum_murdnis on 2006-11-17
Well that didn't seem to work. I loaded up the ubuntu 6.10 cd and it brings me to an option:-k  screen. The only thing i seen that looked like it might help is F6 which is other boot options. i typed in rescue that didn't work. then i rebooted and did the same all the way down the list F6 rescue. none of this worked. i also tried the graphic version of the help file that didn't work either do to the fact that it wanted me to reformat my hard disk (i tried not selecting it and clicking forward ad tels me it has to be formated)

---

### Post by Swab on 2006-11-17
> **sindrum_murdnis said:**
> Well that didn't seem to work. I loaded up the ubuntu 6.10 cd and it brings me to an option:-k  screen. The only thing i seen that looked like it might help is F6 which is other boot options. i typed in rescue that didn't work. then i rebooted and did the same all the way down the list F6 rescue. none of this worked. i also tried the graphic version of the help file that didn't work either do to the fact that it wanted me to reformat my hard disk (i tried not selecting it and clicking forward ad tels me it has to be formated)

OK, assuming you have one IDE hard drive, and that Windows is on the first partition and Linux is on the second, try the following.  If you have another setup you will need to adjust accordingly.

Boot up with the live CD.

Open up terminal and type

```
sudo su
```

then make a temporary directory..

```
mkdir /target
```

then mount the linux install partition to the temp directory

```
mount /dev/hda2 /target
```

now choot to /target

```
chroot /target
```

OK, now edit your menu.lst

```
nano /boot/grub/menu.lst
```

Scroll to the bottom of the file and add in an entry for Windows

```

title   Windows XP Professional
root    (hd0,0)
makeactive
savedefault
chainloader +1
boot

```

Save the file (ctrl+x , then y to save)

Not sure if this next step is required, but do it for good measure.
Edit: Actually of course it is required, haha.

```
grub-install hd0
```

now reboot, and hopefully you can boot to Windows.

---

### Post by sindrum_murdnis on 2006-11-17
Okay this last entry didn't work either. I didn't realize this until after i tried it but im not able to get into Linux, I can long into windows just fine. also on the last entry i couldn't get the last step to work. so if its needed i need to use it differently than i was.

---

### Post by sindrum_murdnis on 2006-11-17
Also one more thing on step #6 of the last entry i only had to add the last line of text (boot) to the file or i did anyways. im not sure if you wanted me to add another instance or put that there if it was missing?

---

### Post by Swab on 2006-11-17
> **sindrum_murdnis said:**
> Okay this last entry didn't work either. I didn't realize this until after i tried it but im not able to get into Linux, I can long into windows just fine. also on the last entry i couldn't get the last step to work. so if its needed i need to use it differently than i was.

OK, do you have more than one hard drive in your computer?  It seems like we guessed the Linux partition right, maybe we got the Windows one wrong.  What was the error when you tried to last step?  I have to go now, perhaps someone else can help out.  I'll have a look again tomorrow to see if you still need help.

---

### Post by Swab on 2006-11-17
> **sindrum_murdnis said:**
> Also one more thing on step #6 of the last entry i only had to add the last line of text (boot) to the file or i did anyways. im not sure if you wanted me to add another instance or put that there if it was missing?

Sorry, my mistake the "boot" is not needed.  And infact as you say all the Windows stuff was there anyway.  Sorry I am just confusing the issue further.  All that should need to be done is to chroot to the mounted parition and then 

grub-install hd0

edit, and just to make clear, that is hd0 (zero) not hdO

---

### Post by sindrum_murdnis on 2006-11-17
Oh okay sorry about the miss understating. I do in fact have different hard drives. ide hda1 ide hdb1. hda1 is windows and hdb1 is linux. it previously worked and when i had windows installed. then i installed linux, and had to reinstall windows. after the install grub boot loader is no longer there.


hope this gives a clearer picture.

---

### Post by sindrum_murdnis on 2006-11-17
The error was 
Could not find device for /boot: Not found or not a block device.

---

### Post by Swab on 2006-11-17
Ah... hang on, let me check something.

---

### Post by Swab on 2006-11-17
Instead go through the process again, without editing the menu.lst and try...

grub-install /dev/hda

---

### Post by sindrum_murdnis on 2006-11-17
this is what im trying and i keep getting this message
/dev/hda: Not found or not a block device.

```
sudo su
```

```
mkdir /target
```

I use hdb1 here cause thats my linux drive
```
mount /dev/hdb1 /target
```

```
chroot /target
```

```
grub-install /dev/hda
```

---

### Post by Swab on 2006-11-17
OK, I'm not sure then.  Try this thread, several solutions are presented:
[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

---

### Post by sindrum_murdnis on 2006-11-17
okay thanks for the help. Just two more questions. Do i  have to be logged onto my linux hard disk to do these steps(that you have shown me ). How do i load linux with out the boot loader?

---

### Post by AgenT on 2006-11-19
Get your LiveCD out (or any other CD that loads Linux - although do stick with Debian-based ones). When loaded:
1) mkdir /ubuntu
2) mount your boot partition to /ubuntu
3) chroot /ubuntu /bin/bash
4) mount -t proc proc /proc
5) have fun! \\:D/
chroot makes whatever directory you specify become the root. for more information, man chroot.

More information here:
[http://www.debian-administration.org/articles/433](http://www.debian-administration.org/articles/433)

And the most important tip you will ever receive: remove all malware from your PC, including Windows. ;)

---

