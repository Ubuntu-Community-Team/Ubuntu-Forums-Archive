---
title: "need help with a daul boot"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by Artist22405 on 2006-06-06
OK so I need windows for some work stuff sign plotters and stuff > I have been using dapper for about 6 weeks love it . Well my old hard drive died on me . 
I just 4 days ago set up my wifes computer with a daul boot windows and dapper she loves it . 
OK heres the thing I want to put dapper on this hard drive and use it dual boot but I got my work stuff here too I have 61 gigs left on a 120 gi hd I really dont want to start with new installs like the wifes pc as I have setting in felxisign program that will take way too long to redo . what are the chances of just installing dapper on the hd like my wifes but not from a new install of windowswithout messing windows up also .

---

### Post by rcarring on 2006-06-06
You could try Dapper in a Virtual Machine.

Get the vmplayer and got to [http://www.easyvmx.com](http://www.easyvmx.com) to prepare your virtual machine for vmplayer to run.

From a clean virtual hard disk I found the alternate install cd supported everything out of the box.

I didn't have to install vmware tools to get it working either.

This way you can still switch between Windows and Linux without having to worry about resizing the drive.

I would get a 20GB virtual drive and see how you go.

---

### Post by aysiu on 2006-06-06
What's your question exactly?

Are you afraid of messing up Windows (you appeared to be okay setting up your wife's dual boot)? Or do you just not want to reconfigure Ubuntu all over again?

---

### Post by djsroknrol on 2006-06-06
You could also use the Gparted live cd to resize a 10 - 15 GB partition and dual boot with both OS's....

In the beginning, I peeled off 10GB off my 40GB HD and dual booted 98se and breezy for a while....haven't booted into windows in a couple of weeks now, and I'm thinking about peeling off more to make a new /home directory...

---

### Post by RRS on 2006-06-06
If I'm reading your question right when you installed your wifes system windows was also freshly installed? 

It isn't neccessary to do this on your system before installing Ubuntu, Your existing windows installation and data should be quite safe.

Having said that, I would still advise backing up any important data, just in case.

It would also be a good idea to defrag a couple times first  too.

---

### Post by Artist22405 on 2006-06-06
my question is what are the chances of messing up my windows partion I havent done anything yet  . And my wife computer was wiped and everything was a fresh install this wouldnt be a fresh install this drive has work stuff on it but I really hate windows and have been digging dapper for a lil bit now et on windows really sucks. I just cant mess with the settingsin felxisign took too long to get them where they are now .If need be I will save up for a new hd and go with that and dapper. itll just be a while is all

---

### Post by Artist22405 on 2006-06-06
ok kool one more thing when I installed dapper and xp on my wifes pc I made the partion 10 gigs thinking that dapper would take 10 gigs and it left windows with 10 gigs out of 38 is this correct?

---

### Post by aysiu on 2006-06-06
For partitioning schemes:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

Can I take felxisign is some kind of Windows program you need for work? All the settings usually live in C:\Documents and Settings\username\Application Data. You can just back that folder up. Otherwise, there may be system-wide settings stored in C:\Program Files\felxisign

Settings are relatively to back up in both Windows and Ubuntu.

I say back up your settings, repartition, and go for the dual-boot.

---

### Post by rcarring on 2006-06-06
Um, I would expect the settings would be stored in both the users Documents & Settings folder in Application Data as well as in the registry. They would have to export every single key in the registry to do with the specific software program they mention. Not to mention reinstall the program and retweak it if the settings it uses (such as an ini file) are missed.

My idea is probably the safest. The only time they would see Windows is when they boot their machine and run vmplayer.

---

### Post by confused57 on 2006-06-06
[QUOTE=Artist22405]my question is what are the chances of messing up my windows partion I havent done anything yet  . And my wife computer was wiped and everything was a fresh install this wouldnt be a fresh install this drive has work stuff on it but I really hate windows and have been digging dapper for a lil bit now et on windows really sucks. I just cant mess with the settingsin felxisign took too long to get them where they are now .If need be I will save up for a new hd and go with that and dapper. itll just be a while is all[/QUOTE]

If you go with a 2nd hd, see if this may be an option:

[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot)

Please read the instructions by "lha" in the links provided.

---

