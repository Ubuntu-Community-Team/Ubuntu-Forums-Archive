---
title: "[SOLVED] Crash when booting 7.10"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by SwarmReignsDown on 2007-11-05
This is my fist time installing 7.10. I used the alternate AMD64 iso. When booting, I select ubuntu from the list and my display goes blank and I get two flashing lights on my keyboard. The only thing I could find to try was reconfiguring xorg but that did not work. The strange thing is that when I go into recovery and type "startx", the GUI loads and I am logged in as root. 

Does anyone know what the problem might be? Sorry if some of the terminology is wrong.

---

### Post by mivo on 2007-11-05
Are you trying to boot from the Live CD? If so, press F6 in the boot menu of the CD (where it asks you what you want to do) and remove "quiet" from the line, and change "splash" to "nosplash". This way you will see what is going on.

If you already installed Ubuntu, press ESC in the Grub menu (where it counts down), select the first entry, hit "e"dit and remove "quiet" and "splash" (if present). Add "nosplash", then hit "b"oot. If your computer completely restarts after this and does not continue where you had stopped, please let us know -- there is another way of doing it.

---

### Post by Bliepo32 on 2007-11-05
This is related to a bug. Please read [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910) including the comments.

---

### Post by rsambuca on 2007-11-05
> **Bliepo32 said:**
> This is related to a bug. Please read [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910) including the comments.

How do you possibly know that the OP's problem is related to that launchpad bug?  It is hardware related, and the OP didn't give any details.

---

### Post by SwarmReignsDown on 2007-11-05
Ok, I tried all the suggestions and nothing worked. I went ahead and reinstalled from a live CD (which worked fine) but after installing I have the same problem when booting. My monitor actually goes into standby so maybe it's the video card. Here is the hardware I'm using:

NEC 16X DVD±R DVD Burner Black IDE/ATAPI Model ND-3500A BK - 

GIGABYTE GA-K8NE 754 NVIDIA nForce4 4X ATX AMD Motherboard - 

mushkin 2x512MB 184-Pin DDR SDRAM DDR 400 (PC 3200) Desktop Memory Model 991093 -

Western Digital Caviar SE WD800JD 80GB 7200 RPM SATA 3.0Gb/s Hard Drive -

AMD Athlon 64 3000+ Newcastle 2.0GHz Socket 754 Processor Model ADA3000AXBOX -

SAPPHIRE 100106SR-RD Radeon X850XT 256MB 256-bit GDDR3 PCI Express x16 Video Card - 

Any further suggestions would be most welcome, thanks.

---

### Post by rsambuca on 2007-11-05
I'd say with about 99% certainty it is due to your ATI card.  Unfortunately, I am an nVidia guy, so I can't help you with this one.

---

### Post by mivo on 2007-11-05
You need to boot with "nosplash" and without "quiet", or you won't see what is going on. I had the "screen goes black and eventually into standby mode" problem too, and I have an Nvidia card (on this box anyway, the other one has an ATI card). 

You may have the same Grub problem I had, so if you are up for another try, give this a whirl (type in the boded bits):

Boot from the Live CD into the live environment. Open a terminal (Applications -> Accessories -> Terminal) and go to root (**sudo -i**) and change to your /mnt folder (**cd /mnt**). Create a mount point for the drive where your Ubuntu installation is on  (**mkdir mydisk**). Now you need to find the name of the drive and the partition. Type: **dmesg**. You will get a whole lot of stuff. You are looking for a part that looks roughly like this:

```

[   32.608406] sd 4:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
[   32.608519] sd 4:0:0:0: [sda] Write Protect is off
[   32.608605] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.610747] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.610887]  sda: sda1 sda2 sda3

```

