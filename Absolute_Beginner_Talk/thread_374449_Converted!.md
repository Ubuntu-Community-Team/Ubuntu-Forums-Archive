---
title: "Converted!"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by BuntuConversion on 2007-03-02
I love Ubuntu.  I just did the wubi install, and it was SO EASY, I am already on it.  I love Ubuntu.  I laughed and clapped my hands at how awesome this is.

One problem I've noticed, however, is  SHIFT+ 2 = ",  not @.  I had to use the word processor to insert a special character and copy/paste it.

Also, how come I don't see my C drive?  Also, I just noticed--  SHIFT+2 = " and SHIFT + ' = @  please advise

I LOVE UBUNTU!!!!!

---

### Post by BuntuConversion on 2007-03-02
I mean it.  This is so awesome.  Unbelievably cool.

I LOVE IT!

---

### Post by floke on 2007-03-02
Glad you like it.
Try system/preferences/keyboard

---

### Post by Rhubarb on 2007-03-02
You want to use a US layout keyboard (I'm guessing).
You must've chosen UK english as your keyboard layout when you installed.

Glad to hear everything's going great for you, welcome to the Ubuntu community :)

---

### Post by goodbyewindows on 2007-03-02
Your "C" drive usually auto-mounts and appears on your desktop. It should be /dev/hda1/

---

### Post by dstew on 2007-03-02
Drives in Linux are not designated with single letters, as in windows. So, there is no C drive to be found when you have linux running. Drives in linux are designated either hd0, hd1 etc. when booting, and then as dev/hda, or dev/hdb after linux is loaded. Furthermore, each drive has partitions, which in linux are named dev/hda1, dev/hda2 for example, for two partitions on the hda drive. In windows, the main disk may be partitioned also, but in that case each partition is named with a letter, like C: and D:. But, in windows, C: and D: could also be two different disks. In linux, the disk and partition names are not so ambiguous.

I think from your question that you want to be able to see files on your windows partition from linux, is that right? If so, you need to "mount" the windows partition to someplace on your linux file system tree. On my Xubuntu system, I go to the Disks icon in my system menu, and there I can see the windows partition. I pick a mount point (I made a folder for it in my home directory named Windows_disk) and then enable it. The partition is mounted to the folder, and then I can see the files, and read and write them. This works with no added programs if the Windows partition has a Fat32 file system on it. If it has a NT file system (NTFS), I think you need to add a program to your system if you want to write files to the Windows partition.

You can also mount and unmount partitions from the terminal window using the mount and umount commands.

---

### Post by tlmarker on 2007-03-02
Im with you. I love Linux in general, and Ubuntu in particular.  I am still fighting with a learning curve, as linux makes you "get you hands dirty". But I have never been afraid to jump in and get dirty, I have had a couple bumps, but there are smothed over now.

Now, I am looking for replacement software for Windows programs I need. Once I can find them, it is bye bye windows. (Just got to convince my wife to leave windows. :) )

Regards,
Troy

---

### Post by BuntuConversion on 2007-03-02
I'm going to make a LiveCD for my fiancee, so's we can both start using it--she is a word-processor-email-MySpace computer user, and hates hang-ups and slow crap, so I bet she'd appreciate Linux.  I was just blown away--I came home on my lunch break and saw that the wubi installer was done, so I rebooted, took a leak, checked my email on her computer, and sat back at mine ready to roll.  AMAZINGLY fast install.  I expected it to be 60% done when I got home from work (thanks to my WinXPerience).  Then I clicked a few things, sniffed around, and just started laughing and smiling--it is so awesome.  I messed with the fonts and themes and colors, and shivered when they changed...*gasp*...*immediately*, rather than after some lame "Please Wait" screen...

 Now I know why Linux folk are so die-hard (if only they weren't so snobby sometimes).

Linux Rules.

---

### Post by BuntuConversion on 2007-03-02
> **dstew said:**
> Drives in Linux are not designated with single letters, as in windows. So, there is no C drive to be found when you have linux running. Drives in linux are designated either hd0, hd1 etc. when booting, and then as dev/hda, or dev/hdb after linux is loaded. Furthermore, each drive has partitions, which in linux are named dev/hda1, dev/hda2 for example, for two partitions on the hda drive. In windows, the main disk may be partitioned also, but in that case each partition is named with a letter, like C: and D:. But, in windows, C: and D: could also be two different disks. In linux, the disk and partition names are not so ambiguous.

I think from your question that you want to be able to see files on your windows partition from linux, is that right? If so, you need to "mount" the windows partition to someplace on your linux file system tree. On my Xubuntu system, I go to the Disks icon in my system menu, and there I can see the windows partition. I pick a mount point (I made a folder for it in my home directory named Windows_disk) and then enable it. The partition is mounted to the folder, and then I can see the files, and read and write them. This works with no added programs if the Windows partition has a Fat32 file system on it. If it has a NT file system (NTFS), I think you need to add a program to your system if you want to write files to the Windows partition.

You can also mount and unmount partitions from the terminal window using the mount and umount commands.

This was very helpful--it is exactly what i was wondering.  I'm a Windows user from the beginning of my computer use, so this is obviously a big change.  I want to build a PVR, and my Linux-nerd brother kept saying LinuxLinuxLinux, and after seeing some really cool videos from digg, I figured what the heck, why not try it out.  So it is all new to me, but given my excitement, I don't care if the learning curve is a week or a month--it is already worth it just for the simplicity and ease of use.  I installed and used it on my lunch break--can't beat that!

---

