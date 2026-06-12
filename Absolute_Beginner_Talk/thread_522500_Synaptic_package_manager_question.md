---
title: "Synaptic package manager question"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Indy452 on 2007-08-10
Sorry for not reading fifty miles worth of other posts. I hate to read stuff I don't understand.
With that said. I'm having loads of problems with this Ubuntu version6.06 LTS for PC.
I was not even sure it was totally installed properlly as at first I was not sure what was going on, I have never attempted anything like this before.
I have it set up with the time and passwords and name and all. I was able to connect to the internet with no problems but I realized that I am unable to watch videos etc from youtube.
It says something about not havind java something or another turned on or I need a newer version. I guess that is fine but I don't understand how to install stuff. What does "Extract" mean anyway? I get nowhere when I click and tinker with it. I'm obviously doing something wrong.
Also the question regarding the synaptic package manager is I get a warning window stating that I have 33 broken packages on my system! This can't be normal can it?  When I use the broken filter it says to use I have no clue what to do in there. Can someone help? Or should I just re-install the OS? I also have a Kubuntu 6.06 for pc and a Ubuntu 6.06 for 64bit pc, whatever that means.

Sorry for the long post but I really want to be able to use this instead of windows.

Thanks a million, Neal

---

### Post by overdrank on 2007-08-10
> **Indy452 said:**
> Sorry for not reading fifty miles worth of other posts. I hate to read stuff I don't understand.
With that said. I'm having loads of problems with this Ubuntu version6.06 LTS for PC.
I was not even sure it was totally installed properlly as at first I was not sure what was going on, I have never attempted anything like this before.
I have it set up with the time and passwords and name and all. I was able to connect to the internet with no problems but I realized that I am unable to watch videos etc from youtube.
It says something about not havind java something or another turned on or I need a newer version. I guess that is fine but I don't understand how to install stuff. What does "Extract" mean anyway? I get nowhere when I click and tinker with it. I'm obviously doing something wrong.
Also the question regarding the synaptic package manager is I get a warning window stating that I have 33 broken packages on my system! This can't be normal can it?  When I use the broken filter it says to use I have no clue what to do in there. Can someone help? Or should I just re-install the OS? I also have a Kubuntu 6.06 for pc and a Ubuntu 6.06 for 64bit pc, whatever that means.

Sorry for the long post but I really want to be able to use this instead of windows.

Thanks a million, Neal

HI if you have broken packages in synaptic then you need to repair them. You can do this by  opening synaptic manager and under edit there is a option to fix broken packages. Once that is done then you need to reload button and you should be ready to go. Also you said you don't like to read things you don't understand then how will you understand if you don't read. :(

---

### Post by lemmy999 on 2007-08-10
Neal

lets take this slowly. You've installed 6.06 and you have a number of "issues"

Lets start from the top. > but I realized that I am unable to watch videos etc from youtube.

Have you tried "youtube" as a search here? 

I think that maybe you need to do some more research before you start shouting about things not working. Linux is not Windows ( thank allah) I would respectfully suggest that you try a good guide to Ubuntu and then ask questions here. 

Can I recommend Aysiu's excellent guide to everything Linux at [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

The forum here is THE best computer based forum I have ever known. It will help you, and the other members, if you break your questions down into smaller bits.

You have made the right decision. Patience and perseverance will get you what you want! Please don't make the mistake of thinking that Ubuntu is just Windows with a brown coat on!

---

### Post by Indy452 on 2007-08-10
I'm sorry if I have come off as "shouting" about things not working.  I think that I'm feeling some frustration right now.
Several people have sold me on this install and I'm not that computer literate (obviously).
I was also told that if I had any problems this community is the place to turn as I village basically blew me off.

Overdrank, I guess I don't really know what to do with the packages. I can see that there are way more than thirty three. Some have green boxes filled in and most are blank. What should I do here?

Lemmy999, thanks for the link, I will certainly check it out. I also realize that Ubuntu is not windows with a brown coat but I need to start somewhere right?

Thanks, Neal

---

### Post by overdrank on 2007-08-10
> **Indy452 said:**
> I'm sorry if I have come off as "shouting" about things not working.  I think that I'm feeling some frustration right now.
Several people have sold me on this install and I'm not that computer literate (obviously).
I was also told that if I had any problems this community is the place to turn as I village basically blew me off.

Overdrank, I guess I don't really know what to do with the packages. I can see that there are way more than thirty three. Some have green boxes filled in and most are blank. What should I do here?

Lemmy999, thanks for the link, I will certainly check it out. I also realize that Ubuntu is not windows with a brown coat but I need to start somewhere right?

Thanks, Neal

Hi the one's highlighted in green are packages installed not broken. DO as I stated in the previous post and synaptic with find and fix the broken packages. Then be sure to reload by clicking the reload button.

---

### Post by Paul133 on 2007-08-10
Do you have Flash installed? 

Go to Synaptic package manager and search for "flash". You should find "flashplugin-nonfree". The box to the left of it will be greened if it's install, and white otherwise. If it's not green, click it. A menu will pop up. Mark it for installation and then click apply (the green checkmark at the top). 

