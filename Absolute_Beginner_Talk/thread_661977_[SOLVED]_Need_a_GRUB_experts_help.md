---
title: "[SOLVED] Need a GRUB experts help"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2008-01-08
I have a problem that has gone on for about 3 weeks of intensive research & effort. I installed Gutsy on my SATA drive - with no other HD's connected. I had fiesty on an IDE drive and it was installed with no other HD's connected. I put them in the same box and with a lot of [help here I got GRUB to see them both]("http://ubuntuforums.org/showthread.php?t=650900"). 

Now I have installed XP on the IDE drive without the SATA being connected, then powered up with both connected and have been trying to sort it out with Super Grub and after much help and 3 weeks of research including THE HERMAN ZONE I still cannot get Grub to see and boot both drives. (seperately of course. Can someone please help out here?

---

### Post by mikewhatever on 2008-01-08
More info is required to help. Connect both HDDs, boot into Gutsy and post the outputs of the following:
sudo fdisk -lu
sudo cat /boot/grub/device.map

---

### Post by benrboone on 2008-01-08
I have always found it much easier to start with windows xp installed and then add the other operating systems But since that is no longer an option can you post the contents of  /boot/grub/menu.lst on the drive you wish to boot from.

You probally will have one of these on each of your ubuntu drives

to boot windows you will need to have something like the following

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


this will not be exactly right because we don't know if your grub menu comes from the sata or the ide drive.

---

### Post by kindafunnylookin on 2008-01-08
I now have GRUB "seeing" both drives but the XP deive will still not boot, GRUB says Starting up...... and for the first time does not give an error but no boot. 
```

peter@Gutsy7_10:~$ sudo fdisk -lu
[sudo] password for peter:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006f4f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   476230859   238115398+  83  Linux
/dev/sda2       476230860   488392064     6080602+   5  Extended
/dev/sda5       476230923   488392064     6080571   82  Linux swap / Solaris

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2a112a10

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63    78043769    39021853+   7  HPFS/NTFS
peter@Gutsy7_10:~$ 

```

and
```
peter@Gutsy7_10:~$ sudo cat /boot/grub/device.map
(hd0,0) /dev/sda
(hd1,0) /dev/hdc1
My Windows XP on the IDE hard drive
root (hd1,0)
config /boot/grub/menu.lst
peter@Gutsy7_10:~$ 

```

---

### Post by steve-shinn on 2008-01-08
Please post the contents of /boot/grub/menu.lst

---

### Post by kindafunnylookin on 2008-01-08
Here is my /grub/menu.lst  as it is now:


## ## End Default Options ##

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, kernel 2.6.20-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet

title        Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu 7.10, kernel 2.6.20-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet

title        Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title        My Windows XP on the IDE hard drive
root        (hd1,0)
chainloader +1

---

### Post by mikewhatever on 2008-01-08
Try adding the following to the very end of menu.lst:
> #Manually added Windows XP entry 
title           Microsoft Windows XP
root            (hd1,0)
savedefault
makeactive
chainloader     +1


What errors do you get, if any?

On the second thought, you may want to try the following:
> title WindowsXP
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


---

### Post by kindafunnylookin on 2008-01-08
[quote=mikewhatever;4098026]Try adding the following to the very end of menu.lst:


What errors do you get, if any?

I added that and the results were the same - "Starting up....." but XP never booted, there was no error. Will try your edited version now

---

### Post by kindafunnylookin on 2008-01-08
title WindowsXP
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Thank you so much, that did the trick.

---

### Post by mikewhatever on 2008-01-08
My pleasure. \\:D/

---

