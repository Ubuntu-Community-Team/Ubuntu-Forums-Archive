---
title: "Partitioning problems"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by bash the bishop on 2006-05-01
Hi all,
I'm new to the ubuntu scene, so this may have already been covered. I'm trying to install Dapper as a dual boot, but the install will not let me create the partition with my XP system. 
No matter what size I set the partition to, it will not proceed. It keeps telling me to manually set the partition. 
Any help?????:)

---

### Post by Qrk on 2006-05-01
Here is a great guide with screenshots.

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

Ubuntu resizes the ntfs partition and makes they Linux partitions separatly (though they aren't written to the disk till the end.) Make sure that you are resizing ntfs before you attempt to make an ext3 partition for Ubuntu.

Here is another good guide.

[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

---

### Post by teasum on 2006-05-01
I had some trouble with the partition editor in the Dapper Live CD installer as well.  Assuming you're trying to install from the Live CD, you could use the installed partition editor (GParted) available on the Live CD to change your partitions, and then run the Espresso installer.  Gparted is available from one of the application menus (I can't remember exactly which one right now, and I'm at work on a Windows box right now).  This is the workaround solution I used when installing Dapper (Beta 1) on my laptop.  

GParted should enable you to resize the XP partition and create one for your Ubuntu installation.  Then, when running the installer, you would simply select the new Ubuntu partition you created.  This way, you would not need to use the partition editor that comes with the installer.

I hope this is all clear.  Let us know how it works... good luck!

---

