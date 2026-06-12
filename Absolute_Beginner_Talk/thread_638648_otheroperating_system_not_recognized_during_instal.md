---
title: "otheroperating system not recognized during install"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by 720iD on 2007-12-12
i have recently been trying to install ubuntu alongside my existing windowsXP. when i boot the live CD i get an error message "I/O error at logical block fd0" live CD will then boot up and i can run the installer, i can see all my drives and partitions but problem is that the installer does not recognise my XP operating system. i can explore the partitions form ubuntu system but the installer is not recognising the operating system on it. i use a very lite version of xp and tying to install ubuntu710

i appreciate any suggestions.

---

### Post by Drate on 2007-12-12
You say it recognizes your partitions?  What then are you expecting in the way of it recognizing your XP?  As far as the installer is concerned the partitions are all you need.  Furthermore, if you know what partition Windows is on, you can select that partition from the manager, and make the mount point "/windows" or even make your own custom mount point.  Make sense?

---

### Post by mridkash on 2007-12-12
Do you mean to say that you can't boot(start) the computer in Windows?

---

### Post by 720iD on 2007-12-12
> **Drate said:**
> You say it recognizes your partitions?  What then are you expecting in the way of it recognizing your XP?  As far as the installer is concerned the partitions are all you need.  Furthermore, if you know what partition Windows is on, you can select that partition from the manager, and make the mount point "/windows" or even make your own custom mount point.  Make sense?
the installer on gutsy recognises other operating systems and adds them to grub menu when i boot. on previous versions of ubuntu this was done automatically and other os' where visible on grub on reboot after install. 7.10 has page on the installer that identifies and labels other os'. i have xubuntu710 dualbooting with XP on an old IBM. the installer recognised this operating system and added it to the grub boot menu. i tried a couple of weeks ago to install ubuntu710 with XPand the other operating system was not recognised. i though that this would be okay and XP  would be available on grub boot menu as it was with older type installer, however i was wrong. XP was not added to the grub boot menu and i had to reinstall windowsXP. now i am in this position again of not being able to install ubuntu without i losing XP. although XP will still be there but i could not boot it.

i am not sure if make sense now:confused:

---

### Post by 720iD on 2007-12-12
> **mridkash said:**
> Do you mean to say that you can't boot(start) the computer in Windows?
yes windows wont boot after installing ubuntu. and the part on the installer doesnot recognize any other operating systems. it sees all my drives and data. but does not recognise them as a bootable os.

---

### Post by Niniel on 2007-12-12
No need to reinstall windows though, all you'd need to do is restore the MBR. 

If you are having problems with Grub, try the GaG boot menu. In that case though, don't install Grub to the windows partition, but to the Linux partition. GaG will then call Grub, which will start Ubuntu. At least that's what works for me (I just wanted a "graphical" boot menu :) )

Btw, my installer also wouldn't recognize Windows, but that was only during the "importing settings/files" part. Everything else worked, including installing Grub.

---

### Post by OffAxis on 2007-12-12
you shouldn't have needed to reinstall XP, just fix the grub loader.

What's your hard drive setup look like?

---

### Post by 720iD on 2007-12-12
> **Niniel said:**
> No need to reinstall windows though, all you'd need to do is restore the MBR. 

If you are having problems with Grub, try the GaG boot menu. In that case though, don't install Grub to the windows partition, but to the Linux partition. GaG will then call Grub, which will start Ubuntu. At least that's what works for me (I just wanted a "graphical" boot menu :) )

Btw, my installer also wouldn't recognize Windows, but that was only during the "importing settings/files" part. Everything else worked, including installing Grub.

this sounds like a similar problem when it comes to importing settings and files.  

when i did this last time i tried to restore MBR using Super grub disc. i could not do it, i cant remember why now but it was quicker for me to reinstall xp. would like to get it done prooperly this time. 

not sure how to use GaG

---

### Post by 720iD on 2007-12-12
> **OffAxis said:**
> you shouldn't have needed to reinstall XP, just fix the grub loader.

What's your hard drive setup look like?


