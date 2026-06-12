---
title: "Ubuntu Install - should I partition?"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by ptirapeo on 2007-08-28
I am doing a completely new install of Ubuntu on a laptop.  The intsall asks to Partition 60/40 or use entire disk?

What is the difference here?  I don't want to save anything I had on the hard drive b/c I want to start from scratch and erase anything that was on my hard drive.

However, the install states:
How do you want to partition the disk?
1-Guided - resize IDE1 master, partition#1 (hda1) and use freed space
2-Guided - use entire disk
3-Manual

What do you recommend?

Thanks in advance.

---

### Post by mikewhatever on 2007-08-28
Since you want it from scratch, use the entire disk option.

---

### Post by crazypiglady on 2007-08-28
I recently upgraded my version of ubuntu and was very pleased i'd created a separate partition for /home (my personal files) which i could choose not to overwrite. I'm not sure if I'd have had this option if i'd used the entire disc. The install process offered this option to choose /home as the new partition. I think it forces you to make a swap partition (ie it does this by itself). You can move /home to a new partition later but cleaner to do it at installation.

---

### Post by Wikzo on 2007-08-28
If you are new to Ubuntu and want to make a fresh start, use the "2-Guided - use entire disk" :)

---

### Post by ptirapeo on 2007-08-28
Thank you.
I will use the entire disk.
Hopefully I will be up and running in a bit.

Thanks again!

---

### Post by Wikzo on 2007-08-28
On my Acer laptop (512 RAM) the installation took about 20 minutes, which I think is really fast for a system to install :)

---

### Post by MozartlovesUbun2 on 2007-08-29
but is it a good idea to have "/" and "/home" in separate partitions?
I'ld like to keep all my data safe and have the option to do a clean OS install anytime, so the question is why doesn't ubuntu give this choice by default when installing? I had to get the alternative install CD for it.

well i'ld like to do a clean install of gusty over my feisty when it comes out, so is it gonna recognize automatically that my home folder is in a seperate partition or is it gonna make another home folder on the "/" main OS partition?

also i saw using the gusty tribe5 live CD that it has new folders in the "/home" like (Music, Videos...etc) how is that gonna go with my current "/home" installation?

well i got Automatix all over to install various stuff, read too late now some people say to avoid it, so whats a good alternative and am I gonna have problems if I decide to upgrade feisty to gusty instead of the clean install option, and if i go for the clean install how is my "/home" which is on a separate partition gonna react to that?

or to put the question again precisely: "whats the best way to install ubuntu?" with or without seperate "/home" partition.

i'm linux newbie thanks for any help

---

### Post by hyper_ch on 2007-08-29
yes, it's good to have a seperate home. That is where you (normally) store your user files and user specific settings/configurations for programs....

I'd say make 1 partition about 1 GB in size for SWAP
then about 10-15 GB for root "/"
and the rest for "/home"

assuming you have a 100 GB drive.

---

### Post by tnc on 2007-08-29
Hiya.  
I'm new to Ubuntu but was using Mandrake/mandriva for last 5 years. (just for some credibility I guess.)
Absolutly go with the separate /home partition.  Although you should always be careful, a fresh install of future releases will always give you the option to keep your /home folder.  This will enable you to keep all your "stuff" and do a fresh install.   The fresh install will not create a new home folder as long as you tell it that "hey, this is my home folder here" so to speak.
Tim

---

### Post by MozartlovesUbun2 on 2007-08-29
thank you for the super fast response
yes i have a 120GB drive,

one question i'ld still like to ask, how are the new folders which gusty creates (like "Movies", Documents" etc) gonna react to my existing home folder?

well if it is a good idea to have home on a seperate partition then why doesn't ubuntu give this option as default?

--------------------------------------------------------------
also is it theoretically possible to switch to another distro without any major hassles as the home folder is on a seperate partition (not that i'ld really wanna do that, just wanted to know) am very happy with feisty.

---

### Post by hyper_ch on 2007-08-29
Waht new folders does gutsy create?

---

### Post by tnc on 2007-08-29
Hiya 'gain.
My experience with Ubuntu was that, yes, I had to tell it "this here is the /home folder".  Kinda like naming the partition for the installer.
As for the folders, logic says that as long as it accepts the existing /home folder, it will just create the new folders it wants inside /home.
Seems though that hyper_ch may know for sure....?
Tim

---

### Post by hyper_ch on 2007-08-29
well, during install process you select manual partitioning and then you just say where the root and home folder are to be found.

e.g.  /dev/hda1  &  /dev/hda3

It will not overwrite anything in your home but if new stuff is required, it will create that...

But then of course, always make backups first ;)

---

### Post by r4ik on 2007-08-29
I have my "Home" on a separate external disk.
I copy and paste all important stuff to that disk just in case something breaks beyond repair.(Hard Or software)
Therefore i have no need for a separate home and just do a fresh install when a new
release comes out.
Just my two cents.

---

### Post by MozartlovesUbun2 on 2007-08-29
here are some links which relate to this topic:

[http://ubuntuforums.org/showthread.php?t=537240&highlight=partition+home](http://ubuntuforums.org/showthread.php?t=537240&highlight=partition+home)

[http://ubuntuforums.org/showthread.php?t=537091&highlight=partition+home](http://ubuntuforums.org/showthread.php?t=537091&highlight=partition+home)

--------------

also now reading your post "r4ik" made me think

is it possible to have multiple seperate "/home" folders which could be synced identical for data safety or just be normal separate "/home" folders entirely so one has more spce?

---

### Post by r4ik on 2007-08-29
If you use "entire disk" and want a separate home later try,

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by r4ik on 2007-08-29
> **MozartlovesUbun2 said:**
> here are some links which relate to this topic:

[http://ubuntuforums.org/showthread.php?t=537240&highlight=partition+home](http://ubuntuforums.org/showthread.php?t=537240&highlight=partition+home)

[http://ubuntuforums.org/showthread.php?t=537091&highlight=partition+home](http://ubuntuforums.org/showthread.php?t=537091&highlight=partition+home)

--------------

also now reading your post "r4ik" made me think

is it possible to have multiple seperate "/home" folders which could be synced identical for data safety or just be normal separate "/home" folders entirely so one has more spce?

Not quite sure what you mean.
I see it this way you can create a separate /home on you're machine and have a .what i call semi-home on a external for safety.
If both disks die at the same time, which is not very likely, it simply had to be that way.

---

### Post by MozartlovesUbun2 on 2007-08-29
what i mean is to have several "/home" in different locations, internal or external, and to have them acting as one, i mean synced if thats the right word, so changes to one effect across all other "/home"

sorry i'm not a PC expert

also I see, there are hidden folders as well in the "/home" which have a "." dot in front of their names (usually app names) so do you copy them all to you external "/home" drive? are the hidden files selectable or important?

---

### Post by r4ik on 2007-08-29
On you're first question i don't know the answer,sorry
Keep in mind i only backup important data like music/spreadsheets etc to my semi-home.
When i do a fresh install of a new release the .files will be automatically installed.

---

### Post by steve.horsley on 2007-08-29
Actually, I'm wondering about keeping two entirely separate systems, with /home being part of the system partition. This would allow me to dual boot a working system and a test system without their settings interfering with each other. I have in the past had problems with a shared home where the application settings for two different versions of an application are incompatible. Of course you need more disk space this way as you will probably have 2 copies of all your data.

---

### Post by MozartlovesUbun2 on 2007-08-29
hi steve
yup i heard of that problem, it mentioned some distros are compatible for sharing same home, i dunno which.

---

