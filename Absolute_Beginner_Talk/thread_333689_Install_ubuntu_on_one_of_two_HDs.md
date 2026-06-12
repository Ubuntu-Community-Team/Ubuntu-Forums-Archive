---
title: "Install ubuntu on one of two HDs"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Naci Sey on 2007-01-07
I've received a live CD from ubuntu - v6.06 - and would like to install it on one of two hard drives on my PC. 

Drive C has WinXP installed; it's the drive which contains all the program files and boots the system. Drive D is 20 GB, still has Millennium on it, and I've been using it strictly for my files. 

D is the drive on which I'd like to install ubuntu.

First, will the install process automatically proceed to install on the main drive, C, or will it give me the option of installing it on D?

Second, assuming this can be done, will the programs on the WinXP drive be able to access files on the ubuntu drive? E.g., if I want to use PaintShop Pro and access one of the .psp files on ubuntu, can I do it? (Or am I muddling things by assuming that .psp files can be managed by ubuntu?)

---

### Post by ieee488 on 2007-01-07
Do you actually have two physically distinct hard drives or is it one hard drive that has C:\ and D:\ ?

---

### Post by Duck2006 on 2007-01-07
Run the live CD look for a Terminal and open it then run

sudo fdisk -l

and post the output hear

---

### Post by Naci Sey on 2007-01-07
> **ieee488 said:**
> Do you actually have two physically distinct hard drives or is it one hard drive that has C:\ and D:\ ?

Yes, two distinct hard drives, not one that is partitioned into two.

---

### Post by ieee488 on 2007-01-07
My experience is with a PC with 2 PATA hard drives.
1st drive has Windows 2000
2nd drive had data and was formatted as NTFS

First thing they suggest you do is defrag D:\

Ubuntu will most likely suggest installing on D:\ ; or at least it did with me.
It will suggest resizing the partition with ME which is probably FAT32 smaller so it can create a partition for Ubuntu.

Windows XP and Ubuntu can both read and write to FAT32.

---

### Post by cuonght on 2007-01-07
I also want to install ubuntu into my hardisk driver D:\. I have just downloaded Ubuntu isoimage from the website. I tried to install this OS, when I runned it in window xp, it appeared error " the specific file cannot be found". When I tried to install it from Bios, it could not recognize the cd disk as a boot then it jumped to window xp again. Could someone help me to solve this problem?

thanks

---

### Post by ieee488 on 2007-01-07
Did you burn a CD with that ISO image?

You need to check in your BIOS that the PC is set to boot first from the CD then the hard drive.

---

### Post by cuonght on 2007-01-07
I burned isoimage into CD by two ways. First I made it as a data, second, I burned all the file after unzipping the isoimage. I also changed the CD room as the primary driver but it didn't work.

---

### Post by Duck2006 on 2007-01-08
You have to burn it as a ISO not as a data disk

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Naci Sey on 2007-01-08
> **ieee488 said:**
> My experience is with a PC with 2 PATA hard drives.
1st drive has Windows 2000
2nd drive had data and was formatted as NTFS

First thing they suggest you do is defrag D:\

Ubuntu will most likely suggest installing on D:\ ; or at least it did with me.
It will suggest resizing the partition with ME which is probably FAT32 smaller so it can create a partition for Ubuntu.

Windows XP and Ubuntu can both read and write to FAT32.

Thank you for the advice. I only have the 'My Documents' folder on D and so have moved it to C. Now D is completely empty. 

A few more questions before I take a huge gulp and run the install... 

After installation, 

a) will my computer continue to boot onto C, the WinXP drive? 
b) If yes, will it continue to list D under 'My Computer' and will I be able to access D simply by clicking on that icon in 'My Computer'? 
c) If no to 'a' will my computer give me the option of booting into C or D?

Finally, am I completely clueless, as evidenced by my questions? :confused:

---

### Post by ieee488 on 2007-01-08
> **Naci Sey said:**
> Thank you for the advice. I only have the 'My Documents' folder on D and so have moved it to C. Now D is completely empty. 

A few more questions before I take a huge gulp and run the install... 

After installation, 

a) will my computer continue to boot onto C, the WinXP drive? 
b) If yes, will it continue to list D under 'My Computer' and will I be able to access D simply by clicking on that icon in 'My Computer'? 
c) If no to 'a' will my computer give me the option of booting into C or D?

Finally, am I completely clueless, as evidenced by my questions? :confused:


a.) Ubuntu will add a menu for you to choose which OS to boot into. By default the Ubuntu choice is highlighted but it is very easy to make Windows XP the default.

b.) I don't know about XP but Windows 2000 cannot see the part of your 2nd drive that has Ubuntu installed. To be able to see all of your 2nd drive you will need to download and install [http://www.fs-driver.org/](http://www.fs-driver.org/)

Do you know if D:\ is currently NTFS or FAT32?

