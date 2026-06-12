---
title: "Im new to linux need alot of help"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by slammer25 on 2006-01-01
im trying to run a live cd i cant get it to work at all.im a windows xp user dont know anything about programming can somebody help me get started with this i have a laptop toshiba satellite m55-s139 if you need any thing else let me know ill do my best

---

### Post by Gray. on 2006-01-01
Make sure that your laptop is set to boot from CD before the Hard Drive.

---

### Post by kaamos on 2006-01-01
Hello, and welcome to the forums!

You will need to be more specific about your problem. When do things start going wrong, do you see and error message (what is it)? It will be a lot easier to help you with this info.

---

### Post by slammer25 on 2006-01-01
im not seeing anything at all cant get it to boot up dont know how to make sure my cd drive is set to bootup

---

### Post by Jukey on 2006-01-01
you will have to go into BIOS. when you first boot press F2 to get into the bios. there will be some sort of setting that allows you to change boot order. make note of it so you can change it back. set CD as the first one. then restart (usually by pressing F10) and insert the CD. if you boot into windows restart and make sure the CD is in. you should start the live CD

---

### Post by slammer25 on 2006-01-01
ok ill try that and let you know thanks

---

### Post by slammer25 on 2006-01-01
ok i changed the bootup to cd first then i put the disk in and got an a:> dont know what to put in there

---

### Post by tim15856 on 2006-01-01
It's still not booting on the CD. Is this an original live CD, or did you burn it? Does the live-CD work in another system?

---

### Post by slammer25 on 2006-01-01
i burnt the cd not sure if its right im downloading it again ill try to burn the iso file again im using cdburnnerxp pro 3 to burn with

---

### Post by Madpilot on 2006-01-02
ISOs need to be burnt differently from regular data CDs for them to work - have a look at [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto), which includes Windows information.

---

### Post by slammer25 on 2006-01-02
i tried to burn another cd still doesnt work i wish icould find someone close to me that could help

---

### Post by Sef on 2006-01-02
Did you do an MD5Sum to check the download is correct?

---

### Post by slammer25 on 2006-01-02
no

---

### Post by slammer25 on 2006-01-02
ok i got the cd to burn right now when it tries to startup it says Failed to start Xserver any ideas of what to do?

---

### Post by mitdxiw on 2006-01-02
When you look at the CD in windows, you should see a bunch of files and directories when you try to explore it, say, in 'my computer'. If you see just the one file ending in .iso you did not burn it correctly. Also, if you have autorun enabled, you should see a program load in windows when you put the cd in (its a window showing some of the features of the live CD). Make sure in your CD burning software that you are burning from an image and NOT a data disk. If you are drag and dropping the file onto the CD, you are not burning it right.

Assuming you have burnt it correctly, and you have changed the CD-ROM to be before the Hard Disk in the boot order in BIOS, it should boot into linux from the cd.

---

### Post by Mustard on 2006-01-02
[QUOTE=slammer25]ok i got the cd to burn right now when it tries to startup it says Failed to start Xserver any ideas of what to do?[/QUOTE]

What type of graphics card to you have?

---

### Post by diggs on 2006-01-02
I can honestly say that installing ubuntu on my laptop and desktop was one of the hardest and most challenging things I have ever done. I am glad that I stuck to it, but after the 6th install, 100th install attempt, the 2 hours I spent trying to play an mp3 file, trying to install programs and so on was at times really frustrating....hopefully things will only get better, but ubuntu really did it's best to ensure I wanted to stick to windows 4eva!

---

### Post by slammer25 on 2006-01-02
vid card is ATI Radeon xpress 200m

---

### Post by Mustard on 2006-01-02
[QUOTE=diggs]I can honestly say that installing ubuntu on my laptop and desktop was one of the hardest and most challenging things I have ever done. I am glad that I stuck to it, but after the 6th install, 100th install attempt, the 2 hours I spent trying to play an mp3 file, trying to install programs and so on was at times really frustrating....hopefully things will only get better, but ubuntu really did it's best to ensure I wanted to stick to windows 4eva![/QUOTE]

Ubuntu has an IRC support channel that has a lot of friendly volunteers that can assist you with getting some of the basics working on your system.  The X-Chat irc client is set up by default in Ubuntu, and if you choose the Ubuntu servers from the server list in will take you straight to #ubuntu on the irc.freenode.net server.  That's where I really started to learn things quickly with Ubuntu.  They have a bot in channel that allows people to quickly show you where different HOW TO's can be found, and the volunteers in the channel will be able to help you over the hurdles you strike in understanding the terminology and methods of using linux.