hitachi deskstar BasicHDD HD0 - 372.6GB
logical disk primary 36GB NTFS [Windows]
extended partition 
logical disk extended (C: FAT32 [media]
logical disk extended (E: FAT32 [media]

hitachi deskstar BasicHDD HD1- 232.8GB
logical disk primary EXT3  10GB[/ ]
logical disk primary SWAP 900MB
logical disk primary FAT32 [media]
logical dsik primary FAT32 [media]

---

### Post by OffAxis on 2007-12-12
Please post your 

```
/boot/grub/menu.lst
```
file.

---

### Post by 720iD on 2007-12-12
> **OffAxis said:**
> Please post your 

```
/boot/grub/menu.lst
```
file.
can i do this from a live CD before install as i have not committed to the ubuntu install this time? i lost my previous ubuntu install when i plastered over it with XP.

---

### Post by OffAxis on 2007-12-12
not so much... the menu.lst file doesn't exist if you haven't installed ubuntu.
Once you've installed it you've got some options for booting, editing grub, etc.

---

### Post by 720iD on 2007-12-12
i am worried about the i/o error message that i get when i first boot a live CD [i mention this in my OP]

i/o error at logical block fd0, i think this may have soemthing to do with why the installer is not seeing my XP os. i think that XP is installed on hd0. is fd0 the same as hd0? i know they are not the same because one is F and one is H but i mean are they related in someway.

---

### Post by dstew on 2007-12-12
fd0 may be referring to a floppy disk.

---

### Post by 720iD on 2007-12-12
i dont want to go through the install again until i know what might be happening. 
if i install ubuntu without it recognising windowsXP i will be right back to square one
 installing XP over my ubuntu installation. Aarrggh the circle never ends!!

does anybody know what is going on here. i tried searching for I/O error on the forums but get now results.

---

### Post by 720iD on 2007-12-12
> **dstew said:**
> fd0 may be referring to a floppy disk.

that would make sense only i dont have a floppy

---

### Post by OffAxis on 2007-12-12
fd0 is typically the first floppy drive.

Have you disabled the floppy in your bios?
There may be in option for it as 'Enable/Disable' as well as within the boot sequence.

The install may also be temperamental if you've got a USB flash drive plugged in or a zip drive.

---

### Post by 720iD on 2007-12-12
i will try both of those things, i do often have usb sticks or memory cards left in my devices. i am sure that there is no bios settings for a floppy on my system but i will check that too thanks for the advice i will let you know soon as.

---

### Post by mridkash on 2007-12-12
That problem happened with me too. Don't worry, install ubuntu as usual, even if it doesn't recognize windows. Later you can add a single line in menu.lst file and boot into windows as usual. there is a thread somewhere in this forum, which shows how you can do that.

visit [http://ubuntuforums.org/showpost.php?p=3670296&postcount=9](http://ubuntuforums.org/showpost.php?p=3670296&postcount=9)

---

### Post by 720iD on 2007-12-13
that thread is interesting might be some help thanks. 
i do think there is something wrong with my windows partition also. the last two times i installed XP the installation would not let me choose fat32 formatting for the partitions. i would generally always format with  FAT32 but i was only allowed to install with NTFS. i am not sure why this has happened and though i thought it was problem i never thought it wold be too serious so i just formatted the partition with NTFS.

---

### Post by 720iD on 2007-12-13
i disabled the floppy option from the boot menu and i booted into ubuntu live CD. i still get message I/O error on Device fd0, logical block0. the live CD continued after this but then gave me some more similar errors with numbers 228.100189  error on Device fd0, logical block0
then 266.181771 error on Device fd0, logical block0
i then got into ubuntu live and tried the installer still not recognizing any other operating system. i discovered while i was running the live CD that my old install of ubuntu is still on the partition although windows has erased grub from MBR.

also removing usb driives and memory cards has not made any difference.

---

### Post by 720iD on 2007-12-15
i changed around the configuration of my partitions. i now have both windowsXP and ubuntu on the first drive, windows on first partition ubuntu on second partition. the installer likes this set up better than my previous configuration, now recognises windowsXP pro and asks me to specify users. this is all good then.

i am still having error messages IO buffer error on device fd0 logical block 0

not sure what this is about, half a problem solved though.

---

### Post by Drate on 2007-12-17
CRAP!  I wish I had been payin attention to this thread!  When you said extended partitions back there I knew immediately what the problem was!

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/174669]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/174669")

So yeah, it doesn't like extended partitions.  I found that out the hard way myself.  But I have no clue on the I/O error.  Sounds vaguely familiar but I don't know anything about it.

---

### Post by 720iD on 2007-12-17
reading that bug reminded me of another issue. i noticed the partitioner identified my drives as sata but i have ide and ubuntu still labels my devices as sata drives. also the fdo error somebody says is a floppy error but i dont have any floppy drives and i disabled floppy boot from bios but still get fd0 error when i boot a live cd. although putting the operating system on the same drive and in a primary partition cleared up dual boot / grub problem.

---

### Post by froy02 on 2007-12-17
It is probably because of the size of your partition.  Windows XP won't let you format a partition larger than 32 gb. It would install then support fat32 bigger than 32 gb if  the drive is formatted by another utility like maxblast or partition magic.  

It is actually better to use ntfs because it is more efficient in a sense that it uses 4kb for cluster size instead of fat32 which uses 16kb.  This means that when you save a file that's let's say 2 byte size, in ntfs it still uses 4 kb while in fat32 it uses 16kb for storage for that file.

Also it you are editing movies the files can grow to more than 4gb.  That's the max single file size that fat32 can do.  Ntfs does not have that limitation. 
Ntfs is much better than fat16 or fat32 that's why windows adapted it.

---

### Post by 720iD on 2007-12-17
thats useful to know. i tend to use Fat partitions because previously they where more accessible form other opertaing sytems than NTFS.

---

