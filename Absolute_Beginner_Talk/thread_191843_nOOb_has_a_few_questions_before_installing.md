---
title: "nOOb has a few questions before installing"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by SpecialEd on 2006-06-08
First off, I've searched the forums and found an answer to a few of my questions, but not for most of them, so I apologize in advance if these have been asked and answered.

I downloaded both the desktop and server versions of Ubuntu. I burned the desktop .iso to disk and tried it out...really pleased with it, especially since it recognized all my hardware (well, almost all, I think).

So, after using the Live CD, the following questions arose (sorry for having so many):

1. From my understanding, the only difference between the desktop and server version in the inclusion of the LAMP (Linux, Apache, MySQL, and PHP--I think that's the correct name?) program in the server version, correct? In other words, the KDE files, hardware drivers, etc. will be included in the server version?

2. The only hardware I was unsure about when using the Live CD was my Hauppauge WinTV PVR-350 tv-tuner card. I looked under the Device Manager and it recognized it, but as far as I know, Hauppauge doesn't have software to run it under a Linux distro. So, is there a Linux app to run tv-tuner cards?

3. Which is better, KDE or Gnome? I realize it probably is mostly personal preference, but are there any major differences? The only thing I could tell, other than the look, was the Konqueror browser that's on KDE.

4. A few years ago, I remember hearing someone talk about having both KDE and Gnome on a Linux OS and being able to choose b/w the two. If I install Ubuntu (server version) and then install the KDE extras, will I have the option to boot into/choose different desktop environments or do I have to use one or the other?

5. What bootloader comes with Ubuntu? GRUB, LILO, or both? Which one is better and why?

6. Since Ubuntu recognized all my other hardware, I'm assuming it'll recognize my Canon PowerShot G6, since the PowerShots are pretty popular cameras. Is that digikam program the app that'll replace Canon's ZoomBrowser for Windows? I need to be able to process RAW files and currently use ZoomBrowser in Windows XP to do so.

7. What program is used to burn DVDs in Ubuntu? I couldn't figure this out on the Live CD.

8. My hard drives are as follows: 2 internal 120 GB and 1 external 300 GB HDDs. I want to be able to move files back and forth b/w Windows and Ubuntu and on both my storage drives, the int. and ext. What file system should I use and why?


Thanks!

---

### Post by 3rdalbum on 2006-06-08
> **SpecialEd]

1. From my understanding, the only difference between the desktop and server version in the inclusion of the LAMP (Linux, Apache, MySQL, and PHP--I think that's the correct name?) program in the server version, correct? In other words, the KDE files, hardware drivers, etc. will be included in the server version?
[/QUOTE]

Actually, the server version does not contain a graphical user interface. That is the main difference. (It can be downloaded later through the repositories). The hardware drivers will be included with the server edition.

[QUOTE=SpecialEd]
2. The only hardware I was unsure about when using the Live CD was my Hauppauge WinTV PVR-350 tv-tuner card. I looked under the Device Manager and it recognized it, but as far as I know, Hauppauge doesn't have software to run it under a Linux distro. So, is there a Linux app to run tv-tuner cards?
[/QUOTE]

The Ubuntu repositories include MythTV, which is a PVR-type program. I get the impression that it works with Hauppauge cards. It can't hurt to try it.

[QUOTE=SpecialEd]
3. Which is better, KDE or Gnome? I realize it probably is mostly personal preference, but are there any major differences? The only thing I could tell, other than the look, was the Konqueror browser that's on KDE.
[/QUOTE]

KDE is tremendously customisable, and allows the user a fine degree of control over their system. Gnome is designed to be simpler and more intuitive. These differences in Desktop Environment are often implemented in add-on programs - for instance, a Gnome-based program is likely to be easy-to-learn, and a KDE one will have lots of different settings.

I prefer Gnome. But if you can, you should try both DEs at some point in time. As far as Ubuntu goes, you should probably start with Ubuntu rather than Kubuntu simply because the documentation is better.

[QUOTE=SpecialEd]
4. A few years ago, I remember hearing someone talk about having both KDE and Gnome on a Linux OS and being able to choose b/w the two. If I install Ubuntu (server version) and then install the KDE extras, will I have the option to boot into/choose different desktop environments or do I have to use one or the other?
[/QUOTE]

Exactly. When you log in, you get the option to use a different "session". You can even run KDE programs during a Gnome session and vice-versa.

[QUOTE=SpecialEd]
5. What bootloader comes with Ubuntu? GRUB, LILO, or both? Which one is better and why?
[/QUOTE]

Both come with Ubuntu. I don't know which is better, but both of them can boot Ubuntu and Windows flawlessly said:**
> 
6. Since Ubuntu recognized all my other hardware, I'm assuming it'll recognize my Canon PowerShot G6, since the PowerShots are pretty popular cameras. Is that digikam program the app that'll replace Canon's ZoomBrowser for Windows? I need to be able to process RAW files and currently use ZoomBrowser in Windows XP to do so.


I don't know if the Powershot uses normal USB mass storage, or Picture Transfer Protocol. Digikam, and its Gnome equivilant F-Spot, shouldn't have any trouble transferring files if the camera uses PTP, and if it uses USB Mass Storage KDE should mount it automatically.

[QUOTE=SpecialEd]
7. What program is used to burn DVDs in Ubuntu? I couldn't figure this out on the Live CD.[/QUOTE]

In Gnome Ubuntu, Nautilus has a CD/DVD burning program built-in ("Go>CD/DVD Creator"). Otherwise, you could download Graveman or GnomeBaker from the repositories, both of which are quite good. If you end off using Kubuntu, you can download K3b which is the best Linux CD-burning program.

Sorry I can't help you with Question 8, but I'm sure someone will advocate a file system for you.

---

### Post by pyromithrandir on 2006-06-08
I'll only take a shot at a couple of these questions.

3. KDE. :) Okay, I'm a bit biased. I use KDE because I can customize it more than I can customize Gnome to make it do what I want. 

