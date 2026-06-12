---
title: "Install new programs on Live CD?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by smoaky on 2006-08-14
Hi there,
Over the last few months I have tried several Linux Distros, and for me at least Ubuntu 6.06 is by far the best and easiest to use.(Freespire,Xandros ties for second) In the past I have only installed one disto onto my HDD as a dual boot,that being Simply Mepis. Sorry but it was too difficult to learn how to install various programs using apt-get,and I lost interest.Well Ubuntu is different,so I thought.... while running the "live cd" I was able to Upgrade Firefox and even install opera 9 browser with little problem.(Could not find Opera on the add/remove programs list and had to go to the opera web site). Keep in mind I am doing all this on the "live cd" just to see how easy installation of programs would be before I install Ubuntu on my hdd. I wanted to install Macromedia Flashplayer and performed all the necessary steps to install as the how-to states here on this link:  [http://www.wiredwriter.net/index.html?page=%20Install%20Flash%20Player](http://www.wiredwriter.net/index.html?page=%20Install%20Flash%20Player)

How to Install Macromedia Flash Player 7 Using apt-get

Now you are ready to install Flash Player.
Click Applications in the overhead Panel. 
Select Accessories. 
Select Terminal. 
When the terminal opens, type sudo apt-get install flashplugin-nonfree. 
NOTE: You will be prompted to enter your password. 

It asked me "are you root"? I tried "y" no good..I tried "yes" nothing.
My question to this long winded post is,can I install programs like Macromedia Flashplayer using the live cd? I know they will be erased after a re-boot but I want to practice installing the programs I want before install on my hdd. If so when it asks if I'm root what would be my response?
I really love this distro and want it to work easily and simply and I want to break away from the Micro$oft Monopoly. Vista..Boo !!  Be prepared for more questions when you reply to this post!!
Thanks

---

### Post by zxee on 2006-08-14
> When the terminal opens, type sudo apt-get install flashplugin-nonfree. 
Did you do that step? iirc in the live cd you can just do sudo without an argument (another command following sudo) and you become root so try that too. Hope that helps.

---

### Post by smoaky on 2006-08-14
Hi zxee,
"When the terminal opens, type sudo apt-get install flashplugin-nonfree."
Yes I performed this step afterwards is when it asked me if I was root. Did'nt know how to proceed afterwards.I will try sudo and (??) what command do you suggest. I will experiment and see what happens. Let me know of any other suggestions. I will re-boot now and run ubuntu and see what I can do. In the meantime thanks for responding and I hope I can get this to work. Win XP is a no brainer but Linux requires a bit of thought...something I'm lacking in...lol  :-]
ttys

---

### Post by smoaky on 2006-08-14
Tried everything. Using Firefox cannot get Pandora music to play. Says I must install additional plug-ins @##@!!(**&&!!!. I give up for now. Anybody can help me using simple language to fix this,pls respond.
For now I'm re-booting to Freespire. At least it has Macromedia already per-loaded!!!!
A frustrated simple-minded Linux wannabe user.

---

### Post by derekguy on 2006-11-24
I tried the command

[INDENT][COLOR="Red"]sudo apt-get install flashplugin-nonfree[/COLOR][/INDENT]

I had no problem with root access but terminal replies:

[INDENT][COLOR="#ff0000"]Reading package lists... Done
Building dependency tree... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate[/COLOR][/INDENT] 

I'm a noob so I'm going to ask it... what should I look for now? I'm looking for the flash plugin for the Opera browser on Dapper live CD. TIA

---

