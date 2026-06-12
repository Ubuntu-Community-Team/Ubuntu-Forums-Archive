---
title: "Expert help needed (Triple boot)"
date: 2008-04-07
forum: Apple Intel Users
---

### Post by rokayjon on 2008-04-07
Hello,

I was a windows user for years and migrated to Mac OS about 2 years ago.  I saw a youtube video of Ubuntu and it looks AMAZING!  Now, I HAVE to have it.  

I have a Mac Pro (Intel) and so I definitely want to keep that OS.  I have invested too much in the software to give it up.  Unfortunately, I need Windows XP for work.   So the only option I have is to do a triple boot of Mac OS (Leopard), XP, and Ubuntu.

I am very new to Linux and have been trying to read as much as possible.  I have about 2 TB of Hard Drive space on my mac.  However, the main drive is only 250 GB.

My first question is, if I were to do a triple boot, would all three OS'es have to be on the same HD?

The bigger question that I have is with the actual triple-boot installation.  I have read that I need the following software to make the triple boot work:

rEFIT 
iPartition ($50.00) 

I am really concerned that I won't be able to do the partitioning part without using iPartition.  Is that me being paranoid or is it fairly difficult for a newbie?  Is there a step-by-step guide for dummies?

Can someone please provide me with the latest instructions on how I can triple boot my Mac Pro?  It would be extremely appreciated if details were given regarding the partioning part, as that sounds the most complicated to me.  Setting up the windows part is a breeze (dual boot) as I have done it a few times using Boot Camp.  The difficult part for me is to set up Ubuntu on top of that.  That is the part I need help with.

Best Regards.

---

### Post by mjp216 on 2008-04-07
when u put in the Ubuntu Live CD, there is a program called gpartition which will allow you to partition your hard drive... and if anyone says you need to buy sofware, i can almost guarentee that linux has a free version that is just as good, if not, better

---

### Post by sdennie on 2008-04-07
You may want to take a look at virtual machines if you really want to be able to have 3 OS's on a machine.  Sun has more or less made the VirtualBox website unsavory after buying the company but, it's still a great product and I believe that OSX is a supported host environment.  Essentially, you can run Windows and Linux within a window.  I [unfortunately] write software for Windows and so am running linux, XP and Vista all at the same time as I write this message.  A warning though:  Once you get into virtual machines you will be absolutely hooked...

---

### Post by tubasoldier on 2008-04-07
> **mjp216 said:**
> when u put in the Ubuntu Live CD, there is a program called gpartition which will allow you to partition your hard drive... and if anyone says you need to buy sofware, i can almost guarentee that linux has a free version that is just as good, if not, better

To get Linux to run properly on the mac you have to use rEDIT. However, you are correct about partitions. Gparted is free, iParted is not.

The newer Intel macs have quite a bit of power. Running Linux in a virutalbox is a good idea. Compiz will not be avaliable, but to learn to use linux, its the best bet.
VirtualBox has an OSX version.

---

### Post by cyberdork33 on 2008-04-07
> **tubasoldier said:**
> To get Linux to run properly on the mac you have to use rEDIT. 
I assume you mean rEFIt, and if so, that is False.

If you want a "step-by-step" guide, then you have to be more specific about where you would like to install Ubuntu (a separate hard drive?). Partitioning is not a big deal and you do not need iPartition. Furthermore, you are not limited to one hard drive (although it can be tricky because of the way the Mac works).

---

### Post by rokayjon on 2008-04-07
Thanks for all your responses.

I ran windows within a virtual machine and it was very buggy.  I am looking into doing the triple boot where all the OS'es run one at a time.

Cyberdork33, yes I want to install Ubuntu on the Same HD as the Mac OSx.  But if it is easier to install on a separate internal hard drive, that is just as cool.  Either way works for me.

My goal is to have all three OS'es running on the Mac Pro (internal HD).  

Glad you guys told me about iPartition.  I hate to fork over $50.00 for something I don't really need.

Again, thanks in advance for your help!

---

### Post by cyberdork33 on 2008-04-07
> **rokayjon said:**
> I ran windows within a virtual machine and it was very buggy.  I am looking into doing the triple boot where all the OS'es run one at a time.

Cyberdork33, yes I want to install Ubuntu on the Same HD as the Mac OSx.  But if it is easier to install on a separate internal hard drive, that is just as cool.  Either way works for me.
There are several threads covering this then, and they should all be fine.
[http://ubuntuforums.org/showthread.php?t=594298](http://ubuntuforums.org/showthread.php?t=594298)

There is a section in the Macbook Pro wiki page about getting everything installed, it should work too. You basically just install OSX and Windows via boot camp, then follow the directions. [https://help.ubuntu.com/community/MacBookPro#head-8224be4fd9e91b7d57ecb73af7a8a420f002082d](https://help.ubuntu.com/community/MacBookPro#head-8224be4fd9e91b7d57ecb73af7a8a420f002082d)

---

### Post by mrsteveman1 on 2008-04-07
As far as i know, the apple firmware can boot legacy OS on multiple drives.

If you are going to resize your OS X partition to make room, do it in OS X, because the HFS+ volume will have to be resized. Gparted can do it, but I've seen gparted really screw with the partition tables, leaving them really, REALLY out of sync, and gptsync didn't help, I had to edit them manually to get things back in order.

---

### Post by cyberdork33 on 2008-04-08
> **mrsteveman1 said:**
> As far as i know, the apple firmware can boot legacy OS on multiple drives.Yes, but when you do that, it sees the drive from which you booted as sda instead of it's "real" placement and this requires some changes to files after installing Ubuntu.

---

### Post by rokayjon on 2008-04-15
Thanks,

Here is what I have done so far...

Installed XP Pro and MAC OS X.  I have also installed rEFIt.  When I login, I see both XP and OS X.

The MAC partition is on an internal HD.  The XP is on a second Internal HD.

I want to put Ubuntu on the same HD as the XP (2nd internal drive).

From what I read, I am supposed to use the following command to partition my HD's.

diskutil resizeVolume /dev/disk0s2 40G Linux Linux 30G "MS -DOS FAT32" Windows 30G

But I get a message saying that "linux" isn't a valid OS Type.

Is there another TYPE i should use for linux?

---

### Post by cyberdork33 on 2008-04-15
> **rokayjon said:**
> diskutil resizeVolume /dev/disk0s2 40G Linux Linux 30G "MS -DOS FAT32" Windows 30G


Is there another TYPE i should use for linux?

I think your command needs more work... /dev/disk0 is the first disk, so if you are trying to partition the second disk, you should be modifying something on /dev/disk1

You probably should have made your partitions before installing Windows, as changing it now will likely make windows have a fit. It doesn't matter what partition type you use for Ubuntu, when you boot from the cd, use the "partition editor" application to delete the created partition (leaving free space) then in the installer choose to install to that free space. It will create the needed partitions in that space.

---

