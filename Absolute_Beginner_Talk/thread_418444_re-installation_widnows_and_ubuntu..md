---
title: "re-installation widnows and ubuntu."
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by delilahjed44 on 2007-04-22
Ok here is my problem, I want to get back to windows, restore that system, then go back when I am ready for installation with unbuntu, as then I will patition drives.  For now I cannot get past the grub to even get to windows.  My floppy disk holder no longer works to type in fdisk/mbr,  I have Feisty Fawn now.  I am thinking to re-install ubuntu 6.10 the on the choise of space on the hard-drive just eliminate ll.  then the Ubuntu icon will show.  Will this eliminate grub, as I cannot put my windows xp cd in and get into windows.  Typing F1 F2 F12 rapicly upon boot does not work.  So my alternatives lye with the cd holders only not floppy for fisk.mbr.  Can this work? I can install my needs for windows then later re-install ubuntu on dual.. For now I cannot get into windows no matter what and no matter what on opon reboot.

System 8100 Dell dimensions with Ubuntu 7.04.

Thanks Sherri

---

### Post by Happy_Man on 2007-04-22
Well, if you're ok with wiping the hard drive, I would do that, install Windows (no partition, just give it the whole drive), then go ahead and reinstall Ubuntu.

---

### Post by amaroKer on 2007-04-22
If you cannot get a BIOS boot menu with F12, that is not an Operating System problem.  I don't mean to sound demeaning, but ensure that your keyboard is plugged in correctly (maybe pull it out, and put it in again) because the F12 (or F-whatever) boot menu should ALWAYS work.

The dual boot option will require you to install Windows first.  In the Windows installation, setup your partition tables to allow for another OS to be installed, by leaving ~8-10 GB (enough for Ubuntu and a swap-partition) as "unallocated".  This way, when you install Ubuntu again, you won't need to resize your Windows partition.  Also consider formatting your Windows partition as FAT32 instead of NTFS, because NTFS won't play nice with Linux.

Hope this helps!

Logan W

---

### Post by delilahjed44 on 2007-04-22
Well thank you dear, this was the answer I was looking for, I have had to many problems with ubunut on my German lanquage programs and no-one can help, here or otherwise, we have all tried, so I want to use them in Windows see, and some of my other programs that I truly need that are not provided in Ubuntu.  But, my plan is to be able to do a dual boot eventually and then try to install programs as I go along with Feisty.  In this I can still have my programs useful to me, then phase out Windows as Ubuntu increases with the mimick of windows for my programs.  Eventually I can say bye bye to windows, and be in full use of Ubuntu.  I only want to use my programs as I paid good money for them and have not found Linux alternatives as of yet.  Well then there is the mic thing, I too need that for my programs.  Ok hey, thanks again on this, I needed to be sure.

Sherri

---

### Post by delilahjed44 on 2007-04-22
> **amaroKer said:**
> If you cannot get a BIOS boot menu with F12, that is not an Operating System problem.  I don't mean to sound demeaning, but ensure that your keyboard is plugged in correctly (maybe pull it out, and put it in again) because the F12 (or F-whatever) boot menu should ALWAYS work.

The dual boot option will require you to install Windows first.  In the Windows installation, setup your partition tables to allow for another OS to be installed, by leaving ~8-10 GB (enough for Ubuntu and a swap-partition) as "unallocated".  This way, when you install Ubuntu again, you won't need to resize your Windows partition.  Also consider formatting your Windows partition as FAT32 instead of NTFS, because NTFS won't play nice with Linux.

Hope this helps!

Logan W

Hey I will give this a shot first, but truthfully I dont think it will work, I have not been able to get pass the grub in linux period.  I will un-plug keyboard as to reset it, but I dont think it will matter.  I will try it now and respond.
Thanks
sherri

---

### Post by delilahjed44 on 2007-04-22
> **amaroKer said:**
> If you cannot get a BIOS boot menu with F12, that is not an Operating System problem.  I don't mean to sound demeaning, but ensure that your keyboard is plugged in correctly (maybe pull it out, and put it in again) because the F12 (or F-whatever) boot menu should ALWAYS work.

The dual boot option will require you to install Windows first.  In the Windows installation, setup your partition tables to allow for another OS to be installed, by leaving ~8-10 GB (enough for Ubuntu and a swap-partition) as "unallocated".  This way, when you install Ubuntu again, you won't need to resize your Windows partition.  Also consider formatting your Windows partition as FAT32 instead of NTFS, because NTFS won't play nice with Linux.

Hope this helps!

Logan W

Hey, ok hi, I did do exactly as you said and with no luck,  see you cant get past grub unless you have a boot disk of some sort and my floppy is not working. beleive me I have tried every which way, so using the ubuntu cd to clear out the hard-drive should eliminated grub and thus having a choice once again to be able to get back into windows.  Then upon reboot it should work with F1 F2 and or F12, its just the grub wont let me back in.  I will send a note if I have a success.

Sherri

---

### Post by Oki on 2007-04-22
Hi
Do you have a USB keyboard, if "yes" then thats the problem.

---

### Post by delilahjed44 on 2007-04-22
I am not sure,  since I cannot see my properties with keyboard in Ubuntu it does not say, but that is possible.  I have another keyboard but it will set up the same way even if I do plug it in.  So it looks as though cleaning out the system from the ubuntu 6.10 is the option here.  Keyboard even usb should not matter though, if this is so explain please

Thanks
Sherri

---

### Post by Oki on 2007-04-23
If I understand you correct Sherri;  Your problem is that you can not use the keyboard when booting (so you can choose witch OS to use). Older main boards(as mine) can not use a USB attach device upon booting(this has nothing to do with Ubuntu). It cant communicate with USB at that time. 

So take a look at the plug witch your keyboard are using(from the keyboard to the computer), if it is a USB plug then you properly now what the problem is.
I changed the USB plug with a cheep converter so it becomes the olderly keyboard plug, and now it works fine (can choose OS when booting).

---

