---
title: "Installing MAC OS and Ubuntu on G4 desktop"
date: 2008-12-31
forum: Apple Hardware Users
---

### Post by trungd_t on 2008-12-31
Hi All,

I just acquired a PPC G4 with only Yellow Dog Linux installed. The installed Linux is very old. I would like to install both MAC OS and Ubuntu. I've already installed Ubuntu on my laptop and like it very much. 

My problem is that the G4 boot menu has only Linux, and I don't know how to get the G4 to boot from the CDROM, to start the MAC OS install. I've literally zero experience with Apple hardware/software. On a PC, I can tell the BIOS to boot from CDROM first. Is there something like this on the G4? I've tried entering the hdc at the yaboot prompt, to get it to boot from the CDROM, but that didn't work.

I would really appreciate for any help or pointers in the right direction.

Thank you,
Trung

---

### Post by pxwpxw on 2008-12-31
Hold down the Option/Alt key while restarting, should get the CD icon.
Or the C key.
EDIT:
When installing from the  Ubuntu CD -
At yaboot prompt, TAB for a list of options, take the nosplash one if there is one.

---

### Post by trungd_t on 2008-12-31
I have a lot to learn about Mac. Thank you pxwpxw! That did the trick. It listed three icons: Penguin HD icon, MacOS HD icon (untitled), and the MacOSX CD icon. I selected the CD icon and proceeded with the installation. However, at the select a destination screen, only the HD (8.5 GB - untitled) was shown. How come it didn't list the existing linux partition? I was not given the option to manage the partitions (as in Windows). I want to repartition the entire 40 GB to install a dual boot of both MacOSX and Ubuntu.

I went ahead and selected the 8.5 GB untitled partition for the installation, which resulted in an error. The system rebooted and now the existing linux doesn't even boot and installing MacOSX shows no available partition.

What am I doing wrong and how can I recover the 40GB HD to repartition it properly?

Thanks,
Trung

---

### Post by mkvnmtr on 2008-12-31
My mac install disk with disk utility can't read my linux partitions. When you decide how big you want your mac partition use the disk utility to form the mac partition. Leave the rest as free space. Don't format it. Then when you have installed mac and boot of of the Ubuntu live disk take a look at with the partition editor. It should show the mac partition and the mac boot and the rest as free space. You can then install and choose to install Ubuntu in the largest free space. It should form your boot and swap partitions and you Ubuntu partitions all in the free space. That should be the most uncomplicated way to get both systems on the disk. Many recomend a seperate home partition but for your first dual boot install you might be better to wait until later.

---

### Post by pxwpxw on 2008-12-31
> **mkvnmtr said:**
> My mac install disk with disk utility can't read my linux partitions. When you decide how big you want your mac partition use the disk utility to form the mac partition. Leave the rest as free space. Don't format it. Then when you have installed mac and boot of of the Ubuntu live disk take a look at with the partition editor. It should show the mac partition and the mac boot and the rest as free space. You can then install and choose to install Ubuntu in the largest free space. It should form your boot and swap partitions and you Ubuntu partitions all in the free space. That should be the most uncomplicated way to get both systems on the disk. Many recomend a seperate home partition but for your first dual boot install you might be better to wait until later.

Yes, agreed.
I missed that you need install OSX first, I edited my post, it referred to starting the Ubuntu install CD with the yaboot prompt.

---

### Post by trungd_t on 2009-01-01
Thanks great suggestions guys, but where can I get a disk tool to manage and repartition, before I can install OSX. You mentioned a Mac disk util, but did allow you to remove all of the existing partitions, including linux? And does it allows me to create new partitions for Mac and Ubuntu?

Where can I find this disk utility? Is it included in the Mac installation disks and what is it called?

I'm at a state, where I cannot install MacOSX nor manage partitions, because the Mac installation doesn't recognize any partitions at all. Any suggestions would be greatly appreciated.

Thanks a lot.

Trung

---

### Post by tiresia on 2009-01-01
Before installing anything, you must know following:

The File System for Mac OS X is HFS Plus (or HFS+), the FileSystem for Linux is called Ext2. Usually you use both in the Journaled Version, i.e. "HFS+ Journaled" and Ext3.
MacOSX doesn't recognize Ext2/Ext3, Linux recognizes HFS+ (Journaled or not). This means that Linux can read a HFSPlus Journaled Partition. But if you want that Linux writes on a HFS+ Partition you must disable the Journaling.

This can explane you, why MacOSX does not see any Linux Partition.
.......

You want now make a dualboot. Why do you need to install MacOSX before?
As I said before, Linux can read HFS+ Journaled or not, but can't generate a HFS+ File System. Therefore the easiest solution is:

1. Start the MacOSX Installer CD/DVD (holding down the C-key or pressing the option-key at bootup)

2. In the Main Menu of the Installer-CD you see 'Utilities'. There you find the Apple Disk Utility, you are looking for. Make two partitions. You have 40 GB HD. Let's say that you want to use 15GB for Ubuntu and 25GB for MacOSX (MacOSX thakes more room than Ubuntu). Leave the 15GB unformatted (free space) and format the 25GB for MacOSX as HFS+ Journaled. When it is ready, close the Apple Disk Utility.

3. Install MacOSX. The Install gives you the option to install macOSX only on the 25GB Partition formatted with HFSPlus. When you are ready, restart.

4. After you restarted in MacOSX, download the desktop-Ubuntu-Hardy  (8.04.1) from here and burn it with the Apple Disk Utility at low speed. Again you will find it in the Applications > Utilities.

5. When you are ready, restart again the computer from the Ubuntu Live CD (as always holding down C or pressing the option-key at bootup). At the first prompt hit TAB. You will find different options. Choose linux-nosplash-powerpc. 

6. According to your system, you need to wait a while until you get a desktop. You can try Ubuntu to see how it works, or you can install it. Install it on the 15GB FreeSpace you left before. When you are finished with the Installation, restart the Computer.

7. When you restart, you will get a prompt. It is yaboot, the kernel Bootloader. There you can choose to start MacOSX (pressing the x-key) or Ubuntu (pressing the l-key). You will get a second prompt. Yaboot gives you the option to choose between different kernels. Ignore it for the moment and hit just Enter. You are done!

8. If you get a blak screen after the second prompt don't worry. Restart again, and at the second prompt write```
video=ofonly
```

Let us know, if you have any problems - and read the FAQ for knowing more!

---

### Post by mkvnmtr on 2009-01-01
It sounds like your first problem is finding Disk Utility. It was mine also the first time I looked for it. When you boot the mac disk you will see at the top of the screen  menus. Look for Disk utility there. When you launch it you should be able to see and understand how to use it. Don't worry. If you screw it up the first time you can do it again. Or like me again and again and again. You can't break equipment installing software unless you use a hammer.

---

