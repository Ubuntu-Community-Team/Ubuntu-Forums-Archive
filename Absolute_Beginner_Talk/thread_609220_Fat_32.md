---
title: "Fat 32"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2007-11-10
I have Ubuntu up and running on my second hard drive just fine. I have an external hard drive which is formatted FAT32 and I have some videos on it. I am able to play those videos with VLC just fine. I want to use this drive to store music files. I will be saving these files from Ubuntu. Will I need to repartition and reformat this drive to accomplish this? Would running a virtual machine from Ubuntu be better for this? 

My ultimate goal is to completely switch to Linux. The only thing holding me back from doing that right now is that my wife has a program that she has to run from windows. She works in a school district and sometimes works from home so she has to connect to the district server to accomplish that. Can she do this with a virtual machine? Of course I would have to learn how to do this myself and then teach her.

---

### Post by MarCustomized on 2007-11-10
Linux can write to Fat32 partitions just fine.

---

### Post by escobar_ on 2007-11-10
No, you don't have to reformat or repartition it. Ubuntu can write on FAT32 as well as NTFS so you are all set.

Perhaps the program your wife uses can be run with [Wine]("http://en.wikipedia.org/wiki/Wine_(software)")? I suggest keeping Windows as a dual boot until it's clear whether the program works in Wine or not.

---

### Post by geirha on 2007-11-10
> **bgast1 said:**
> I have Ubuntu up and running on my second hard drive just fine. I have an external hard drive which is formatted FAT32 and I have some videos on it. I am able to play those videos with VLC just fine. I want to use this drive to store music files. I will be saving these files from Ubuntu. Will I need to repartition and reformat this drive to accomplish this? Would running a virtual machine from Ubuntu be better for this? 

Fat32 is fine for external drives, you will be able to read and write to it easily, though make sure you right-click the drive and select unmount before you disconnect it, or there's a high chance you will lose data. Also, linux filesystems allows alot more characters in filenames that fat32 don't, so if you have a music file with a "?" questionmark in it for example, you will get an error when trying to copy it to the external drive. Removing or replacing the ? with a _ for instance is a typical work around.

> **bgast1 said:**
> My ultimate goal is to completely switch to Linux. The only thing holding me back from doing that right now is that my wife has a program that she has to run from windows. She works in a school district and sometimes works from home so she has to connect to the district server to accomplish that. Can she do this with a virtual machine? Of course I would have to learn how to do this myself and then teach her.

What program is it she's using? If it's remote desktop connection she needs to connect to a terminal server at work, then ubuntu also has a program to do that. You'll find it in Applications -> Internet -> Terminal server client.

---

### Post by bgast1 on 2007-11-10
:( Guess I will just have to be satisfied with a dual boot system. Besides I have a bunch of games that would probably just run better out of windows anyway. My list of games that I play are:

Command & Conquer Decades
Command & Conquer 3 Tiberium Wars
Tiger Woods PGA Tour 2008
Civilization III Complete
Civilization iV and Warlords Expansion Pack
Doom III (Windows version) - have absolutely no idea how to make it run in Linux
F.E.A.R. -- paid for, downloaded version
Half Life 2 -- paid for, downloaded version
I want to get Bioshock
I want to get that latest Leisure Suit Larry, uncensored version. 

Have not played around with wine. But tried Cedega several months ago with very little success.

---

### Post by bgast1 on 2007-11-10
> **geirha said:**
> Fat32 is fine for external drives, you will be able to read and write to it easily, though make sure you right-click the drive and select unmount before you disconnect it, or there's a high chance you will lose data. Also, linux filesystems allows alot more characters in filenames that fat32 don't, so if you have a music file with a "?" questionmark in it for example, you will get an error when trying to copy it to the external drive. Removing or replacing the ? with a _ for instance is a typical work around.



What program is it she's using? If it's remote desktop connection she needs to connect to a terminal server at work, then ubuntu also has a program to do that. You'll find it in Applications -> Internet -> Terminal server client.

I need to learn a whole lot more about Linux, and Linux file systems before I understand what you just talked about in the first paragraph. I want to set up a folder called 'My Music' on that drive. I will be ripping CD's to that folder. I have been using computers since the DOS days, and know how to use DOS, but have not invested much time learning Linux yet. I will though. :), just need to get started, I am still very new to Linux.

The program that my wife uses is called Skyward. The school district that she works in, as far as I know only has windows machines.

---

