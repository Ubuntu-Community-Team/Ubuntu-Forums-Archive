---
title: "Ubuntu XP Dual Boot on Dell M70"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by beno4433 on 2007-10-13
I have a Dell Precision M70 laptop and have been wanting to configure a dual boot with Ubuntu and my current XP Pro Operating System for some time now.  However, given that I'm new to Linux, I've been hesitant to install Ubuntu alongside XP Pro, knowing the problems I've read about changing the configuration of factory installed Dell systems. Especially creating a new partition for Ubuntu while still keeping the Windows NTFS partition with limited BIOS functionality.

I did, however, successfully perform a dual boot (Ubuntu/XP Home) installation on my old Dell Deminsion 4550 without any problems with hardware configuration.  And I'm excited about learning how to use a new OS like Ubuntu.  But I use this computer strictly for testing purposes.  

The Dell M70 is my main system and, again, I'm wary that installing Ubuntu in a dual boot format will fail and possibly cause problems with my XP Pro system.  I've been able to boot Ubuntu using the live cd format and there seems to be no hardware configuration problems.  So the first question I'd like to ask the community is the following:

1) If the Ubuntu live CD works on my Dell M70, does that mean I will not encounter any hardware conflicts when installing Ubuntu alongside my XP Pro System.

Here is all the information I know to give about my system so that someone may be able to let me know if I'll encounter problems when permanently installing Ubuntu while still keeping my XP Pro setup.

Computer Type - ACPI Uniprocessor PC (Mobile)
CPU - Intel Pentium M 780 (2.26 GHz)
Chipset - Mobile Intel Alviso i915PM
BIOS - Phoenix(with limited configuration functionality) Version A04
Video Adaptor - NVIDIA Quadro FX Go 1400 (256 MB) with 3D accelerator
Audio Adaptor - Intel 82801FBM ICH6-M AC'97 Audio Controller
IDE Controller - Intel 82801FBM Ultra ATA Storage Controllers
Hard Drive - 100 GB 7200 RPM Ultra ATA with 63 GB free space
Optical Drive - NEC DVD+- ND-6550A
Ethernet Adaptor - Broadcom NetXtreme 57xx Gigabit Controller
Wireless Adaptor - Intel PRO/Wirelesss 2200BG 

I hope I provided enough information for someone with more Ubuntu experience to let me know if I'll encounter any hardware configuration problems if I try to install Ubuntu into a dual boot configuration with XP Pro.

Oh - I also use Acronis True Image Home 10 to create backup images of my hard drive.  These images are placed on two external hard drives.  If for some reason, the Ubuntu installation should fail and corrupt my XP Pro setup, I'm hoping to be able to restore my hard drive using one of the image snapshots.  I am concerned that I may encounter problems restoring my image once I create a new partition for the Ubuntu OS.

Lastly, please forgive me if I've been too verbose or not used the posting correctly.  I've purchased several Ubuntu books and  have been studying how to install and use OS.  Since I'm new, I still feel I don't know the right questions to ask.  I just hope there's someone out there who has the knowledge and experience to answer my questions.  If my questions are too general, then let me know and I'll provide more details.

Thanks

---

### Post by obscur156 on 2007-10-13
Hi,welcome to ubuntu forum.

I am still a noob,but when i started using ubuntu i have used a simple tutorial to setup my dualboot  XP/UBUNTU FEISTY FAWN.

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")

First make a back of your valuable data.
After you can start the install of ubuntu.

It worked straight forward for me.
Now i have a triple boot XP/FEISTY/GUTSY.

Best regards,good luck budy.

---

### Post by beno4433 on 2007-10-13
Thanks for the recommendations and suggestions.  One of my hesitations has to do with my NVIDIA Quadro FX Go1400 video adaptor.  From reading some of the posts on the forum, there are some drivers that have to be installed.  I'm ashamed to admit that I'm not very good at installing or updating drivers.  But I guess the only way to learn is to try.

I'll have to do some more research before jumping in and installing Ubuntu.

Thanks again for the response.

---

### Post by obscur156 on 2007-10-13
Maybe you can try ENVY to install driver for your video card.

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

Best regards ,good luck budy:)

---

### Post by Blazeix on 2007-10-16
Hi. You might consider.waiting two days before installing Ubuntu, since this Thursday a new version of Ubuntu (Gutsy Gibbon - 7.10) is being released. It makes it really easy to install the binary Nvidia drivers (It has a 'Restricted Driver Manager' that will most of the legwork for you).

