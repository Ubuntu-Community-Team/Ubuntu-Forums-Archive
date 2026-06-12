---
title: "Save my &quot;/home&quot; partion in new installation"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by bladexp210 on 2007-10-10
Hello,
I've just thrown away Windows Vista completely (yey \\:D/) and installed opensuse 10.3, unfortunately it does not work properly with my hardware.
I want to change to Ubuntu Gusty when it comes (fisty Live DVD works great, but I prefer wait another 9 days), but I don't know how to make my actual "/home" partition as the one of my new installation.
What makes me worry is :[LIST=1]
[*]I'm changing from KDE to Gnome (**configuration files** and **access rights**);
[*]The file system (know it's **ext2**);
[*]and the possibility of using a **GUI** (I'm not at ease with text console);[/LIST]Thanks a lot.
-------------------------
Additional infos :[LIST]
[*]Partitions : extended partition with : "/" (10 GB), "swap" (1 GB, same as RAM) and "/home" (83 GB) partitions.
[*]Experience with text console : beginner.
[*]Not always connected to the www.
[*]Very busy : don't have much time to configure computer and software settings.[/LIST]

---

### Post by cameronw on 2007-10-11
The way I understand it you would like to change your home dir to a different folder (another partition) without formattting it during install when the 83GB partition is set as /home. All I can say is that you can use System > Administration > User and Groups   click on your user then find the home dir input. This should redirect your home dir somewhere else (e.g /dev/sda2/home/joebloggs)

---

### Post by dkaddict on 2007-10-11
When you install Ubuntu from a live cd you will, at some stage, be given the opportunity to either do a full install which will wipe your hard drive or to manually edit your partitions and install Ubuntu that way. As long as you do not check your /home partition to be reformatted during the manually edit install process, you will not lose any of its data and the cd will install all of the necessary ~. files. My advice would be to move all of the existing hidden configuration files in your home folder to another folder so that they will not be read by the new install as they could give you some problems. I always move them into an folder called old-config-files or something like that and install whatever distro via the manual partitioning option and go in and pull out the files I wanted to keep whence it has finished installing. I have always used ext3 partitions though so you should read more about that before going to far. There should be loads of documentation concerning the hidden files in your home folder and ext2/3 partitions here in the forums. In konqueror choose to show 'hidden files'. They will then be visible and, again, are all preceded with a . (we call one of them a 'full-stop' here in UK).

The Ubuntu installer is pretty well behaved and will not trouble your files if you do not check the reformat box pertaining to the /home partition you want to keep.

Peace

dk

---

### Post by cameronw on 2007-10-11
Ah I see. You can have the option to not reformat. Maybe it's just that I usually do a backup first and reformat anyway. you could always keep the hidden files and folders there to avoid having to reconfigure everything and remove them using recovery mode or the LiveCD if you run into problems.

---

### Post by bladexp210 on 2007-10-11
My worry is not reconfigure my preferences, what I really worry about is losing my files or not having access (locked folders or files) to them totally.
I am worried because it happened before with windows xp (after reinstall, I could not access the previous "My Documents" partition), but fortunately I could recover my data, thanks to knoppix.

And thanks for your replays,

---

