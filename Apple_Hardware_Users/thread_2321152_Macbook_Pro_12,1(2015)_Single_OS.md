---
title: "Macbook Pro 12,1(2015) Single OS"
date: 2016-04-20
forum: Apple Hardware Users
---

### Post by Tristan_shute on 2016-04-20
So I have finally gotten fed-up with OSX and the apple environment, and have looked into install Linux on my Macbook Pro Retina 2015. I used to be really into linux and install tens of distro's on my old laptop, but it used MBR instead of EFI. I have read up on the GUID partitioning system and UEFI/EFI. What I would like to do is completely wipe OSX off my laptop and install linux, but keep the recovery partition so that I can use 'Command R' at boot up and access time machine and reinstallation of OSX in case I ever need to use proprietary software for my university. As far as I know, all that needs to be kept is the apple recovery partition. Unfortunately, I have not been able to find much information on whether or not I should delete the EFI OS X partition. And if I cannot, will I be able to share that partition with Ubuntu? On top of that, I would also like to know if GRUB2 will prevent me from accessing 'Command R' on boot up.
Unfortunately, my google search has come up blank with these questions.
Excited to start using Linux again, I just need to know more about how this all works with EFI now.:D

---

### Post by sherman-dougherty on 2016-04-25
I'm fairly new to Ubuntu on Mac but I can tell you this much from a recent install on an iMac (16,1 - I think, it's newer - 2015 mode, shipped with 10.11) - I still have my recovery partition for OS X and it is accessible during boot. But... I have kept a fully functional install of Mac OS 10.11 - so that would a difference b/w our approaches. I still think you could achieve the same result if you're careful about the partitioning performed before and again during the Ubuntu install. Use reFind not reFit - and read up on SIP disablement it's required for 10.11 only (until 10.11 is superseded then it will likely still be required). If you're running an OS earlier than 10.11 then there's no SIP to disable. 

Do not delete the OS X EFI partition! I strongly recommend running a Live USB stick of Ubuntu b/f you install - check that everything works OK. Then after a few days do your install (you can make the USB image persistent to save work done in the meantime).

When actually doing the install choose "something else" for the install type (to avoid writing over your recovery partition) and make sure you cut out a swap area if you think you'll need it (>=installed RAM) and set the root to be @ your empty partition where you're installing Ubuntu (created in OS X as a GUID partition type). The directions available for older MBP installs should be sufficient to get you going. The ReFind tutorial that helped me much was from rodsbooks.com (?) something like that. If on 10.11 read the SIP section in a black box on the right hand side of the page b/f you do anything. The ReFind setup was the most critical of the install steps ime - for all three Macs I've installed Ubuntu onto in the last month. It should help you with your EFI concerns.

Your MBP may run pretty hot, make sure to install macfanctld and associated packages lmsensors, etc... Use the instructions on the Ubuntu forums and you'll get at least some fan speed control, I'm sure you could write a script to manage fan control, or just set the speed to something like 2000 - 2500 rpm while running. There's lots of info about temp issues with MBP - don't let that issue prevent you from doing the install. You can always rollback. That said, the packages available to help control temp are decent enough. PSensors will help with a GUI for monitoring, logging & real time graphing of temps.

"[COLOR=#000000]will I be able to share that partition with Ubuntu" - I'm not sure I understand why you'd want access to recovery partition from Ubuntu. Someone else should give you advice on this if it's a concern to you. I can "see" my main OS X partition as a drive in Ubuntu but not the recovery partition. Though I see it in gparted Ubuntu's disk partition utility, and I know it's accessible on boot. So... maybe I did / didn't do something you should do to be able to access that recovery partition from Ubuntu if you really need to do so. Access to this partition while running a Live USB instance of Ubuntu may not guarantee the same will be true after install.[/COLOR]

Hope that helps. Cheers and welcome back to Linux, Ubuntu is a but too GUI for me, but it's helpful for me while I learn to do everything from the CLI and with scripts.

Recently I: installed Ubuntu 14.04 on three Macs (iMac 2015, macmini 2012 and a MBP early 2011) and 14.04 server on a (now) headless PC. I'd never worked with Linux b/f a month ago. I love it! I also installed Oracle 11g express onto the server to work with to refresh my dba skills.

---

### Post by Robert_Jackson on 2016-05-08
I have just tried three single OS scenerios tonight and I was able to get all three to work on my macbook prot 11,5
Windows 8.1 Pro only.
El Capitan only.
Ubuntu 14.04 only.
You dont need to keep the recovery partition....if you delete the recovery partition and do a Command R....it will act just like the internet recovery and pull the recovery into memory striaght from the apple.com servers.
Having said that...I made a USB stick recovery because my internet is slow out at the farm.

I currently have an install with windows 8.1 and with Ubuntu 14.04 with grub.
I just tried the command R and it works.

---

### Post by Robert_Jackson on 2016-05-08
if you really screw things up you can boot from internet recovery or your USB.
go to terminal
  fdisk -i /dev/disk0                  this restores the master boot record
  fdisk -a boothfs /dev/disk0      this makes a boot partition and the rest of the drive an hfs partition
exit terminal
start diskutil
 name the partition "Macintosh HD" and erase and format it to OS X Extended
exit diskutil
 start the reinstall of MAC OS on that partition

---

### Post by Robert_Jackson on 2016-05-08
I had put bootcamp on my machine a while back. 
I had to boot from the live Ubuntu thumb usb and run gdisk to get rid of the hybrid master boot record.

---