4. You can have both installed, and then you choose which one to use when you log in.

5. Grub is used by default in Ubuntu. I think it's better than lilo, but only because I'm more familiar with it. So, I'm biased, but I say use Grub.

7. K3b

8. fat32. It has the best and easiest read/write support for both Windows and Linux.

*Oh, looks like I was beaten to it with more detailed responses. The more the merrier, right?*

---

### Post by Phasmagon on 2006-06-08
I 'll just fill in some blanks.

5. The default boot loader for Ubuntu is grub. In my opinion grub is better, since it allows the user to enter a very small terminal (if needed) and configure boot options on the fly. But in most cases users do not need this option.

8. Linux has to be installed on a native filesystem. Although theoritically it can install on fat32 there are problems and the reason is simple. Fat32 does not allow file permissions. What you can do, not to face any problems, is to have an ext3 (or ext2 but preferably ext3) for your root (/) partition, a fat32 for the files you want to move back and forth the two OSes and your ntfs for your windows.

Some explainations:

NTFS: Ubuntu can read ntfs out of the box, but you have to put a little effort if you want writing capabilities too.
FAT: This file system type is used when you want data available any time any os. (no file permissions).
EXT2, EXT3, REISERFS, JFS, XFS: Your root partition (/) can be anything of the following: ext2, ext3, reiserfs, jfs, xfs. But problems might occur when installing on something else than ext3 (or 2). For instance (/boot) is not recognised by grub when its filesystem is xfs.

So there you go.

---

### Post by SpecialEd on 2006-06-08
First off, thanks to both of you. Your replies were the quickest replies I've gotten from any forum/web site. So far, the community is living up to what it claims to be.


3rdalbum: thanks!

pyromithrandir: 

FAT32? I thought some type of Journaled File Systems was the way to go. Could you be more specific as to why you chose FAT32, other than maybe ease of moving files b/w OSes (if that was your reason)? 

In other words, having a better file system is more important than ease of use for sharing files b/w 2 OSes. Is there a way to create a 3rd partition (FAT32) outside of both OSes to store the files? Also, I thought I read somewhere that FAT32 only supports files 4 GBs of smaller in size, is this true, maybe I'm thinking of something else?

---

### Post by r3st on 2006-06-08
about the camera, #6
yes it will recognize it, you dont have to install digikam. just plug it in.

---

### Post by SpecialEd on 2006-06-08
Phasmagon and r3st -- Thanks.

Again, getting answers this quick is great! 

Got it, ext3 and no need for digikam. Now I got everything I need to know.

:grin:

---

### Post by vjun on 2006-06-08
Hi, 
> 
8. My hard drives are as follows: 2 internal 120 GB and 1 external 300 GB HDDs. I want to be able to move files back and forth b/w Windows and Ubuntu and on both my storage drives, the int. and ext. What file system should I use and why?

I have just installed Ubuntu on my laptop few days ago, which it boots winXP Pro too. When you are running on winXP environment, install ext2ifs software [http://www.fs-driver.org/](http://www.fs-driver.org/) to allow you to write/read ext3 file system.

This is the solution when you're running on winXP.

---

### Post by pyromithrandir on 2006-06-08
> **SpecialEd]
FAT32? I thought some type of Journaled File Systems was the way to go. Could you be more specific as to why you chose FAT32, other than maybe ease of moving files b/w OSes (if that was your reason)? [/QUOTE]
Well, the reason I say fat32 is so that you can read/write on both linux and windows with the most ease. i.e. You have to work to install external drivers for Windows to get at ext3 or Reiser (and I don't like spending any more time than I have to on windows, so why would I want to do that  said:**
> 
In other words, having a better file system is more important than ease of use for sharing files b/w 2 OSes. Is there a way to create a 3rd partition (FAT32) outside of both OSes to store the files? 
I may have implied that you should use it for everything- not the case. I was under the impression that when you were asking which filesystem you wanted to have on your "storage" drives, you were implying "drives without an OS on them." So, the answer to your question here is a resounding "Yes!" I have partitions for Windows, Linux and storage, and use fat32 on the storage partitions.
I wouldn't say for a minute that you should install Linux on a fat32 drive. Use ext3 or Reiser or whatever else you want.
[QUOTE=SpecialEd]Also, I thought I read somewhere that FAT32 only supports files 4 GBs of smaller in size, is this true, maybe I'm thinking of something else?[/QUOTE] Yeah, this is true. I don't use huge files on my fat32 partitions anyway, so it doesn't bother me.

If you don't mind going through a bit of extra trouble to get your partitions read/write from both operating systems, then by all means, go with ext3 and use the driver linked by vjun.

---