The last line in particular. Your information is likely to be different. Now when you have this information, type in: **mount /dev/sda1 /mnt/mydisk**  (replace the sda1 with your file system's name). This will mount the disk. If you did this correctly, you can now access the files on the disk. If this part fails, tell us more about your hard drive setup (partitions, etc.) Do **cd mydisk**.

Type: **nano /boot/grub/menu.lst**

Scroll down to where the ## lines (comments) end. In the "kernel" line, add *nosplash irqpoll* and, if it is there, remove *splash* and *quiet* (not the one at the bottom). Do not copy and paste, just make the changes.

```

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a005caf2-e969-4eff-8e8d-c1971a2ba227 ro irqpoll nosplash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```

Save the file and reboot from the hard disk. If this worked, you should no longer get a blank screen but at least a more meaningful error message.

(It is 4am, and I hope I didn't typo or miss something. :))

---

### Post by SwarmReignsDown on 2007-11-05
Thanks for the reply. I can't seem to get this to work. I can find the section in question but maybe I'm specifying the wrong drive.

```
[   42.528554]  sda: sda1
[   42.543321] sd 0:0:0:0: [sda] Attached SCSI disk
[   42.543521] sd 1:0:0:0: [sdb] 156250000 512-byte hardware sectors (80000 MB)
[   42.543554] sd 1:0:0:0: [sdb] Write Protect is off
[   42.543581] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   42.543593] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.543656] sd 1:0:0:0: [sdb] 156250000 512-byte hardware sectors (80000 MB)
[   42.543686] sd 1:0:0:0: [sdb] Write Protect is off
[   42.543712] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   42.543723] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.543751]  sdb: sdb1 sdb2 < sdb5 >

```

I tried them all but I get the error:

```
root@ubuntu:/mnt# mount /dev/sdb1 /mnt/mydisk
mount: mount point /mnt/mydisk does not exist
```

Tried this with sdb1 and sdb2 and sda1. I may be typing something wrong. Thanks.

---

### Post by mivo on 2007-11-05
Naturally, I made a 4am mistake. :)  Use:

**mount /dev/sda1 /mnt/mydisk**

(the same name you used when you made the point with mkdir before). I'll fix my post.

---

### Post by SwarmReignsDown on 2007-11-05
Well, I got the disk mounted, but when typing nano /boot/grub/menu.lst, the file that opens is empty. :confused:

---

### Post by rsambuca on 2007-11-05
You will need to use:

sudo nano /mnt/mydisk/boot/grub/menu.lst

or 

gksudo gedit /mnt/mydisk/boot/grub/menu.lst

---

### Post by mivo on 2007-11-05
No typo in **nano /boot/grub/menu.lst** ?

The partition you mounted may not be the right one. After you mounted it, do **cd mydisk** and then **ls**. What do you see? If you don't see something like this:

```
bin    dev   initrd      lib32       media  proc  srv  usr
boot   etc   initrd.img  lib64       mnt    root  sys  var
cdrom  home  lib         lost+found  opt    sbin  tmp  vmlinuz
```

.... then you mounted the wrong partition. Do **cd ..** to go back and then mount the others. I saw you had another disk, sda. Did you try to mount sda1?

---

### Post by mivo on 2007-11-05
> **rsambuca said:**
> You will need to use:
sudo nano /mnt/mydisk/boot/grub/menu.lst


**sudo -i** put him into root mode. I figured it is easier than having to type sudo in front of some commands. :) It changes the prompt to *root@hostname:$* also.

---

### Post by SwarmReignsDown on 2007-11-06
Well, I got through those steps and added *irqpoll nosplash* and now it boots fine. Go figure. Thanks to both of you for your help. :)

---

### Post by rsambuca on 2007-11-06
Good stuff!  Mark the tread as solved (in the thread tools).

---

### Post by mivo on 2007-11-06
> **SwarmReignsDown said:**
> Well, I got through those steps and added *irqpoll nosplash* and now it boots fine. Go figure. Thanks to both of you for your help. :)

Awesome! Glad we could be of help. :)  Welcome to Ubuntu -- the rest of the journey should be smoother!

---

