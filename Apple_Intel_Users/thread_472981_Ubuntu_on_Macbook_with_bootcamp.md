---
title: "Ubuntu on Macbook with bootcamp"
date: 2007-06-13
forum: Apple Intel Users
---

### Post by LieToPurify3 on 2007-06-13
I want to install ubuntu on my macbook using bootcamp.  How much hd space is this going to take up and will it affect my OSX or files?

---

### Post by thully on 2007-06-13
Yes, you can use Boot Camp to install Ubuntu - though if you want Windows as well you need extra steps.  It shouldn't affect your files, but as Boot Camp is beta you should back up the essentials.  You would need 5GB at minimum, but can give Ubuntu more if you want.

To do it, just run through Boot Camp as you would for Windows - except that the "Windows" space is actually for Ubuntu.  When Installing Ubuntu from the CD (you have to boot off the CD first - just insert it when Boot Camp asks for a Windows disc), simply do manual partitioning, delete the Windows partition (which should be /dev/sda3 - DON'T change any other partitions), and create a Linux partition (with mount point /) using all but 1GB or so of the free space.  After that, create a swap partition in the leftover free space and install.  After installing you will choose your operating system just as you would if you installed Windows in Boot Camp.

If you ever want to uninstall Ubuntu, you'll have to go back to the boot CD, delete the Ubuntu root and swap partitions, and create a single partition and start an Ubuntu install to that.  Kill the install before it finishes, reboot to OS X, and use Boot Camp to restore the drive to one partition.  I know that sounds weird, but otherwise Mac OS X will see the swap partition and refuse to restore the disk to one partition.

You may see steps involving gptsync, rEFIt, etc.  Those work, but if you're just doing a dual--boot I've found the Boot Camp solution more stable and easy to use.  If this at all scares you, you may want to try Parallels or VMware to run Ubuntu in a virtual machine.

---

### Post by dopey220 on 2007-06-13
I have a similar question; I have a MacBook with Windows XP installed with boot camp, and I'd like to replace XP with Feisty on my XP partition. Can I do that?

---

### Post by thully on 2007-06-13
Just follow the same install instructions - delete the Windows partition and replace with a root and swap partition.

---

### Post by SectionThree on 2007-06-13
I used this [ page on the wiki]("https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Ubuntu_Feisty_On_Intel_Mac_Mini_Quick-Start_Guide?highlight=%28mac%29%7C%28mini%29") to install Ubuntu on my MacBook and it worked (don't let the "Mac Mini" part of the title throw you off.

Unfortunately, if you have a newer MacBook, you might have issues with your WIFI capabilities (Apple changed the device after Feisty came out). If this is the case, go to [this page]("https://help.ubuntu.com/community/MacBook") of the Wiki.

Two hints to avoid the pitfalls I hit:
1. [Download MadWifi]("http://madwifi-hal-0.9.30.13-current.tar.gz") before you boot up into Ubuntu. Save it in Macintosh HD and you can copy it to your home folder when you boot into Ubuntu. You can install it without an internet connection that way.

2. This may sound simple, but it's crucial: Make sure your Ubuntu disc is IN THE DRIVE! Trust me, it will save you some heartache if you go for my first hint.

---

### Post by ronocdh on 2007-06-14
> **SectionThree said:**
> 
Two hints to avoid the pitfalls I hit:
1. [Download MadWifi]("http://madwifi-hal-0.9.30.13-current.tar.gz") before you boot up into Ubuntu. Save it in Macintosh HD and you can copy it to your home folder when you boot into Ubuntu. You can install it without an internet connection that way.

2. This may sound simple, but it's crucial: Make sure your Ubuntu disc is IN THE DRIVE! Trust me, it will save you some heartache if you go for my first hint.
I like the first tip, but remember that DHCP-enabled ethernet will work out of the box, folks. Don't expect wireless to, but you can always plug in until that's set up! I realize this isn't an option for everyone, though.

I don't really get the second tip. Are you saying because during software installations, Feisty often demands the CD be in the drive? This is a default setting that I find rather foolish, and can be changed by going to the Software Sources in the System>Admin menu and unchecking the Feisty CD option.

---

### Post by SectionThree on 2007-06-14
The second tip made it easier to satisfy MadWifi's dependencies because, for some reason, my DHCP Ethernet connection wasn't working out of the box...

---

