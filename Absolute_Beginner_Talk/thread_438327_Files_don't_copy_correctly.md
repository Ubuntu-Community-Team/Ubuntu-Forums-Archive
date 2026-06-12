---
title: "Files don't copy correctly"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Happy_Man on 2007-05-09
Hey everyone,

I had no idea where else to post this, so I'll put it here: I am running a dual-boot, and have finally acquired enough experience (IMO) to completely wipe Windows. Of course, the first step for that is to back up all the stuff on the NTFS partition so your mother doesn't get angry when she wants a photo and I wiped it. :) So, I went into Konq, selected the "Documents and Settings" folder (I know, overkill, but better safe than sorry, hm?) and selected "Copy to /home/----". Wonderful. It started copying the (so it said) 18.1 GB of files and random configs. Great, come back after it finishes, and BAM! Nothing but empty folders. WTF? Is this some random quirk that I am not aware of? All my info is still safe and sound (thank god) on the original Windows partition, so I can copy stuff over as many times as I want. But I would like to know why it didn't copy correctly...any theories? 

**BTW, I run Kubuntu Feisty.**

---

### Post by jargoman on 2007-05-09
try copying from the command line. I don't know how you mounted your ntfs partition when you installed so your command might be different depending on where your partition is mounted. Also when I do a backup I only backup my "Documents and Settings" folder

on my computer the command is

$ mkdir /home/win
$ cp -r /media/hda1/Documents\ and\ Settings /home/win

If you get a message saying permission denied then add sudo before the command. Also make sure the partition is mounted.

either double click on the icon on your desktop
or
$ sudo mount /dev/hda1 /media/hda1

this is assuming that windows is on the first partition

---

