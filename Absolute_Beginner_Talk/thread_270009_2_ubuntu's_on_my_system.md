---
title: "2 ubuntu's on my system?"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2006-10-02
When I dual boot, it shows me the different OS on my computer. It shows Ubuntu, ubuntu mem test, ubuntu, ubuntu mem test, windows xp. Are the two ubuntus the same or did I mess up my install?

---

### Post by Imsati on 2006-10-02
I was confused about that too when I first saw it on mine. Reboot and look for the kernel versions after Ubuntu when you get to that screen. THe last number or 2 numbers should be different. One is simply a newer kernel. It was suggested to me to just leave it be in case anything ever happens (on the remote possibility) to the current kernel, that way you can just load the previous kernel and be on your merry way.

~Jay

---

### Post by blackened on 2006-10-02
The previous kernel version entries won't cause any harm by being there, but if they really annoy you, then you can either comment them out, or delete them in /boot/grub/menu.lst. It would be a good idea to leave at least the two most recent versions though.

---

### Post by bulldog on 2006-10-02
Well memtest twice is not the usual thing to see......:D 

Did you a new install by any chance?

If you did you have to understand Ubuntu will **not** overwrite another install like Windows likes to do.

When you do a fresh install you have to remove the old one.........or you end up with multiple Ubuntu's:D

---

### Post by tdrusk on 2006-10-02
I am pretty sure it showed up after I updated my computer a lot. So it should be fine, and not taking up a lot of space correct?

---

### Post by Imsati on 2006-10-02
> **bulldog said:**
> Did you a new install by any chance?

If you did you have to understand Ubuntu will **not** overwrite another install like Windows likes to do.

When you do a fresh install you have to remove the old one.........or you end up with multiple Ubuntu's:D

Just curious, wouldn't you see something was amiss when entering the partitioning stage of the install, then? Free HDD space vs space you know the HDD has (or should have)?

Maybe I read the post wrong? I'm just a bit confused.

---

### Post by bulldog on 2006-10-02
Well look in your media folder or do ```
sudo fdisk -l 
``` to see how your hdd is partitioned.

But if you did a single install it should be allright.

You can comment out ## the lines you don't want to see in GRUB.

If you're sure you don't need them you can simply delete them with gedit.
```
gksudo gedit /boot/grub/menu.lst 
```

But don't be to hasty,just comment them first and remove later.
Maybe it make sense to make a copy of your menu.lst,just in case things go wrong.```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup 
```

---

### Post by GStubbs43 on 2006-10-02
If you open synaptic package manager and search for linuximage, does it show two packages that are something like linux-image-2.6-*? If it does, remove the one with the lower number, like 23 instead of 27 or something...

---

### Post by tdrusk on 2006-10-02
> **bulldog said:**
> Well look in your media folder or do ```
sudo fdisk -l 
``` to see how your hdd is partitioned.

But if you did a single install it should be allright.

You can comment out ## the lines you don't want to see in GRUB.

If you're sure you don't need them you can simply delete them with gedit.
```
gksudo gedit /boot/grub/menu.lst 
```

But don't be to hasty,just comment them first and remove later.
Maybe it make sense to make a copy of your menu.lst,just in case things go wrong.```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup 
```
These are my partitions:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         653     5245191    7  HPFS/NTFS
/dev/hda2             654        7111    51873885   83  Linux
/dev/hda3            7112        7296     1486012+   5  Extended
/dev/hda5            7112        7296     1485981   82  Linux swap / Solaris
```

---

### Post by GlennB on 2006-10-02
> **bulldog said:**
> Well memtest twice is not the usual thing to see......:D 



I agree, but on the other hand the o.p. did not mention any 'recovery mode' options on the list at all, which I would expect to be there.

fuzzyhair, you should probably check in the file

```
/boot/grub/menu.lst
```

to see what is listed in between the lines that say:

```
## ## End Default Options ##

...and...

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Take a close look at the lines in each stanza labelled 'title' to see if you have two the same, or if there are two similar entries that have different kernel versions. It may be that an Ubuntu update has added a new kernel version for you.

Regards,

Glenn.

---

### Post by bulldog on 2006-10-02
> **Imsati said:**
> Just curious, wouldn't you see something was amiss when entering the partitioning stage of the install, then? Free HDD space vs space you know the HDD has (or should have)?

Maybe I read the post wrong? I'm just a bit confused.

When you pay attention and being informed about your hdd you should notice it I guess.

But most people pop in the cd and do a reinstall and not concerning about removing the old one,you should have enough space though.

I see too many people coming around which haven't the slicest idea what's inside the grey box.

---

### Post by bulldog on 2006-10-02
> **fuzzyhair said:**
> These are my partitions:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         653     5245191    7  HPFS/NTFS
/dev/hda2             654        7111    51873885   83  Linux
/dev/hda3            7112        7296     1486012+   5  Extended
/dev/hda5            7112        7296     1485981   82  Linux swap / Solaris
```

You have just one install,don't worry.:D

---

### Post by Imsati on 2006-10-02
> **bulldog said:**
> When you pay attention and being informed about your hdd you should notice it I guess.

But most people pop in the cd and do a reinstall and not concerning about removing the old one,you should have enough space though.

I see too many people coming around which haven't the slicest idea what's inside the grey box.


Gotcha. Partitioning has always been second nature for me when using MS stuff, so I guess I'm just always aware of it. Took a bit of getting used to with (K)Ubuntu, but after five minutes, I had it down.

---

### Post by tdrusk on 2006-10-02
```
title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

#title		Ubuntu, kernel 2.6.15-23-386
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 #ro #quiet splash
#initrd		/boot/initrd.img-2.6.15-23-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 #ro #single
#initrd		/boot/initrd.img-2.6.15-23-386
#boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

```

This is what my file looks like now. Did I do everything right? (I just copied that one section.) I'm sorry about not mentioning the recovery modes. I was doing it from memory.

---

### Post by Old Pink on 2006-10-02
See my thread "[[COLOR=DarkOrange]Too Much Ubuntu?[/COLOR]]("http://ubuntuforums.org/showthread.php?t=255387")" for information on your situation, and detailed information on how to hide/remove the extra options.

---

### Post by bulldog on 2006-10-02
> **fuzzyhair said:**
> ```
title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

#title		Ubuntu, kernel 2.6.15-23-386
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 #ro #quiet splash
#initrd		/boot/initrd.img-2.6.15-23-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 #ro #single
#initrd		/boot/initrd.img-2.6.15-23-386
#boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

```

This is what my file looks like now. Did I do everything right? (I just copied that one section.) I'm sorry about not mentioning the recovery modes. I was doing it from memory.


Nothing wrong with that.:D

False Alarm.

---

### Post by tdrusk on 2006-10-02
Thanks for the help guys. I love the awesome Ubuntu Community!

---

