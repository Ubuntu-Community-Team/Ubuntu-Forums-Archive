---
title: "Windows XP boot locks up at Starting Up"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Simon Flavelle on 2007-05-11
Hi,

I am now a happy user of Fawn, I must say. ^^ But I must still write in concerning a problem with my XP installation.

At the first boot, the error displayed was something along the lines of "filesystem unknown", but I managed to get it working by next boot, to the point of "Starting Up..." at which point the boot locks up.

I've tried editing the boot.lst file to include rootnoverify instead of root, but to no avail.

Anybody know what to do?

---

### Post by dstew on 2007-05-11
Please post to the forum the contents of your /boot/grub/menu.lst file, and the output of **sudo fdisk -l**.

---

### Post by Simon Flavelle on 2007-05-11
> **dstew said:**
> Please post to the forum the contents of your /boot/grub/menu.lst file, and the output of **sudo fdisk -l**.

**menu.lst**

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b9062058-de7b-4b0f-b7da-0de9a11857a1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b9062058-de7b-4b0f-b7da-0de9a11857a1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Windows XP Professional
rootnoverify		(hd1,0)
savedefault
makeactive
chainloader	+1

---

**sudo fdisk -l**
Disk /dev/hda: 10.2 GB, 10262568960 bytes
16 heads, 63 sectors/track, 19885 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/hdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       12988   104326078+   7  HPFS/NTFS
/dev/hdc2   *       12989       24509    92542432+  83  Linux
/dev/hdc3           24510       24792     2273197+   5  Extended
/dev/hdc5           24510       24792     2273166   82  Linux swap / Solaris

---

### Post by Simon Flavelle on 2007-05-11
Sorry to bump, but I would really appreciate an answer please.

The OS listing in menu.lst and the output of sudo fdisk -l are in the post above.

---

### Post by confused57 on 2007-05-12
I don't know if it will help, but you can try adding mapping lines to your Window's entry:
```
title Windows XP Professional
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

If you're able to boot first to your hdc drive you could try installing grub to it's mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Using the above link:
```
sudo grub
find /boot/grub/stage1
```
this should return "root (hd1,1)", you would then:
```
root (hd1,1)
setup (hd1)
quit
```

Then booting first to your hdc drive should give you a grub menu...if you get a grub menu at boot, highlight your Ubuntu entry press "e", change root from (hd1,1) to (hd0,1), then press "b" to boot...this change is temporary, but you can see if it will work.  You could also try booting your Windows using this method, by using your original Window's boot entry, but changing root to (hd0,0)...this will let you know if the change will allow you to boot your Window's partition.  As I mentioned, this change is temporary for booting, but it might be worth trying to see if it will work...if it does, then you can make it permanent.  It won't affect your original setup by installing grub to your hdc mbr.

The 3rd link in my signature has some instructions on how to edit your /boot/grub/menu.lst, if the changes work and you want to make it permanent.

---

### Post by Billy McCann on 2007-05-12
Did you resize the XP partition when installing Ubuntu?

---

### Post by Simon Flavelle on 2007-05-12
> **Billy McCann said:**
> Did you resize the XP partition when installing Ubuntu?
I did originally, when I was using 6.06 and had the same problem. I eventually reinstalled XP in its old partition just to get back to using it, and I installed 7.04 in the old ext3 partition yesterday.

confused57: Thanks, except you may have noticed that I'm already using Grub. (That or I don't understand what reinstalling Grub into a drive that already has Grub on it does. :S)

---

### Post by confused57 on 2007-05-12
> **Simon Flavelle said:**
> I did originally, when I was using 6.06 and had the same problem. I eventually reinstalled XP in its old partition just to get back to using it, and I installed 7.04 in the old ext3 partition yesterday.

confused57: Thanks, except you may have noticed that I'm already using Grub. (That or I don't understand what reinstalling Grub into a drive that already has Grub on it does. :S)
I guess the mapping commands didn't work.  Yes, you're using grub, but it's probably installed on your hda drive(hd0)...I was suggesting trying to install grub to your hdc drive(hd1).  If you were to boot into Ubuntu and enter the command:
```
gedit /boot/grub/device.map
```
this would probably show this to be the case...grub must be on the hard drive that you're booting to first in bios...it was a suggestion that may or may not work, but possibly worth trying.  If you actually have grub on your hdc drive mbr, try booting to it first & see if you get a boot grub menu.

---

### Post by Simon Flavelle on 2007-05-12
[quote="device.map"](hd0)	/dev/hda
(hd1)	/dev/hdc[/quote]
Well, I guess this would be the best time to remove the empty hda...?

---

### Post by Billy McCann on 2007-05-12
> **Simon Flavelle said:**
> I did originally, when I was using 6.06 and had the same problem. I eventually reinstalled XP in its old partition just to get back to using it, and I installed 7.04 in the old ext3 partition yesterday.
Simon, 

I've had this same problem.  It's possible that you are stepping over critical Windows files when you resize its partition.  

What you want to do is to reinstall Windows, not allowing it's installer to bother with your partition layout.  I recall from my most recent XP installation that I had to specify to only reformat C:, and not to reformat and recreate both C: and D:.

Once you've reinstalled Windows, GRUB will have been erased from your MBR and you won't be able to boot Ubuntu, only Windows.  

Fear not.

Boot into the Ubuntu LiveCD and follow these instructions.  

[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)  

Let us know if anything is unclear.

---

### Post by tom.clements on 2007-05-12
Hi Simon,

I have had exactly the same problem as you and with a similar history, i.e. having resized the XP partition and then put it back in order to get it to work (see [http://ubuntuforums.org/showthread.php?t=432564)](http://ubuntuforums.org/showthread.php?t=432564)). Where our setups differ is that I have Ubuntu on  a separate hdd (sdc). Have not had any luck in getting it to work though.. even tried modifying ntldr without success (boots windows but not feisty).

Would be interested to see if you get anywhere with it! I am now resorting to selecting boot drive in the bios (can select book drive each time by pressing esc, don't have to go fully into the bios).

Cheers,

Tom.

---

### Post by Simon Flavelle on 2007-05-25
Hi all, sorry for suddenly disappearing. I has to spend less time on the computer, and the parents wouldn't give me the setup CD until today.

So, current situation: I now have XP setup on my C: (or hda) drive, with a partition for my files on the NTFS half of the Ubuntu drive. Would I still be able to accomplish a dual-boot, and can we be 100% sure about it? I don't really want to screw up again. ;-;

---

