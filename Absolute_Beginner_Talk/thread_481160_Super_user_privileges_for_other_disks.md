---
title: "Super user privileges for other disks"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Daevius on 2007-06-22
Hi,

We were having some problems with a dual boot with ubuntu and XP. It seems that XP cant be started anymore. We figured that we probably have to add the files boot.ini, ntldr and ntdetect.com to the C: drive. Ubuntu starts without any problems, so we wanted to copy the files we from another XP to the one that doesnt starts up. However, I do not have privileges to do so. We cannot create or modify any file on our XP harddrive. How can I add those files to the harddrive? 

Greetings,
Daevius

---

### Post by Crooksey on 2007-06-22
How are you starting XP, via grub or with the windows boot loader?

---

### Post by obbe on 2007-06-22
i think you should have to install the ntfs configuration tool to be able to write on an ntfs partition

---

### Post by Daevius on 2007-06-22
Previously I used a windows boot program to choose between the two XP's I had. The xp on the master drive I deleted and I installed Ubuntu on it. Ubuntu now launches grub all the time. In /boot/grub/menu.lst I added a windows options for grub with: setup (hd1,0). Ubuntu has: setup (hd0,0). So perhaps its not hd1,0?

So I use grub. When I choose XP to start up, it stucks with 'Starting up...'
I guess it has something to do that the C: drive of windows doesnt contains the file I mentioned in my previous post.

I will try the ntfs configuration tool, thank you.

Daevius

---

### Post by Daevius on 2007-06-22
Okay, the NTFS Configuration tool works :D, thank you :)

I added the files boot.ini, ntldr and ntdetect.com to the C: drive. I copied them from another running XP from another machine. I restarted the pc and choose to start XP, but it still stucks with 'Starting up...'

Perhaps /boot/grub/menu.lst isnt configured alright, or perhaps the files from the other XP cannot be used for this xp?

Daevius

---

### Post by Daevius on 2007-06-22
I change the jumper on the harddrives. I made Windows the master drive, and windows now succesfully started up, because I added the 3 files I meantioned earlier.

I guess GRUB wasnt configured alright to start up Windows. What else could it possibly be than hd1,0 and how can I find out whats right?

Thanks in advance :)

Daevius

---