Another way to do all that is to bring up a terminal and type ```
sudo aptitude install flashplugin-nonfree
```

Finally, after you install flash, restart firefox (or whatever browser you use). Good luck.

---

### Post by lemmy999 on 2007-08-10
I guess that what I am saying is "take it slowly" . try and isolate each problem and post as much information as you can in a human readable format.

This is a great OS and will get even better. If you can't dual boot :( ( I can't sympathize with you that much but you have paid the licence fee for Windows and being unable to use it is wrong IMHO) then I guess that you will get to grips with this OS.

Once again- persevere- This is a great OS!

---

### Post by r4ik on 2007-08-10
The synaptic question seems to be answered just some info if you're interested.

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

Good luck !

---

### Post by link141 on 2007-08-10
> **Indy452]I was not even sure it was totally installed properlly as at first I was not sure what was going on, I have never attempted anything like this before.
 I have it set up with the time and passwords and name and all.

(SNIP)

 Also the question regarding the synaptic package manager is I get a warning window stating that I have 33 broken packages on my system! This can't be normal can it? When I use the broken filter it says to use I have no clue what to do in there.[/quote]
You might have a messed up install CD, where some of the data is missing.  It usually should complain if it's bad enough, but you can always check if the install CD is OK by booting into it, and choosing "Check CD" instead of "start/install Ubuntu".  

It is more likely that you have package version mismatches though...  

**Here's how to fix it:  Open a terminal- press ALT F2 and type-in gnome-terminal or select it from the list.  Update your package information by typing "sudo apt-get update" (without quotes) and pressing enter.  Then type "sudo apt-get autoremove --fix-broken" (again, without quotes).  Make sure Synaptic isn't open when you do this, or Apt won't be allowed to perform the command.  This should take care of the broken packages, but might not if it's really bad.  If this doesn't, then tell us in a new post, and maybe someone with more experience than me can help you said:**
> I was able to connect to the internet with no problems but I realized that I am unable to watch videos etc from youtube.
 It says something about not havind java something or another turned on or I need a newer version. I guess that is fine but I don't understand how to install stuff.
You can't watch videos because flash isn't installed Out-of-the-box for legal reasons.  The Javascript message was just what gets displayed if Flash isn't running the video.  I guess you figured this, and that's why you want to know how to install stuff...  

**To fix your Flash problem, quite simply, install it by doing the following:  Add the universe repositories by following the instructions on this page: [Adding extra repositories.](https://help.ubuntu.com/7.04/add-applications/C/extra-repositories-adding.html)
Update your package information if you haven't already, either by clicking the update button in Synaptic, or by using the same command mentioned earlier in a terminal.  Then install the package "flashplugin-nonfree" (again, without quotes) either with synaptic, or by typing in a terminal "sudo apt-get install flashplugin-nonfree".  Restart firefox, and enjoy :popcorn:.

[quote=Indy452]What does "Extract" mean anyway?[/quote]
Let me guess, you downloaded the flash-plugin installer from Adobe, and it was in tar.bz2 file?  Files are commonly compressed to save space on internet servers, so "extracting" applies to decompressing a file(s) when it's in a compressed archive.

Sorry I wrote so much, but there's your solutions.  Just take your adjustment to this new OS slowly and patiently, and you'll grow to like it a lot ;).  I was fried (really, really, tired) when I wrote this, so it's probably badly organized, and hard to follow, and I may have missed some stuff...

---

### Post by Indy452 on 2007-08-12
Well I thought I'd check in with everyone. Unfortunatelly I'm at my computer from work because I somehow managed to totally screw up my computer at home so I'm S.O.L right now.

I must have done something wrong in the install and now my computer can not get past the boot up screen that tells you how many Mhz etc.
It is stuck on some error that says Grub loading... please wait, next line it says Grub error 15 and its frozen from that point on.

Is there some kind of command I can try to get this thing going again? I've crashed it, I've unplugged it ,  I have tried booting up with an Ubuntu CD but nothing different  happens. ( I was using 6.06 but I recently acuired the 7.04 version of feisty fawn that I have not been able to use)
Maybe I need to get into the system setting, you know the screen right before the one that freezes up on me that tells you to press the delete key. Maybe something in there is a fowl?

I'll leave this post out here for a few hours and I'll check it later this P.M. 

Thanks to all,  Neal

---

### Post by ridgeland on 2007-08-12
deleted

---

### Post by sailor2001 on 2007-08-12
since you haven't posted any info about your pc, I'm going to make the assumption you have less than 256mb ram...and maybe 32 rather than 64 dual core and you have downloaded a standard gui 64.........and maybe even burned your disk as a file rather than an image.  so to start you right.: Download the 7.04 as an iso image and burn to disk as such as a very slow speed. If you have low ram, download as an "alternate iso image"....this will install at a low ram.....above all, take a few minutes and read Pycocats tutorial.....as linked before

---

