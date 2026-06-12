---
title: "GNU Grub version 1.98 not responding"
date: 2011-08-02
forum: Australia Team
---

### Post by youngatheart1946 on 2011-08-02
G'day fellow ubuntu users,following you will find a copy of a posting I placed in ubuntugeek forum and as yet have not received a reply. I am hoping by posting my problem here in Australia that I will get a faster response.Cheers guys...Bryan
Title: **GNU Grub version 1.98 not responding**
				Post by: **youngatheart1946** on **July 28, 2011, 06:42:01 PM** 			 				Hi there folks, I am a relative noob to ubuntu so i ask you to be patient with me.
A  short while ago I decided to give ubuntu 10.04 a spin as a dual boot  alongside Windows xp home edition using WUBI. All went really good, so  good infact that I purchased and had installed an extra 500gb   internal hdd so that ubuntu had its "own space". Once again all went  well so I got quite adventurous and installed Mint alongside ubuntu  10.04 but found that Mint didn't "see" my systems cd/dvd player. Been  very pleased with ubuntu I decided to "get rid of" Mint. As I couldn't  find how to uninstall  Mint  I logged back into windows and  via a partition manager deleted Mint from alongside ubuntu. That's when  my problem manifested itself. Upon restarting my pc I could no longer  get into GNU Grub selection page, all I got, every time I tried, was  notification of  some sort of "grub error". The only way I could  get the ubuntu hdd to work was to disconnect the windows hdd and boot  directly into ubuntu 10.04. After a lot of frustration I decided to take  my pc to a computer shop to see what, if anything, they could do for  me. I was informed that something had corrupted the MBR and needed to do  a "clean install" of Windows XP costing me $50 cold hard cash. Upon  getting home and reconnecting everything I hit the "boot button" only to  be greeted with a "very clean" Windows XP and still no way to boot into  ubuntu without disconnecting the windows hdd. Whilst in ubuntu I had a  rather large update and had to subsequently re-boot my system. Once  re-booted I was presented with the GNU Grub operating system selection  window......ahh at last things were looking up....but alas I could still  not select another OS, infact I could get no response from the keyboard  or the mouse and the system automatically loaded my ubuntu hdd. I am  very impressed with ubuntu 10.04 but still need windows xp for some of  my "special programs" that wont even work through wine. Please, if there  is anyone out there who can help me either email me direct or respond  in this forum.

---

### Post by Jared Norris on 2011-08-02
Gday and welcome to the Australian forums.

I'm not a grub expert but any time I've had a problem the following 2 help pages have got me out of trouble. 

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

and

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

I'd have a look over them and see if they help at all. Sorry I can't be more specific but I thought I'd at least be able to point you in the right general direction.

---

### Post by oldfred on 2011-08-02
If Mint was your last install did you let it install its copy of grub's boot loader to the MBR? If so when you deleted Mint you delete the files the grub bootloader is looking for.

You should just need to reinstall grub2's boot loader to the MBR. If you have two drives you should install it to the same drive as Ubuntu is installed and set BIOS to boot that drive. 

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by kyphi on 2011-08-06
While the instructions given by oldfred are right on the button, they might be a bit bewildering for someone new to Linux.

Here is a (possibly) simpler method for achieving the same result:

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

---

