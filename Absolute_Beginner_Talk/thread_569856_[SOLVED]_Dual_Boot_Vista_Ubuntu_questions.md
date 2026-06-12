---
title: "[SOLVED] Dual Boot Vista Ubuntu questions"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by SloYerRoll on 2007-10-07
So I searched the forums before I asked this and nothing covered all my questions so here goes...

I'm about to create a dual boot machine that has Ubuntu and Vista on it (currently running Vista only). I want to install photoshop and a few other apps on Ubuntu and check to see them run properly before I make the full migration. I found a few threads on how to install these apps in different places on Ubuntu and it seems pretty easy.

My questions are:
Is there anything I should look for outside of the GUI to make sure all my apps are running properly? (the stuff I can see is obvious)
Is there anything I should validate before I nuke Vista once and for all after I get all my necessary apps running? (hidden pitfalls of making the switch permanent?)

How does the file structure work for linux? (total linux NOOB right now). I'd like to migrate files over to Ubuntu before I nuke Vista so I can keep all my settings on Apps. I'm a photographer and have a highly streamlined workflow that would take weeks to recover if I had to start from scratch. 

Any other hints or tips?

I know how to create partitions and set up dual boot and all that rot. So just from the "taking the plunge" aspect of this. 

Thanks for y our time and help. 
I look forward to finally getting this MS monkey off my back. 

-Jon

---

### Post by rsambuca on 2007-10-07
I think that if you are going to dual boot, then you will inevitably end up answering all of your own questions just through use.  Just take your time and I think you will find that the transition will go fairly smoothly.  If you really are attached to Photoshop, though, I think you may as well keep a dual boot system rather than wipe Vista entirely.  Sure, you can use wine or crossover, but I don't think it works as well, and the new version doesn't work at all yet, as far as I know.l

Make sure you back everything up before installing, and if you are using one drive, Make sure you use the Vista disk Manager to resize the vista partition prior to installing Ubuntu.

---

### Post by SloYerRoll on 2007-10-07
Photoshop, Illustrator and Dreamweaver are just too intergrated into my workflow to just up and switch over to Gimp and whatever vector illustration apps are out there. 
I have clients tha have certain expectations and my reputation is what keeps my business going. 

What's this crossover your talking about? Something cool like being able to run both OS's at the same time? (prays for the answer he wants to hear)

---

### Post by Sklasko on 2007-10-07
Wine, Crossover, and Cedega are basically just compatibility layers for Windows apps to run on Linux.. but if you're running a business, I wouldn't rely on them. If I were you, I would go with a dual boot in your particular case.

Edit: Also, if you've got a relatively powerful system, you could use [VirtualBox]("http://www.virtualbox.org/") to run Windows, and use the Seamless feature of VirtualBox to integrate the Windows system nicely into your Ubuntu desktop.

---

### Post by rsambuca on 2007-10-07
Sklasko answered your question.  There is a virtual alternative as well, where you can indeed run both operating systems on your rig at the same time.  The packages for linux are vmware, or virtualbox.  They let you install another operating system and have it run inside your existing OS.  You need fairly decent specs (RAM, CPU) for it to run smoothly though.

I am not trying to discourage you, but if you are attached to photoshop, illustrator and dreamweaver, and have a good system/streamlined workflow in place, then why are you even considering moving to Linux?

---

### Post by SloYerRoll on 2007-10-07
> **rsambuca said:**
> I am not trying to discourage you, but if you are attached to photoshop, illustrator and dreamweaver, and have a good system/streamlined workflow in place, then why are you even considering moving to Linux?There are some apps that I'm getting exposure to that require Linux exclusively to run. 
The opportunities to make some easy (legitimte) cash if I can use these apps is too much to pass up. 
I used to be a web site designer and have old clients that want clones of existing sites to be modified etc (no phishing)
Through my research, the only truly viable option to clone a site that's non FTP/SSH/SFTP is through WGET. THen make a local host on my machine, edit files to clients taste. Deliver finished product...
I've already checked far and wide for MS apps like this. There are a few, but still young in their development lifecycle and not good for what I need. 


[quote=Sklasko]Edit: Also, if you've got a relatively powerful system, you could use VirtualBox to run Windows, and use the Seamless feature of VirtualBox to integrate the Windows system nicely into your Ubuntu desktop. [/quote] I've got plenty of machine. I usually process about 8-15GB per shoot so I have to have some horsepower. Could you do me a favor and exound a bit on virtual box? I went to the site, but found it a bit too geek for me to understand. Would I leave my MS OS on there and run it through this app? Or would I install MS OS through VB?


----
Lightroom is the only app I "HAVE TO" have. It saves me hours of work in post production. But whether it's 1 app or 50 is kind of irellevant I guess...

----
It seems from your knowledge in this thead that indeed it would be easier for me to just run dual OS's and run ubuntu when I needed the apps. Good to know. But if you could drop a bit more knowledge on me as to my questions/comments. I'd appreciate it. Any links to any thing for me to study would be appreciated too.

-Jon

---

### Post by rsambuca on 2007-10-07
> **SloYerRoll said:**
> 
Lightroom is the only app I "HAVE TO" have. It saves me hours of work in post production. But whether it's 1 app or 50 is kind of irellevant I guess...


Since you have plenty of horsepower, then I guess the decision of dual booting or virtual environments comes down to your usage patterns.  If you are only using the 1 application, then I would say go for vmware or virtualbox.  If you are using lightroom, photoshop, illustrator, dreamweaver, plus others... then I would probably just dual boot.

---

### Post by SloYerRoll on 2007-10-07
Sounds good then. 

Thanks for taking some time w/ another noob rsambuca & Sklasko.

