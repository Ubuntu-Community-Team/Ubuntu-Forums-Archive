---
title: "First time install, &quot;Error loading operating system&quot;"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by andyGILL on 2008-02-01
Alright here's my situation:

I have: 250gb SATA and 2x 320gb IDE

I had a Windows XP Pro installation on the 250gb drive and it was having some problems so I went to repair it with the Windows XP Pro disc.  It failed and stopped starting so I downloaded and burned the Ubuntu 7.10 iso image file.  The LiveCD ran fine and I used it to save some files from the corrupt Windows installation and then I made the decision to switch to Linux for good.

I installed it over the Windows partition using the wizard and everything went smoothing.  Once it finished I was prompted to remove the CD and restart, so I did.  Every time it tries to start I get an "Error loading operating system" error.  I tried re-installing it and I ran into the same problem.

Help please, I really want to switch :popcorn:

---

### Post by jan quark on 2008-02-01
if you have rescued all your personal and important data from your windows partitions

I would suggest installing ubuntu on a blank and formatted drive
direct and straight to the point-solution

download the gparted live CD 
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
[http://gparted-livecd.tuxfamily.org/documentation.php](http://gparted-livecd.tuxfamily.org/documentation.php)

 I hope you have a secondary inet connection :) , but you must post from somewhere :)
and format the drive

then try installing ubuntu using the alternate CD
[http://releases.ubuntu.com/gutsy/](http://releases.ubuntu.com/gutsy/)

there might be a less drastic way so feel free to correct me

---

### Post by andyGILL on 2008-02-01
I am posting from my laptop using wireless, lol.

Do you have AIM or MSN or something I can contact you to help me with this?  I have no idea how to use gparted to format my drive nor do I know what to do with the alternate CD.

Edit: Also, I have the Linux System Rescue Disc, would that have partitioning software like gparted?

---

### Post by jan quark on 2008-02-01
I have only IRC 

you can found me there on the freenode > channel: #ubuntuforums-beginners

read this guide nobody is chasing you its not a competition where the clock is ticking

[http://gparted-livecd.tuxfamily.org/larry/generalities/gparted.htm](http://gparted-livecd.tuxfamily.org/larry/generalities/gparted.htm)

---

### Post by marmaladejackson on 2008-02-01
I'm going to throw my two cents in and suggest you might have a hardware problem with your primary hard drive.  Since you have 3 hard drives, I would suggest switching the boot priority around in the BIOS and installing to another drive.

---

### Post by andyGILL on 2008-02-01
I think you're right marmaladejackson; I formatted and installed Ubuntu 7.10 on a blank, formatted drive and when I restarted that after the installation I got the "Error loading operating system" error again.

Looks like I'll take it in to get a new drive, hopefully I can upgrade to 500gb:popcorn:

---

### Post by marmaladejackson on 2008-02-01
Let me know if that fixes your problem.  I got that message when I forgot to reconnect the hard drive once.  Also, make sure your BIOS reflects the boot priority so you are actually trying to boot the drive with Ubuntu on it and not some old windows extended partition with a bunch of mp3's on it.

---

### Post by andyGILL on 2008-02-01
I tried formatting it as an ext2 but I got the same "Error loading operating system" error.  

I should have time to take it to the repair shop today.

---