---

### Post by Naci Sey on 2007-01-08
Well, I gulped and installed ubuntu on my 2nd hard disk, my D drive (which was - still is? - FAT32). So if I install the IFS software on C, which is running WinXP, that will give me access to my files on the Linux D drive? - cuz right now, I have to restart each time I want access to one drive or the other.

---

### Post by ieee488 on 2007-01-08
Yes, installing that software should let you see the files on your 2nd hard drive when you are running XP.

If you boot into Ubuntu, you should be able to see the files on your 1st hard drive aka C:\.
If you don't, search for posts on this message board about mounting hard drives. 

I see all my Windows 2000 files on my C:\ when I am running Ubuntu. It should be the same for you.

---

### Post by Naci Sey on 2007-01-08
OK, I installed IFS and WinXP is now picking up my D drive too. Yipee! But ubuntu on D is unable to 'mount' C - don't know what mount means.

This is the error message I get when I click on the icon for the C drive:

[COLOR="DarkRed"]Unable to mount the selected volume:

error: device /dev/hda1 is not removable
error: could not execute pmount[/COLOR]

Any ideas how to fix this?

---

### Post by confused57 on 2007-01-08
This should give you some idea of what mounting is & how to mount partitions:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by Naci Sey on 2007-01-08
> **confused57 said:**
> This should give you some idea of what mounting is & how to mount partitions:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

Sorry. That's way above my skill level at this point.

---

### Post by confused57 on 2007-01-08
It's really not that hard, boot up Ubuntu, open a terminal(Applications---Accessories---Terminal), enter(best to copy&paste):
```
sudo mkdir /media/windows
```
press enter, enter your password, then:
```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

Then close your terminal by typing "exit"...click on System---Administration---Devices, then find your Windows partition, it should be mounted /media/windows...click on browse.

When you're through, open a terminal, & unmount:
```
sudo umount /media/windows
```

This will mount your Windows for your current session, until you unmount it...if you want to mount it permanently, you'll need to edit your /etc/fstab, as described here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

To determine if you Windows partition is hda1, open a terminal, copy & paste:
```
sudo fdisk -l
```
The -l is a small "L".
This will show your partition tables for both hard drives.

You can copy files from Windows to Ubuntu, but don't try to copy anything from Ubuntu to Windows, assuming your Windows partition is ntfs...if it's FAT32, you'll need a different entry to mount your Windows partition...check back if that is the case.

---

### Post by ieee488 on 2007-01-09
When I installed Ubuntu 6.06, I don't recall having to edit /etc/fstab
I had to do that for Ubuntu 5.10 though

Before doing the heavy lifting of editing /etc/fstab,
you might to go to 
System --> Administration --> Devices
and see if the button to Enable your C:\ which is probably /dev/hda1 is available

---

### Post by Naci Sey on 2007-01-09
I don't see a 'Devices' option under Administration, but Device Manager. Under that, though, there are no enable options. 

There is an enable option for C (the WinXP disk) here though:

[INDENT]System - Administration - Disks - Partitions.[/INDENT]

Under the Properties tab, D (ubuntu) is identified as dev/hdc and C is dev/hda. When I click Partitions, a single partition is listed for C (dev/hda1) and there's a green Enable button. Is it OK to click that?

---

### Post by confused57 on 2007-01-09
> **Naci Sey said:**
> I don't see a 'Devices' option under Administration, but Device Manager. Under that, though, there are no enable options. 

There is an enable option for C (the WinXP disk) here though:

[INDENT]System - Administration - Disks - Partitions.[/INDENT]

Under the Properties tab, D (ubuntu) is identified as dev/hdc and C is dev/hda. When I click Partitions, a single partition is listed for C (dev/hda1) and there's a green Enable button. Is it OK to click that?

Yes, but first change the mountpoint to **/mnt**(type it in the mountpoint space), then click the "Enable" button, then click the "Browse" button.

---

### Post by ieee488 on 2007-01-09
Yes, click that green Enable button.

---

### Post by Naci Sey on 2007-01-09
It worked! Thank you!

---

### Post by confused57 on 2007-01-09
> **Naci Sey said:**
> It worked! Thank you!
Great, thanks for letting us know...could you tell us what you did to get it working?...that'll help other new Ubuntu users reading this thread with a solution for mounting Window's partitions.

---

### Post by Naci Sey on 2007-01-10
> **confused57 said:**
> Great, thanks for letting us know...could you tell us what you did to get it working?...that'll help other new Ubuntu users reading this thread with a solution for mounting Window's partitions.

I went to

    System - Administration - Disks - Partitions.

Then selected the volume for C, clicked Partition (there was only one), entered '/mnt' in the mountpoint field and then clicked Enable. 

Now I've got to find out how to get all the files on Outlook to Thunderbird on ubuntu. Don't imagine that's so easy!

---