I agree it can be a troublesome process at times depending on your hardware setup and the type of things you use your computer for.   I've really enjoyed the whole process though in the end.  It did take me at least two months to learn the basics, as its quite different to how Windows works.

One trip to my brothers and watching my nephews computer get fubared by  trojans and viruses at a malicious website was a great reminder of one of the reasons I like using linux.  Security and freedom from viruses, trojans and spyware.

Along with this I have a vast repository of software to draw from in the ubuntu repositories that allows for easy installation and regular updates that keep my system secure and up to date.

I'm sorry to hear your journey has been dissapointing. :)  The advice I have for all those who get frustrated is 'use whatever works for you'.  Thats the most important thing.  If its not doing what you want it to do, then its not for you.  Ubuntu is definitely working for me.  I'll never be looking back.

---

### Post by Mustard on 2006-01-02
[QUOTE=slammer25]vid card is ATI Radeon xpress 200m[/QUOTE]

Hmm..well I know that ATI cards can be problematic due a general lack of support for linux from ATI.  I've never used ubuntu extensively on a liveCD, opting to go straight to the install process.  I know that for display problems on an ubuntu install, you can do this command...

```
sudo dpkg-reconfigure xserver-xorg
```

You would then choose the default options for all the choices you don't know the answer to and this should reconfigure the display.  I don't know whether this will work on a liveCD.  If you can't get the ATI card to work, you may need to configure X to use the VESA drivers.

---

### Post by diggs on 2006-01-02
[QUOTE=Mustard]Ubuntu has an IRC support channel that has a lot of friendly volunteers that can assist you with getting some of the basics working on your system.  The X-Chat irc client is set up by default in Ubuntu, and if you choose the Ubuntu servers from the server list in will take you straight to #ubuntu on the irc.freenode.net server.  That's where I really started to learn things quickly with Ubuntu.  They have a bot in channel that allows people to quickly show you where different HOW TO's can be found, and the volunteers in the channel will be able to help you over the hurdles you strike in understanding the terminology and methods of using linux.

I agree it can be a troublesome process at times depending on your hardware setup and the type of things you use your computer for.   I've really enjoyed the whole process though in the end.  It did take me at least two months to learn the basics, as its quite different to how Windows works.

One trip to my brothers and watching my nephews computer get fubared by  trojans and viruses at a malicious website was a great reminder of one of the reasons I like using linux.  Security and freedom from viruses, trojans and spyware.

Along with this I have a vast repository of software to draw from in the ubuntu repositories that allows for easy installation and regular updates that keep my system secure and up to date.

I'm sorry to hear your journey has been dissapointing. :)  The advice I have for all those who get frustrated is 'use whatever works for you'.  Thats the most important thing.  If its not doing what you want it to do, then its not for you.  Ubuntu is definitely working for me.  I'll never be looking back.[/QUOTE]

Yeah, I agree with most of your points. I am just used to plugging in a disk and going. One thing that I didn't take into account is that I needed to adjust my way of thinking and how to go about doing things. I was really hoping for an easy solution to windows, which is way too big brother for me. A change of approach and things are going a lot better now. 

One of my biggest hesitations was this: gentoo fedora ubuntu red hat breezy badger hoary and all these cutsey pie names that you guys use. That and just browsing these forums. Even the most basic things seem to cause a lot of grief! such basic, easy things in windows warrant such lenghty discussions. another thing that worried me is when you guys just post code and expect someone to know what to do with it! and that code is really odd, coming from a dos environment, IMO.

Anyways, I am glad I made the switch, look forward to using linux in the years to come. When I get home I will figure out how to acess my partition on my 250 gig HD, something I can do no prob in XP, but ubuntu on the other hand....ah well!

---

### Post by meborc on 2006-01-02
[QUOTE=Mustard]Ubuntu has an IRC support channel that has a lot of friendly volunteers that can assist you with getting some of the basics working on your system.  The X-Chat irc client is set up by default in Ubuntu, and if you choose the Ubuntu servers from the server list in will take you straight to #ubuntu on the irc.freenode.net server.  That's where I really started to learn things quickly with Ubuntu.  They have a bot in channel that allows people to quickly show you where different HOW TO's can be found, and the volunteers in the channel will be able to help you over the hurdles you strike in understanding the terminology and methods of using linux.