I'm sure I'll be around shortly w/ other noob questions. 

Cheers,
-Jon

---

### Post by jnorthr on 2007-10-07
If you have an old spec machine around the house, you could use it to trial a copy of ubuntu. That way you can mess it up if you need to without worrying about vista for the moment, and you may learn a lot about what it's like to do it for vista. Also keep in mind that the gutsy release is on 18 oct. so you may want to wait for that one as it will save you having to (re)install fixes for some parts that were broken.

---

### Post by SloYerRoll on 2007-10-07
OK since we've determined that Linux isn't really for me since I'm a photographer and rely so heavily on the apps that run in windows.....

All I need to do is run one app: WGET. 
I can't use the windows version since I run Vista. 

I've gone through dozens of help threads in this forum and others and found no answer that was close to looking the same (at least to my non linux NOOB eyes)

So I understand how WGET works and have a good idea on how to run it once it's installed. Problem is.. I have NO IDEA how to install it. 

Here's the details:
Terminal says this when I bring it up:
jon@jon-desktop"~$

Wget 1.9 downloaded on my desktop

where do I go from here?
The instructions say to use make install and a bunch of other stuff. 

I understand this forum isn't designed for hand holding. But I'd really appreciate it if someone could help me out a little bit here so I could get moving. I'm not computer illiterate. I jsut don't know where to start. I've already spent 3 hours culling through forums and google searches for the answer. 

Thanks for any and all your help.

Regards,
-Jon

---

### Post by SloYerRoll on 2007-10-08
bump.

Already on page 9..
Wow this forum moves fast!

Thanks again for your help.

-Jon

Summary of last post so you don't have to scroll back a page to see:

So I understand how WGET works and have a good idea on how to run it once it's installed. Problem is.. I have NO IDEA how to install it. 

Here's the details:
Fresh load of Ubuntu
Terminal says this when I bring it up:
jon@jon-desktop"~$

Wget 1.9 downloaded on my desktop

where do I go from here?

---

### Post by SloYerRoll on 2007-10-08
I'm not trying to hijack this forum. I just need a quick answer off someone. I check to see if it was answered and it's already on page 5 an hour later. 

Someone PLEASE help me out w/ this. I just need Ubuntu for this one app. 

After it's installed, I'll be good to go!

Thanks again...

See previous post for question.

NOTE: I'm not lazy, I read through the command line thread in attempts to figure this out. While I understand basic navigation and copy * move functions. I'm still lost on the install of WGET.

---

### Post by rsambuca on 2007-10-08
Hey there again!  Actually, there is a newer version of wget (1.10), and it is in the repositories.  There are two ways you can install it: via Synaptic Package Manager, or via the terminal.

Synaptic:  Go to your top menu bar and open Synaptic by selecting "System -> Administration -> Synaptic Package Manager".  Enter your password and then scroll down to wget, select it for installation, and press apply.  Done!

Terminal:  Open a terminal "Applications -> Accessories -> Terminal".  At the prompt, enter```
sudo apt-get install wget
```

---

### Post by SloYerRoll on 2007-10-08
Thank you sooo much rsambuca!

Made my day!  I'm already understanding what's going on a little better. 

Cheers!

---

### Post by rsambuca on 2007-10-08
Just so you know there is a version of wget for windows as well.

[http://www.christopherlewis.com/WGet/WGetFiles.htm](http://www.christopherlewis.com/WGet/WGetFiles.htm)

---

### Post by SloYerRoll on 2007-10-08
Ya it only works on VP SP2 though. No Vista Love. 

I'm finding out that there may be other reason for having a nix box in my bag of tricks the more I browse these forums. 

Looks like all is well! I'm up and running! Wget is truly some good stuff!

Thanks again rsambuca!

Cheers.

---

### Post by johnwillyums on 2007-10-19
Hi, I'm a complete newbie and have several queries-

Will I be able to play my music, videos, photographs in Ubuntu or will I have to copy them and therefore use more disk space?

I want to dual boot with Vista 64x and Ubuntu 64x-

I understand from previous posts that I need to shrink  Windows area to make space for Ubuntu using Vistas Partition Manager.
I opened Partition Manager and learned that I have a capacity of 465.76GB of which 269.67GB is free space.

However when I go to shrink the space I am told that the size of available shrink space is only 25282MB.

To my mind that's only 25GB. What happened to the other 240+GB of free space? I was hoping to put Ubuntu onto a fairly substantial section of my HD- say 100GB and use both systems as I need Photoshop, Lightroom etc.

I'm stuck, please help.

John Williams

---

### Post by rsambuca on 2007-10-19
> **johnwillyums said:**
> Will I be able to play my music, videos, photographs in Ubuntu or will I have to copy them and therefore use more disk space?Yes, Ubuntu can read the ntfs drives perfectly, and if you are using the latest version, can read and write by default to ntfs drives.

> **johnwillyums said:**
> However when I go to shrink the space I am told that the size of available shrink space is only 25282MB.

To my mind that's only 25GB. What happened to the other 240+GB of free space? I was hoping to put Ubuntu onto a fairly substantial section of my HD- say 100GB and use both systems as I need Photoshop, Lightroom etc.

I'm stuck, please help.

John Williams

It may be due to pagefiles, hibernation files, or shadow copies.  I suggest defragging the drive 2 or 3 times, and see if that simple fix works.  If it doesn't, make sure you turn off hibernation, and see if that works.  You can find [instructions to turn hibernation on and off here]("http://www.petri.co.il/quickly_enable_or_disable_vista_hibernation.htm").  It can also be due to pagefiles, which you can turn off temporarily through "My Computer, Properties, Advanced..."  somewhere in there.  Then defrag and try shrinking again.

---

