---
title: "I have a few noob questions...."
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by Nameless on 2005-12-19
Hi all, this is my first post, but I'm looking forward to having many more.  

I've been reading the boards for a couple of days and I decided that I wanted to go with a dual boot system so I could ease my way into Linux.  I'm currently running an old Dell desktop and an HP zv6000 laptop.  I successfully (and easilly) installed Ubuntu on a 10GB (of a total 40GB) partition of my desktop.  My primary purpose for Ubuntu is going to be learing and maintiang my digital media...and of coarse, much better security. 

That being said, I had a few questions that I wasn't yet able to find in the forums and was wondering if anyone could help: 

1) I want to basically have a shared drive on my desktop that both Windows and Ubuntu can use for iTunes and Amarok.  I realized I need to make this a FAT32 drive so that both can write to it.  My questions is is there a mazimum size that I can make this FAT32 drive.  I have a seperate 80GB harddrive that is simply for digital media storage and I would like to make the whole thing FAT32, but I don't know if that is realistic.  

2) Right now my 80GB drive is NTFS, can I convert this to FAT32 without losing any 
data? 

I think I've read enough on how to mount the drive once, but I had questions about the above.  

Thanks everyone,
Nate

---

### Post by lurch2012 on 2005-12-19
I'm a relative noob myself, but I can tell you that a Fat32 drive as swap is agreat idea and there should be no problem with the fact that it is 80 Gig...I do not, however, think it is possible to convert from NTFS to FAT32 without data loss...One problem I came up with in a similar situation is giving root access to my fat32 drive to certain programs within linux...I had to put my digital media collection on my ubuntu home folder for Amarok to be able to manipulate ID3 tags and whatnot...I'm sure there are ways around it, but this just seemed easier...BTW...definitely get amaroK (you'll need KDM) for your digital audio collection...

---

### Post by Nameless on 2005-12-19
What is KDM?  Does that work with Amarok?  I just succesfully mounted my 80GB windows drive, but wasn't able to import my songs. I think I need to play around a little more.   

That's unforutnate about not being able to convert from NFTS > FAT32.  I'm going to need to some moving a lot things around to get that set up then

---

### Post by aysiu on 2005-12-19
[QUOTE=Nameless]
1) I want to basically have a shared drive on my desktop that both Windows and Ubuntu can use for iTunes and Amarok.  I realized I need to make this a FAT32 drive so that both can write to it.  My questions is is there a mazimum size that I can make this FAT32 drive.  I have a seperate 80GB harddrive that is simply for digital media storage and I would like to make the whole thing FAT32, but I don't know if that is realistic.[/quote] 80 GB should be fine. I was doing the same thing on a 100 GB FAT32 partition between iTunes and JuK until recently.

> 
2) Right now my 80GB drive is NTFS, can I convert this to FAT32 without losing any 
data?  You can't *convert* it to FAT32 without data loss, but you can *shrink* the NTFS partition and create a new FAT32 partition with the remaining space. And whenever you're repartitioning or changing filesystems, you **should always back up your data**.

I'm sure she/he means well, but I don't know what lurch2012 is talking about. 
1. JuK, AmaroK, and Rhythmbox all recognized my iTunes ID3 tags.
2. Root shouldn't come into play at all if you have your FAT32 partition properly mounted (see the fourth link in my sig).
3. KDM has nothing to do with this situation--it's what handles the login screens and logging out. KDM is the KDE version, and GDM is the Gnome version.

---

### Post by jimrz on 2005-12-19
How much unused space do you have on your 80Gb drive? PartionMagic can convert without loss of data but it needs about 55% (at least) unused space. I did this a few weeks ago getting ready to do my ubuntu install, worked like a charm.

---

### Post by Nameless on 2005-12-20
Aysiu, I actually decided that I wanted to make the 80GB drive a 70GB ext3 drive and a 10GB Fat32 drive.  I am going to commit to using my iPod strictly on the Linux start up for now.  

Out of curiosity, did you use Juk for your iPod as well?  I found GTKpod (could be spelled wrong) that seems like it will help syncronize the two, but I didn't quite get far enough installing it.  

Jimrz, I actually decided to back up the entire drive to my laptop (100GB) and so I clean off the 80GB drive.  It had about 65GB of info on it, so I don't think I would have been able to ParitionMagic it.

---

### Post by lurch2012 on 2005-12-24
What I meant was that for whatever reason I had trouble using a FAT32 as a shared partition between Windows/Ubuntu. I gave up attempting to allow programs to edit info. I never had any problems with any programs reading ID3 tag's I just had problems editting them(I could only get ubuntu to have read-only access to the FAT32 without running the "Run as Root" Script). As for KDM, its part of the KDE environment and if you install Ubuntu you won't be able to get AmaroK until you install the KDE Desktop Environment...You can still use the Gnome interface (which I prefer), but AmaroK is dependant on several components of KDE...

---

### Post by aysiu on 2005-12-25
[QUOTE=Nameless]
Out of curiosity, did you use Juk for your iPod as well?  I found GTKpod (could be spelled wrong) that seems like it will help syncronize the two, but I didn't quite get far enough installing it.[/QUOTE] JuK doesn't interface with the iPod. AmaroK and Banshee will, though.

Gtkpod isn't that difficult to install. See the first link of my sig, then ```
sudo apt-get update
sudo apt-get install gtkpod
gtkpod
```

---

