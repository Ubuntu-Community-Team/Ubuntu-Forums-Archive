---
title: "Accidentally deleted Windows. How to reinstall?"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by BordrGuy108 on 2007-12-26
Hey all. I have been interested in trying Ubuntu for a while now so after backing up most (hopefully) of my files yesterday I tried to repartition my hard drive on my laptop and install Ubuntu Gutsy. I have an HP Pavillion zd8000 laptop with 1 gig of ram and a 60 gig hard drive. 

So, unfortunately I am not too experienced with partitioning hard drives so I accidentally told Ubuntu to install over everything, thereby losing my old data (which isn't too big a deal as I backed up most of my stuff). What I am wondering is what do I need to do to reinstall XP so I can dual boot both windows and Ubuntu? Currently Ubuntu is installed and appears to be working fine. I have read some stuff about gparted, but I'm not too sure on what to do. Also seeing as my hard drive is kinda small (60 gigs) what is the best way to split the space between windows and Ubuntu? Here is a link to the guide I was trying to follow to partition my hard drive / install ubuntu: [http://digitalgraphy.wordpress.com/tag/dual-boot-ubuntu-gutsy-and-windows/](http://digitalgraphy.wordpress.com/tag/dual-boot-ubuntu-gutsy-and-windows/). Any help would be greatly appreciated.

---

### Post by LaRoza on 2007-12-26
If you don't have reason to keep the current Ubuntu install, you can start over again, install Windows, then Ubuntu.

If you want to keep the current install, you can install Windows but it can be tricky. 

GParted is a live disk (see the link in my sig) which will allow you to resize, create, delete, and format partitions.

---

### Post by Tadock on 2007-12-26
I had a similar experience when I killed my windows partition heres what I did. First you need to free up how ever much you want for your windows partition this can be done with the Ubuntu installer CD but I am not sure I did it with [Partition magic]("http://www.symantec.com/norton/products/overview.jsp?pcid=sp&pvid=pm80"). But, I am sure theres something free out there that you can use. After you have freed up the space for your windows install pop in your windows CD and install windows on the free space. After windows is installed use [SuperGrub]("http://supergrub.forjamari.linex.org/") to fix your grub so you can pick which OS to boot from. Hope this helps

---

### Post by forestpixie on 2007-12-26
as you've only just done it I'd be inclined to start again - get gparted from [here]("http://gparted-livecd.tuxfamily.org/"), burn it as an iso and boot with it

dlete the partitions you'll find in there - apply changes, you should then have a empty harddrive - make an ntfs partition 15Gb, make an ext3 partition 15Gb, make a 1Gb partition and format for swap and then make another ntfs partition with remaining space

use the first partition to install windows
use second to install ubuntu

you can use the last partition for data - gutsy will be able to make use of it as well as windows

hope that's of some help

---

### Post by Tadock on 2007-12-26
> **LaRoza said:**
> If you don't have reason to keep the current Ubuntu install, you can start over again, install Windows, then Ubuntu.

If you want to keep the current install, you can install Windows but it can be tricky. 

GParted is a live disk (see the link in my sig) which will allow you to resize, create, delete, and format partitions.

If you don't need anything on your Ubuntu forget what I said. Go with what LaRoza said its far easier.

---

### Post by HermanAB on 2007-12-26
Well, dual booting is sooo 20th Century - Install Vmware Server (Free) and install Windoze XP in that.  Then you can run Windows in a window the way god intended it to be...

Cheers,

Herman

---

### Post by Kyran1 on 2007-12-26
To my knowledge, virtual emulators do not have support for 3D due to the use of the emulation drivers for graphics cards. Until this is resolved, those of us that use programs that need 3D support will have to wait. It would be best if you got an external HD and installed windows onto that (assuming your comp has the ability to boot from usb). If your computer is a desktop, invest in another HD and use that for windows. With all the viruses out there for windows, this would be the best option because, I have come across viruses that destroy the mbr of a hard drive and when there is a HD with dual boot, one of them being windows, it can cause for a total reformat of the entire drive (if not causing the need for a low level format).

---

### Post by lasthand on 2007-12-26
What do you need windows for?

---

### Post by wispygalaxy on 2007-12-26
[COLOR="Indigo"]**I posted on here a while back about the same problem you had.  The best advice I can give you is to install Windows first, then Ubuntu.  It was a hassle installing Windows after Ubuntu, so I gave up.    Good luck!  :biggrin:  **[/COLOR]

---

### Post by meierfra on 2007-12-26
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

---

### Post by BordrGuy108 on 2007-12-27
hey thanks for all the responses. I decided to just start over and have installed windows and will be reinstalling ubuntu soon. Unfortunately I have to go out of town for a few days so I'll have to finish this later, but from all the posts I believe I know what to do. Thanks for the help :)

---

