---
title: "[SOLVED] grub and external HD"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by daydan on 2007-07-21
Hello,
i'm stuck
i have installed ubuntu on a external hd, on which i created the linux partition with partition magic, in addition to a ntfs partition which already existed. i booted from livecd and installed linux properly on the proper partition. When install finished, when i reboot had some problems. 
First, my bios doesnt allow me to boot from an external HD connected on USB.
I modified menu.lst so he would boot from sda2 (where linux is installed on the external HD)
When i want to boot windows, on my INTERNAL HD, i get this :
GRUB loading, stage 1.5
GRUB loading, please wait

Error 21

here are the modified menu.lst entries

title        Ubuntu, kernel 2.6.20-15-generic
root        (sd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=aa34cb4e-efa4-4a8f-a350-28b96e3ad394 ro quiet splash locale=fr_FR
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (sd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=aa34cb4e-efa4-4a8f-a350-28b96e3ad394 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (sd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professionnel
root        (hd0,0)
savedefault
makeactive
chainloader    +1


Before the modifications, it was (hd1,1) instead of  (sd0,1) for linux partitions.



here is  fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 #linux installed partition
UUID=aa34cb4e-efa4-4a8f-a350-28b96e3ad394 /               ext2    defaults,errors=remount-ro 0       1
# /dev/hda1 #INTERNAL HD where windows is installed
UUID=4688E24288E22FDB /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3 #swap
UUID=0e421213-bc5e-4f47-bab7-335699b94689 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


The thing i dont understand is why grub come with boot when i choose to boot from INTERNAL HD, forbidding me to boot windows. Did i went wrong on menu.lst? What can i do?
Thanks for your help.
daydan

---

### Post by gn2 on 2007-07-21
Have you tried booting Windows from the internal drive with the USB drive connected and powered on?

Grub might not want to play if it can't "see" all the partitions it has listed.

---

### Post by daydan on 2007-07-21
unfortunately, it has no effect when turn on or off.

what could i type to boot /dev/sda2 in "invite" of livecd knowing that my linux partition is mounted in /media/disk automatically

---

### Post by confused57 on 2007-07-21
You could boot the live cd and post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

I noticed that your root partition is ext2:
> # /dev/sda2 #linux installed partition
UUID=aa34cb4e-efa4-4a8f-a350-28b96e3ad394 / **ext2** defaults,errors=remount-ro 0 1

Did you create the ext2 filesystem with Partition Magic?  If you did, it would be best to reinstall Ubuntu and use the installer's partitioner to format to ext3.

Does your internal hard drive boot OK with the external hard drive disconnected?  If it doesn't, you can reinstall Window's IPL code to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If Windows boots OK without the external hard drive connected, I would recommend you install grub to the external hard drive's mbr and use Super Grub Disk to boot to your external hard drive:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by daydan on 2007-07-21
root@ubuntu:~# fdisk -l

Disque /dev/hda: 80.0 Go, 80026361856 octets
255 têtes, 63 secteurs/piste, 9729 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

Disque /dev/hdb: 10.2 Go, 10242892800 octets
255 têtes, 63 secteurs/piste, 1245 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hdb1   *           1        1245    10000431    c  W95 FAT32 (LBA)

Disque /dev/sda: 250.0 Go, 250059350016 octets
255 têtes, 63 secteurs/piste, 30401 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1               1       28428   228347878+   7  HPFS/NTFS
/dev/sda2   *       28429       30335    15317977+  83  Linux
/dev/sda3           30336       30401      530145   82  Linux swap / Solaris
root@ubuntu:~# 

thanks for your help

---

### Post by confused57 on 2007-07-21
Sounds like your external hard drive isn't "spinning up" fast enough during boot, hence the grub error 21.

What I would suggest is restore Window's IPL to the internal hard drive's mbr, using the link in my other reply.

Once you're able to boot Windows from your internal hard drive's mbr, I would recommend you reinstall Ubuntu to your external hard drive, using this guide:
[http://ubuntuforums.org/showpost.php?p=2982257&postcount=2](http://ubuntuforums.org/showpost.php?p=2982257&postcount=2)
Since your bios is not capable of booting first to USB, you should probably just follow steps 1-7...then download the Super Grub Disk, that you can use to boot your external hard drive.

Be sure to use the Ubuntu install cd to format your root partition to ext3.

I can't guarantee this will work, but if it were my system, it is the way I would try setting it up.  You may want to wait to see if someone else has a better suggestion...good luck with it.

---

### Post by daydan on 2007-07-21
Hi,

Thanks to SUPER GRUB i can now boot my internal drive, that is to say Windows, in a normal way. Grub doesnt come anymore to bother me at startup. But, i still can"t boot linux.
I have followed what was given on the page you told me, i have modified the files, etc.. But it seems my external hd isnt recognized. I have tried to boot with Super GRUB, but even there, there are only two partition /dev/hda and /dev/hdb, which are two internal hd (10 go and 80go)
I have updated bios, so it seems it recognizes USB devices. 
Is there a command, that i could type in the 'lilo kind invite" of ubuntu cd (when it asks what to do), so i can boot the external hd.
I havent said something : i didnt reinstalled ubuntu on an ext3, but there file you gave me tells that it has no real importance. 
Again, i dont know what to do to boot linux...

---

### Post by confused57 on 2007-07-21
Glad you were able to get your Windows booting, the Super Grub Disk is pretty amazing.  You're right that ext2 vs ext3 wouldn't cause the problems you're having.  I don't really know what the problem might be...the only thing I could suggest is to make sure your external drive is plugged into the same USB slot as when you installed Ubuntu.  You might also want to enter your bios setup and try enabling something like "USB legacy"...this is a longshot suggestion, I've seen some people have problems with their USB keyboard being recognized in the grub boot menu and enabling this feature corrected it...may be worth trying.

---

### Post by gn2 on 2007-07-22
Could be a partition problem, creating Linux partitions with Partition Magic sometimes doesn't work out OK.

I only use PM in  Windows to create free space, then use the partitioning tool supplied with whatever distro I'm installing to create the new linux partitions in the free space

---

### Post by daydan on 2007-07-22
hi,
i have reinstalled linux with ext3. The only thing i couldnt really do in the commands of the "http://ubuntuforums.org/showpost.php?p=2982257&postcount=2" page is the : sudo mount -t proc /target/proc
In fact, this doesnt work, so i just mounted the linux partition, and i did chroot on it. Is it a command you have to type exactly letter for letter, or just a line that imply to mount the linux partition?
Then: what is the equivalent of /dev/sda2 in (hdnumber,number) form? can i put (sd0,1) in my menu.lst? Anyway, i dont get grub stage at startup, so it wont change something.
In the invite of LIVECD i tried many differents commands like as i dont really what i should type:
i did : initrd=/boot/initrd.img-2.6.20-15-generic ro quiet splash
but it says it cant find the RAM image. i tried also initrd=/media/disk/boot/initrd.img-2.6.20-15-generic (/media/disk/) is the file where my external drive mount automatically. But again the same error. I tried the same with file=/boot/vmlinuz.-2.6......  I tried UUID=theUUIDofthe/dev/sda2partition .But nothing
Moreover when i want to boot normally from livecd i get the busybox. I have checked my UUID in menu.lst and it is the same as the /dev/sda2 partition. But the problem may come that i'm not booting anytime from that partition, i think the livecd creates a temp file in the internal hd. Is there a way to redirect him in maybe editing the livecd?
Well, i have enabled all legacy USB in the bios, i even flash it with a newer version, but nothing... I'm going to see if the constructor of the external HD can help me...

Thank youi again for support, i'm happy not to be alone in this terrifying throat that is linux.

---

### Post by MQMike on 2007-07-22
I have not experimented with USB booting in this context.  About all I can offer you are some tips you might pursue to solve this.

r
First off, in your first post, where you have root (sd0, 1), that is not proper GRUB notation, there is no sdx in GRUB (the sda1, sdb6, etc. are Linux notations for HD and partition number).
In GRUB, all HDs are hdx (ex, (hd0, 1), (hd2, 5), etc.), and the numbering of hard drives and partition starts from zero.  So the first hard drive is hd0, the second HD is hd1, etc.; the first partition is partition 0, the second partition is partition 1, etc.


Second, here’s a link to a How-To for booting Ubuntu on USB external drives.
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
Comments:
It is much easier if your PC BIOS supports booting from USB, and this How-To does address that option using GRUB and that looks very easy.
If your PC BIOS does not support booting from USB, then the How-To looks quite difficult, but entirely doable (but I’m not sure if personally I would try it!).  (Basically, in this second case, you have to build a bootable CD that in turn boots the Ubuntu on the USB.)

It helps to know GRUB methods, then you could freely devise your own experiments to try, such as installing GRUB to the MBR of your internal drive and trying to boot that way.
I notice everyone here uses Herman’s bigpond, and that’s good -- it’s the standard reference.
I have also written a brief How To on GRUB methods (like re-installing GRUB where you want it; editing menu.lst; booting your Linux manually at a GRUB prompt, etc.).

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

Frankly, you really need to know the basic methods Herman talks about and those I have in my How-To there.

There’s so many issues involved, but you may be able to sort it out.
You DO need to know the proper notational scheme for GRUB devices (like (hd0, 1), etc.), and you do need to know what BIOS is calling your hard drives (again, like which one is (hd0)?   which is (hd1)?, etc.).

Solving this problem involves using these GRUB methods to try different booting configurations until one works.  It need not be difficult, but the first step is to gather all the information on your drives.
For example, you might try to install GRUB to the MBR of the internal HD using the GRUB files included on the USB Ubuntu. That would require GRUB commands like root (hdx, y), setup (hdz), quit, where your Ubuntu GRUB files are at (hdx, y) and (hdz) is the MBR of your internal HD called (hdz).  (For example, z may be zero, or 1, etc.).

Sorry that’s all I have, given the info I have, but you can probably get at this using the cited methods.
How about that for homework!  Actually, it’s all very interesting, and the skills are handy.  Hope this helps somewhat.

---

### Post by confused57 on 2007-07-22
MQMike is right, grub recognizes hard drives as (hd0), (hd1), etc, regardless of whether they're SATA or IDE...usually if you use (sd0), (sd1),etc, you'll get an error "unrecognized format or error parsing number".

Since you've reinstalled, you might want to repost your menu.lst.

Since you can't boot first to USB, your Ubuntu entry should have been something like this:
```
title Ubuntu, kernel 2.6.20-15-generic
root **(hd1,1)**
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=aa34cb4e-efa4-4a8f-a350-28b96e3ad394 ro quiet splash locale=fr_FR
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

I should have had you try this earlier, may have saved you some extra work, if this is the problem...since you've reinstalled, your UUID would be different.

---

### Post by MQMike on 2007-07-22
(Insert Note)

Hopefully, you will not need to go to the effort described by that How-To I gave you, which is:

How-To for booting Ubuntu on USB external drives:
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)


But for future reference, for anyone here:

The following explains this a bit better, step-by-step:
[http://ubuntuforums.org/showthread.php?t=80811&highlight=Success+breezy+booted+from+USB+grub](http://ubuntuforums.org/showthread.php?t=80811&highlight=Success+breezy+booted+from+USB+grub)



If your BIOS will boot from USB, we would hope that a solution can be found that is simpler (than the above reference, which by the way is very well done in case anyone should need it).

---

### Post by daydan on 2007-07-23
hello,
i'm going to try these methods that i have tried but not following it step by step, though for me modifiying grub in the linux partition is useless beacause, it is never loaded, MBR is on the external HD, and as the external HD isnt recognize at boot, Grub isnt loaded.
i have found a very interesting method that consist in creating a boot disk that will call the USB drive and then boot on it. But i coulnd't create it as it is not really explained step by step
Here is the link :
[http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html](http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html)
In facts i dont know how to build a kernel on a bootdisk that will also call this linuxrc file that is explained on the tutorial. Does someone can give me some help? 
Anyway, i'll try to follow now the BootFromUSB you gave me, i'll tell you if it worked.
Thank you again

---

### Post by daydan on 2007-07-23
YES! I finally did it : the solution is : [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
Just followed step by step, findind the right attribution of sda with grub command "root'. Then just following everything that was given. I have read a lot a doc about this question, but this is the best. Moreover on others i find variables that are different : for example some tutorial says that ehci_hcd is ehci-hcd; but here it worked with ehci_hcd. Many adds a lot of procedures. 

For those who will encounter the same problem, on Ubuntu 7 installed on  external HD, just follow [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB) and dont waste time as i did (about 2 days searching)

Thanks to everyone who helped me :)
Daniel who is happy with his fresh install!

---

### Post by MQMike on 2007-07-23
Congratulations, daydan!  
Just curious, which part of that How-To did the trick – the first part using GRUB or the second part?  (This can help others, too, as there are lots of folks with the same external USB HD issues.)

EDIT:  Sorry, it sounds like you used the second method, making the CD, right?

Way to go!  You’re to be complimented for getting that so quick!

--Mike

---

### Post by daydan on 2007-07-23
hi :)
the trick came when i realised how to find what was the equivalent of /dev/sda2 (my scsi partition with linux) in (hdx,x) form. I realised how, with the grub commands explained in the tutorial 'root (hdx,x) and using find /(tab) to know what were the files contained in every partition. For a long time i didn't know what to put in my menu.lst, a lot of person and forum said that it was necessarily (hd0,0) as if  the call of USB drive was contained in this 0,0. No. The partition is different for everyone and must be checked with grub commands. 
I did the bootable cd, which i know i should do because of the others tutorials i read, but here it was explained step by step.
I also read it completely, from the beginning to the end, sometimes people (as i did) just copy the commands highlighted without really knowing what they are doing, and most of the time, it crashes. To make it work, you musn't have any error while doing, and try to understand why an error come when you type the command that is given. I was very happy when i did compiled the bootcd iso :)
Ok i stop talking. 
Good luck for the next ubuntu users ;)

---

### Post by johntkucz on 2007-07-31
hello, VERY similar problem:

Okay now,
I'm pretty sure my system can ACCESS the external hd to boot from, but it just blinks black screen white cursor indefinitely (no grub errors).
the device ids for that external 80gb hd are
sda1 = /home
sda2= /
sda3=swap

Whenever I boot from the internal hd (which had windows xp installed on it) it loads grub and gives this error.
GRUB stage 1.5
Grub loading please wait....
error 22

What is up? I can't even seem to boot from windows now. (note upon installing to the external hd, I selected the option to "migrate" the windows account, and that just seemed to create a few empty folders)

should I modify my menu.lst file or something?

From the Live CD

here's fdisk -l 
```
ubuntu@ubuntu:~$ fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7944    63810148+  83  Linux
/dev/sda2            7945        9768    14651280   83  Linux
/dev/sda3            9769       10011     1951897+  82  Linux swap / Solaris

Disk /dev/sdb: 2057 MB, 2057830400 bytes
53 heads, 52 sectors/track, 1458 cylinders
Units = cylinders of 2756 * 512 = 1411072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1459     2009478+   6  FAT16

Disk /dev/sdc: 1021 MB, 1021312512 bytes
129 heads, 16 sectors/track, 966 cylinders
Units = cylinders of 2064 * 512 = 1056768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         967      997367+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(972, 128, 16) logical=(966, 57, 15)

```

__________________

here's fstab

ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0
ubuntu@ubuntu:~$ 


strangely, even though now much shows up in fstab I can still access the 2 partitions of hte external ubuntu drive, the internal windows drive (although can't RW because of ntfs format) and traveldrives.  Why aren't those mounted and accessible drives listed under /etc/fstab or fdisk? how do I get the external hd to boot?

---

