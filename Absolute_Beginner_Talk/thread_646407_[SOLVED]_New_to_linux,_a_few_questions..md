---
title: "[SOLVED] New to linux, a few questions."
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by ring_wraith on 2007-12-21
Hi ! 

This is my first post on the forums, and my first 10 minutes on Ubuntu as well! But hey, I managed to get it installed which was surprisingly easy. So much for the horror stories people told me of Installing a linux. The reason i switched to Linux after 5 years of windows is that i really love tweaking and fiddling with stuff, which windows barely allowed me to do. I also am a fan of using the command line, as I find it faster than a GUI. Both these desires of mine were enough to make me realize that I just had to get myself a linux, and now that i have it, i am eager to learn! However, as expected , i haven't had the smoothest of starts, and I have a couple of questions.  

This is my current computer config : 

Core2Duo E6550 2.33Ghz [OC to 3.0]
1GB of Transcend DDR2667 RAM 
MSI P6N SLI V2 
XFX 8600GT 256MB PCI-E
LG GSA H55N DVD Writer
Samsung 160GB Sata disk 
HP Laserjet 1020
Canoscan D646u ex
Samsung Syncmaster 740N
PS/2 optical mouse and KB

So, Ubuntu picked up my internet, resolution, graphics as well as printer just fine. I haven't had a chance to test the scanner or sound, which leads us to my first question.

1) How do I access my other partitions? I have my music on a partition different from that which Ubuntu is installed on. I cant seem to access it. Its not under places or even under computer, 

2)Can I adjust my colors? I like to have my gamma a little lower than default.... can i do this? 

3)I currently am a student who is learning C++ and Java. I have pretty much decided my job is going to be something to do with computers, probably Software Dev. Is Linux a useful OS to know in this regard? Because it would be great if one of my interests actually helps me out later on. 

Well, that's all for now. Thank all of you in advance for your answers!

---

### Post by TheLions on 2007-12-21
1) you don't have 7.10 version, right?
2) dunno
3)KDevelop

---

### Post by Sbarton on 2007-12-21
HI! and welcome to 'Ubuntu'.
Have you dual booted with windows? Were the other partitions part of windows?
Have a look at this site for some interesting tutorials!
[http://www.psychocats.net/](http://www.psychocats.net/)
Also have a look at [http://ubuntuforums.org/showthread.php?t=287271)re](http://ubuntuforums.org/showthread.php?t=287271)re) Gamma change.
regards

---

### Post by bansteen on 2007-12-21
For java and c++ go the eclipse website and download appropriate versions.
u can mount all of your windows partions even ntfs.
try the fdisk command to show all your partitions.
and the mount command to mount ur drives.

Sorry, can't help u in detail. google them. gtg.

---

### Post by ring_wraith on 2007-12-21
sparton, yes i have dual booted with XP. I Have 4 partitions, one for windows, one for downloads one for music and one for ubuntu.

---

### Post by svalding on 2007-12-21
1. You probably need to install support for NTFS, have a search of the forums. There are numerous posts.
2. Yes, you can set these variables in xorg.conf. In terminal do a:
```
locate xorg.conf
``` It will be in /etc/X11 I imagine.
3. As stated above, Kdevelop is my programming tool of choice.

---

### Post by maljaros on 2007-12-21
I am also a beginner, so cannot tell you the reasons, but when I loaded Gutsy four weeks ago and opened Musicbox it went and found all the music files on my disk, regardless of which partition they were in.
I had never heard of gamma settings, but when I right clicked on the desktop one of the options that came up was a set of three sliders that changed the hue.  That was in XFCE - don't know if that makes a difference.

---

### Post by seventhc on 2007-12-21
click on 'Applications>Add/remove make sure the upper right corner is set to all open source applications, then do a search for NTFS, you will see NTFS Configuration Tool. install that. this will enable read write support for your windows partitions.

---

### Post by roaldz on 2007-12-21
> **ring_wraith said:**
> Hi ! 

This is my first post on the forums, and my first 10 minutes on Ubuntu as well! But hey, I managed to get it installed which was surprisingly easy. So much for the horror stories people told me of Installing a linux. The reason i switched to Linux after 5 years of windows is that i really love tweaking and fiddling with stuff, which windows barely allowed me to do. I also am a fan of using the command line, as I find it faster than a GUI. Both these desires of mine were enough to make me realize that I just had to get myself a linux, and now that i have it, i am eager to learn! However, as expected , i haven't had the smoothest of starts, and I have a couple of questions.  

This is my current computer config : 

Core2Duo E6550 2.33Ghz [OC to 3.0]
1GB of Transcend DDR2667 RAM 
MSI P6N SLI V2 
XFX 8600GT 256MB PCI-E
LG GSA H55N DVD Writer
Samsung 160GB Sata disk 
HP Laserjet 1020
Canoscan D646u ex
Samsung Syncmaster 740N
PS/2 optical mouse and KB

So, Ubuntu picked up my internet, resolution, graphics as well as printer just fine. I haven't had a chance to test the scanner or sound, which leads us to my first question.

1) How do I access my other partitions? I have my music on a partition different from that which Ubuntu is installed on. I cant seem to access it. Its not under places or even under computer, 

2)Can I adjust my colors? I like to have my gamma a little lower than default.... can i do this? 

3)I currently am a student who is learning C++ and Java. I have pretty much decided my job is going to be something to do with computers, probably Software Dev. Is Linux a useful OS to know in this regard? Because it would be great if one of my interests actually helps me out later on. 

Well, that's all for now. Thank all of you in advance for your answers!
If ubuntu doesn´t see your other partitions, they shouldn´t be listed if you run the command ¨mount¨ in a terminal. That command is used to mount filesystems to places, so you can read/write them.
Your harddisks are represented by device files. These files are located in /dev/.
/dev/sda is your primary master, sdb is your primary slave, sdc, secondary master and so on.
/dev/sda1 is the first partition on the primary hard drive. 
Normally you don´t need all this, but if the command ¨mount¨ doesn´t list your desired partition, you should execute this:
```
sudo mount /dev/sd** /media/<mountdir>
```
Make sure /media/<mountdir> is replaced by the correct directory, and make sure /dev/sd** is replaced by the correct device file.

Good luck and welcome!

---

### Post by Sef on 2007-12-21
> sparton, yes i have dual booted with XP. I Have 4 partitions, one for windows, one for downloads one for music and one for ubuntu.

Applications > Accessories > Terminal

Let's check your partitions, so do this command:

```
sudo fdisk -l
``` (That's a small L.)

Copy and paste the results here.

---

### Post by ring_wraith on 2007-12-21
Thank you all for the help, but i figured it out! 

I had done an illegal shutdown of windows and as a result chdsk was scheduled to run and to my best guess the disks were being read as currently in use and thus linux was not mounting them. 

I let chkdsk run and my disks mounted successfully.

---