I agree it can be a troublesome process at times depending on your hardware setup and the type of things you use your computer for.   I've really enjoyed the whole process though in the end.  It did take me at least two months to learn the basics, as its quite different to how Windows works.

One trip to my brothers and watching my nephews computer get fubared by  trojans and viruses at a malicious website was a great reminder of one of the reasons I like using linux.  Security and freedom from viruses, trojans and spyware.

Along with this I have a vast repository of software to draw from in the ubuntu repositories that allows for easy installation and regular updates that keep my system secure and up to date.

I'm sorry to hear your journey has been dissapointing. :)  The advice I have for all those who get frustrated is 'use whatever works for you'.  Thats the most important thing.  If its not doing what you want it to do, then its not for you.  Ubuntu is definitely working for me.  I'll never be looking back.[/QUOTE]
i am truly inspired... it was quite painless for me to switch from xp to breezy but i still needed a lot of help... now i have been using ubuntu for 3 months and already know how to solve some simple problems... heck - i just a minute ago was searching for a terminal in university xp box to fix a prob with software... :D

> Anyways, I am glad I made the switch, look forward to using linux in the years to come. When I get home I will figure out how to acess my partition on my 250 gig HD, something I can do no prob in XP, but ubuntu on the other hand....ah well!
try this dual boot how to... it also explains how to mount partitions... this site helped me alot [users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by diggs on 2006-01-02
^^thanks, I already have the dual boot down on my desktop, just need to get acess to those partitions now. then I will be happy. That site really helped me out.

Dual boot I have decided is impossible on my laptop. it just won't work. After installing XP a good 6 times, and about 20 failed installs under ubuntu, I just said **** it and dumped ubuntu onto my laptop, and here I am. Even that was a real bitch, but last night after the new year's celebrations I had a head full of mushrooms and figured I was in a good frame of mind, and after only 4 tries I got it installed. anyways...moving forward, I think it will be a good time, eh!

---

### Post by slammer25 on 2006-01-02
well i decided to just install and now when it get finished i get a prompt dont know what to do next i hope i did everything right gotta go to bed talk to everyone later thanks for the help

---

### Post by Mustard on 2006-01-02
[QUOTE=slammer25]well i decided to just install and now when it get finished i get a prompt dont know what to do next i hope i did everything right gotta go to bed talk to everyone later thanks for the help[/QUOTE]

Cya tomorrow, slammer25.  

Keep pluggin away and asking for advice.  Describe the processes you have gone through and be fairly elaborate in describing the exact errors that occur.

Describe the prompt you see and what stage of the installation this prompt appeared at.  Someone will be able to give you an indication of where to go from there.  As I said earlier, your hardware is troublesome, so its not going to be a smooth ride. :)

---

### Post by slammer25 on 2006-01-02
ok im back in here for a little while i can get to the part after it loads up then get a prompt and i dont know what to type in can anyone help

---

### Post by carlosqueso on 2006-01-02
did you do a server or a complete install?  Also, what does the prompt say?

---

### Post by slammer25 on 2006-01-02
i did a complete install its the computers name and then :~S i think

---

### Post by carlosqueso on 2006-01-02
What does it say if you type "startx" without the quotes? this will tell us 
(hopefully) what the problem is....

---

### Post by slammer25 on 2006-01-02
it says it cant create temp file not enough space left when i type in startx

---

### Post by Mustard on 2006-01-02
hmmmm...is it possible its run out of space for the installation on your hard drive?

---

### Post by slammer25 on 2006-01-02
i doubt it it had 31GB in the partition and 2GB in the swap

---

### Post by jackdirt on 2006-02-03
Sorry I don't want to highjack this thread, but let me explain quickly.

I installed ubuntu on my desktop not too long ago loved it but hated the lack of support any way I put my desktop back to winblows. Moving on

I just got this same laptop and am encoutnering the same exact xserver problem 

However I found that when in the terminal

sudo dpkg-reconfigure xserver-xorg

setting up default drivers at least got me a menu with 640 x480 resolution.
So I can say it does work, just need to get regular drivers to work. Once I get this going I plan on doing all my personal design/ artwork using Linux apps. I was just so impressed with the community and the greatness of this OS I can't quit. 

What I am saying is keep trying and don't give up it is worth it!

---

