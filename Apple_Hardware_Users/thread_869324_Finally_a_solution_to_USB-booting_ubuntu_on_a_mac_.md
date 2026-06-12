---
title: "Finally a solution to USB-booting ubuntu on a mac ;)"
date: 2008-07-24
forum: Apple Hardware Users
---

### Post by Nosferax on 2008-07-24
Hey guys and gals, I've been doing some research to boot a linux distro by USB, and I thought it would be nice to share what I found out with you all. I've done it using a mac mini (Core 2 Duo, 1.8 Ghz type) and tested both Ubuntu and Debian successfully.

So, how is it achieved ? By booting Linux from EFI instead of BIOS.

Using grub2-efi and a kernel with EFI support, I was able to boot a Ubuntu distribution entirely from USB, nothing else needed. The main back draw : the agp isn't working yet, so no hardware acceleration (I didn't mind about this, depends on what you need to do). From what I've read, I'm not sure there are graphic drivers that work under EFI-booted linux. ANYWAYS, I haven't toyed much with that, I leave it to someone who needs the hardware accel :lol:

What I did was partition a USB-key with 2 principal partitions, one HFS+ partition (couple MBs) that would contain the grub2-efi and one partition ext2 containing Linux. The grub2-efi partition needs to be blessed using OSX so it can be seen without rEFIt. It is imperative you use a kernel 2.6.25 or higher, because the older kernels don't seem to work too well with efi boot.

Basically you can just follow this tutorial [here]("http://grub.enbug.org/TestingOnMacbook") and instead of using rEFIt (unless you don't have access to an OSX installation, in which case you should perhaps try using rEFIt), do the blessing part as explained [here]("http://grub.enbug.org/TestingOnEFI?action=recall&rev=15").

This method really doesn't need anything that comes from the hard drive, I actually opened the mac mini and removed the hard drive to be sure that it still works.

---

### Post by kosumi68 on 2008-07-24
Great news! It is good to hear the EFI grub tools are finally becoming useful. Worth trying on the other laptop models. You don't happen to have an image available for download, do you? It would be great to see how many models could immediately benefit from this.

---

### Post by cyberdork33 on 2008-07-25
This is very good to know, unfortunately, the Mac Minis are really the only Macs that boot from EFI very well. (PS I think there is a patch or something that should allow for 3D acceleration on the Mac Mini, but it is the only one). I thought maybe you found a bless tool outside of OSX, but I guess I am wrong... Blessing still requires OS X (at least booting the DVD).

EDIT: I added a note to the FAQ and linked to this thread.

---

### Post by pxwpxw on 2008-12-13
> **kosumi68 said:**
> Great news! It is good to hear the EFI grub tools are finally becoming useful. Worth trying on the other laptop models. You don't happen to have an image available for download, do you? It would be great to see how many models could immediately benefit from this.

I put a pre-built grub.efi test package here with that aim.
(from svn 1913 with all grub modules)

grub2 EFI boot loader internal/external booting
[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

---

### Post by freesparks on 2010-04-16
Hello Guys,

   I have successfully installed Ubuntu 9.10 Server on my Lenovo that I use for work on an external USB 2.0 SATA harddrive.  With that being said,  I own 2 Macs, a Mac Mini, and a MacBook Pro Snow Leopard version 10.6.3.  I read most of your tutorial and am very impressed and I also read that only Mac Mini is able to take advantage of this.  I would like to run Ubuntu 9.10 from an external USB 2.0 harddrive preferrably utilizing my MacBook Pro to run Blender-a 3D animation software.  I am new to Linux so please bare with me.  I have ordered 3 books and am passionate about programming and 3D animation.  I am aspiring to learn Python, C++, and Java, and would love to safely install this on my Mac Book Pro externally.  The reason I have not installed Ubuntu on the internal Solid State Drive is because I am limited to space (128GB),  And I've heard that Ubuntu runs Blender extremely well.  Any help on the pitfalls, challenges, and shortcomings that I may encounter before doing this would be greatly appreciated.  I wish i could buy another MacBook Pro to test this solely because most of the time, one learns when things go wrong, ie. erasing entire partitition that the OS is installed on.  Not that I have done this YET, :) But I would like to avoid this because I am in the middle of some big projects, so i was very impressed when I read that this method did not affect Mac OS Snow Leopard.

Best Regards,

freesparks

---

### Post by HotForLinux on 2012-04-15
Years have passed an I easily installed rEFIt in a MacBookPro 3,1. And works well, allowing me to boot Linux, Mac or a system in a CD.
When I choose to boot Ubuntu-Linux, Grub2 starts presenting its menu with all the systems installed, but only works the Ubuntu options and don't know how to boot  a system in an USB flash drive.

I explained this in this thread:

[http://ubuntuforums.org/showthread.php?t=1957838&page=2](http://ubuntuforums.org/showthread.php?t=1957838&page=2)

Can anyone help?

---

