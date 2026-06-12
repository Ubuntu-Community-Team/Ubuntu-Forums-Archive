---
title: "'Error loading operating system'"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by davidajohnson12 on 2008-03-17
Hello,
I received this error after I tried installing ubuntu 7.10 on a computer with windows xp as the other operating system. I used the 'Guided-resize...and use freed space' optionto give ubuntu about 7 GB. The rest of the installation went pretty seamlessly until the end. I am pretty sure it finished installing, but  I don't remember it ever giving the me the 'Continue using live cd' or 'Restart now' screen. I don't pay much attention sometimes though, so I may just not remember clicking the "continue using live cd' button. Regardless, I restarted and that's when I got this error. Can anyone help me please? Has anyone seen this before. Did I lose my Windows OS? Ubuntu? Both? Or, could it be something with me telling it to continue using the live cd? I appreciate your advice.

Dave

---

### Post by Xiong Chiamiov on 2008-03-17
My guess is that both your operating systems are just fine, but GRUB (the bootloader that tells the system where to look for an OS) is pointing at the wrong place.  It's a little hard to tell without being there, but I had to adjust mine manually since the automagic options weren't correct for me.

---

### Post by davidajohnson12 on 2008-03-17
So, might you have any idea how to check if it is a problem with GRUB?...and how to fix it possibly...? Thanks.

---

### Post by Ub1476 on 2008-03-17
[Super Grub Disk]("http://supergrub.forjamari.linex.org/?section=download").

Burn it to a CD, boot onto it and let it search for an OS and start it (it can also reinstall GRUB, but in this case it's probably just wrong configs).

It also might be that the installation did not work correctly, but you'll figure that out as soon as SGD boots up Ubuntu.

---

### Post by davidajohnson12 on 2008-03-17
When I boot with the Super GRUB Disk, it gives me the same error message. I even made sure it booted from the cdrom and not the HD. Any other ideas?

---

### Post by davidajohnson12 on 2008-03-17
ok, don't listen to my previous post. I was stupid and just burned the iso to a disk without actually mounting it to the disk. whoops. I am playing around with SGD right now...I'll let you know if I can get it to work. Thanks.

Dave

---

### Post by jimv on 2008-03-18
Make sure that NTLDR, NTDETECT.COM, and BOOT.INI exist on your XP partition.  Some machines (like my laptop) store these files on the first partition of hte drive, which in my case was a backup partition.  If the files don't exist, copy NTLDR and NTDETECT.COM from the I386 folder on an XP disk to the root of your XP drive.  As for the boot.ini, google it and you should find the default configuration in an MS kb article.

---

### Post by davidajohnson12 on 2008-03-18
Sorry to be dragging everyone along with me through my trials and tribulations, but it seems like every time I fix one thing, something else goes wrong. I truly appreciate everyone's input.

Here is my current situation: I have used Super Grub Disk and tried every option and nothing works. I have also loaded ubuntu with the cd and played around with the partitions a little bit. I now have (1) 176.74 GB hard drive that has all of my Windows stuff on it. It's location is /dev/hda1 (is this correct for a windows partition?) and it is a ntfs file system with 15.05 GB unused (GParted says '15.05 GiB boot' under the unused column). After that, there is 9.57 GB of unallocated space. I do not have any /boot or /root partitions. Do I need these for Windows to boot? If so, can I just change the /dev/hda1 to /boot or /root?  If not, do I just create a new partition (how large?) from the unallocated space? There is absolutely no linux currently on my system.

First, I need to figure out how to get windows to boot if that is still possible, so that I can back up everything before I try to install ubuntu again. If it is absolutely not possible, I am ok with that because I have most of my stuff backed up, but I would rather not have to go through the entire setup process again. Can anyone help me figure out what I need to partition or what I need to install, etc, etc, etc...in order to get windows to boot again? I tried booting with the windows xp install cd and it gets to a screen that says "Press any key to boot from cd" and it freezes. Also, when I try to boot windows from Super Grub Disk (after trying to 'Fix Boot of Windows' of course) it just freezes on a black screen right away and nothing about windows ever comes up.

Thanks for your help.

Dave

---

### Post by davidajohnson12 on 2008-03-18
> **jimv said:**
> Make sure that NTLDR, NTDETECT.COM, and BOOT.INI exist on your XP partition.  Some machines (like my laptop) store these files on the first partition of hte drive, which in my case was a backup partition.  If the files don't exist, copy NTLDR and NTDETECT.COM from the I386 folder on an XP disk to the root of your XP drive.  As for the boot.ini, google it and you should find the default configuration in an MS kb article.

Jimv,
What is the root of my xp drive? Can I just paste those files onto the windows partition? See my last post for more information of my current setup. Thanks.

Dave

---

### Post by jimv on 2008-03-19
Usually when one says the root of a drive, they mean the partition....like if I told you to copy a file into the root of your c drive, that would mean just copy it onto the c drive, but not in any folders.

---