I'm currently using the prerelease of Gutsy 7.10 on my Dell Precision M70. Since it is so close to the release date, the prerelease is very similar to the release version now. My Dell M70 has a slightly different set up from yours, but the crucial components are the same. 

I have a Nvidia go 1400, and it works perfectly with the driver that comes by default (the 'nv' driver) and the nvidia driver from the restricted driver manager. I have the same BCM57xx Ethernet and AC'97 Audio controllers, and both of them work out of the box with zero configuration. You have an Intel wireless adapter; their driver is open source, so that should not require any driver installation/configuration either.

Hope this helps

---

### Post by beno4433 on 2007-10-17
Blazeix

Thanks for the comments.  I am waiting for the 18th to install the new Ubuntu version.  It's good to hear from someone with the same system as mine.

I have an old Dell Dimension 4450 which I will install 7.10 on first.  Since I'M so new to Ubuntu, I want to try the installation on this machine first because I only use it for testing purposes.

I have one question.  Did you perform a dual boot installation on your Dell M70, keeping Windows, or did you just install Ubuntu?  I'm apprehensive about installing Ubuntu on my M70 because of the process of shrinking my XP Pro installtion and creating a new partition for Ubuntu.  I have Norton Partition Magic and never could get the program to create a new partition on my M70.  I've heard stories of people with Dell computers not being able to create new partitions on their machines.  Did you ever encounter the same problem?

---

### Post by Blazeix on 2007-10-17
I dual boot Windows XP and Ubuntu. I didn't have any problems setting it up, although I did read a lot about partitioning before I did it. Its pretty easy. First thing I did was I defragged my windows partition, in an effort to consolidate all the files.For the actual partitioning, I didn't use Partition Magic. The ubuntu install disk can shring ntfs/fat32/ext3/etc partitions for you. The key option is to choose the 'Manual' option when you are partitioning, and this will launch a GPartEd interface where you can shrink existing partitions, delete partitions, create new ones, etc. I've attached a screenshot of the interface with my current partitioning scheme. 
[list]
[*]The first partition is my windows partition, which I wanted to access from linux in the directory /media/windows. 
[*]The second partition is where linux is installed (note that the mountpoint is '/' which is required for installation. I chose the ext3 system format
[*]The third partition is my swap partition
[*]The fourth partition is optional, its where I keep my documents. It is fat32, so I can easily access them under Linux and Windows. I put it under /media/documents, and I have a link to it from my home directory.
[/list]
It becomes more complicated if you want to have more than 4 partitions, because then you have to mess with logical partitions. I haven't really messed with this, I just know it exists.

---

### Post by beno4433 on 2007-10-18
Blazeix

I downloaded two copies of version 7:10 this morning.  One copy was made using bit torrent and the other using Dapper Drake.

I've been able to successfully boot into the liveCD session on both my Dell Dimension 4550 and M70.  I have one problem though.  I can only use the liveCD when not docked into my Dell D Port Replicator.  When using the docking station, the cd seems to boot fine and I hear the new sound, but then it stops and all I can see is what looks like a screensaver with no mouse access.  The computer locks up and I have to manually shut it down to reboot.

When I undock the M70,, everything works fine.  I'm using the liveCD now on the M70

So my question is, do you have a docking station for you M70?  And if so, how did you get it to work with Gutsy Gibbon?

I'm going to try and install 7.10 on the Dell Dimension.  From there, I'll have to wait until I have the confidence and knowledge to install it along side XP Pro on the M70.

---

### Post by Blazeix on 2007-10-18
Hi, I do have access to a dock. I believe it is the same one that you are using (D/Port Advanced Port Replicator). The external keyboard, usb mouse, network, and monitor all seem to work fine. The only gotcha is that I have to press Fn+F8 (the button with the "CRT/LCD" sticker on it) to tell my laptop to use the external monitor after I attach the laptop to the dock.  If I don't press this, I just get a black screen with no mouse access.

---

### Post by beno4433 on 2007-10-18
Thanks for the tip.  I don't know why I didn't think about that.

---

### Post by beno4433 on 2007-10-20
Blaziex - 

I've tried booting the 7.10 liveCd on my Dell M70 several times with the machine docked and I've yet to get it to work.  I always end up getting a weird blue graphic.  And when I use the fn +F8 option, my monitor give an error saying it cannot work with the native resolution of1680 x 1050.

Do you know of any boot options that may resolve this?

---

