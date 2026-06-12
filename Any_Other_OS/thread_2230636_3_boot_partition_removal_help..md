---
title: "3 boot partition removal help."
date: 2014-06-20
forum: Any Other OS
---

### Post by Otacon.hugs on 2014-06-20
Hi all!
So to be short, I recently installed Kali Linux on my pc as I was experimenting with it for some understanding of the environment it provides.
But as I now have no use for it I wanted to be sure about the removal. Yes I know it is not Ubunutu, but one thing that I was confused by was this:
I have 4 drives
The first is an ssd with Windows 7, the third has Ubuntu, and the fourth has kali.
grub 2.02~beta9 (i think that was it) was installed and the boot order was for my ssd to be booted firts meaning grub must have been there. 
but as I was installing kali, it asked if i wanted it to be triple booted along side other OS's and I accpeted for it to then write the boot record to sda (my ssd).
As a person with minimal knowledge with linux removal i wanted to ask about how i can format the 4th drive, return the grub 2.02 (now it has a kali 1.99 grub version) and return to a dual boot
any contribution im greatfull for so please let me know of what I can do to remove Kali and keep windows and Ubunutu and my info all intact and my 4th hdd back to an ntfs file system :)
Specs:
i7 4770k
gtx760
z87 killler fatality Mboard by asrock
thanks in advance.
~Daz

---

### Post by sudodus on 2014-06-20
0. Start with a ***backup*** of everything important, because things could go wrong.


1. I suggest that you boot into the installed Ubuntu and then ***re-install the bootloader*** to point to Ubuntu. ***Then run update-grub***, which will identify the other bootable systems.

Check that things work. You will probably still have a boot entry for Kali.

See this link

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System)

Run

```
sudo update-grub
```


2. Boot from an Ubuntu install disk and use ***gparted*** to remove Kali by formatting the partition with Kali. Double-check so that you format the correct partition.


3. Boot into the installed Ubuntu again and run

```
sudo update-grub
```

again. This time there should be no boot entry for Kali.

---

### Post by Bucky Ball on 2014-06-20
*Thread moved to **Other OS/Distro Support***

Personally, I'd boot from a Live disk/USB, launch Gparted, delete the Kali partition and install and run Boot Repair to reinstall grub and get it all back together again.

[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

---

### Post by oldfred on 2014-06-20
Combination of above suggestions.

I prefer to have the boot loader on the same drive as the install. And set BIOS to boot Ubuntu drive which has the Ubuntu grub. But then if any issue the other drive(s) can boot the systems installed on them. 

Or install Windows boot loader to sda, install Ubuntu boot loader to sdc and set BIOS to boot sdc. Then you can totally erase Kali.

You can use Boot-Repair, but do not run auto fix. That just installs grub to every MBR. You go into advanced and choose system like Windows and drive like sda. Then choose Ubuntu and drive like sdc.

Ubuntu/grub also remembers where to reinstall on major updates. So if originally installed to sda, on a major update it may reinstall to sda, but you have BIOS set for sdc and older grub in sdc which may then fail. You need to make sure grub reinstalls to sdc.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

