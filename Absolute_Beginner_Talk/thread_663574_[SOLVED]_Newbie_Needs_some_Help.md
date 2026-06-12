---
title: "[SOLVED] Newbie Needs some Help"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by solucki on 2008-01-10
So, I've been wanting to try ubuntu for a while now but not sure which one is best for me.  I have a nice gaming computer(AMD 3500+ 2gb ddram radeon9800 256mb) and love gaming.  So I'm just looking for a OS to do everything else and still keep winXP for games.  Coming from someone who is fed up with windows, I want an OS that blows windows out of the water.  I heard that linux community is one of the best so I wanna know what do you guys think?

---

### Post by dustman on 2008-01-10
i have a laptop, and tried gaming in linux, maybe it's just me, but i say that gaming is not for linux (still :D). You can always have a dual boot on your computer : Ubuntu/Windows (there are a lot of tutorials that show how to make this).

Cheers!

Radu

---

### Post by jonnywombat on 2008-01-10
If your looking for a linux distro that does much everything then IMHO Ubuntu is for you.. Gaming is limited, but your solution of dual booting is the compromise lots of people make.

I started as dual booting and found I used windows less and less, until you find weeks have gone by without booting into windows!! 

Linux does do things a little differently to windows so expect a bit of a learning curve, but there is always loads of help here.

Download and burn a live cd and boot your machine from it.. Have a good play and check to see your hardware is working ok. If you have any issues as a result you can check out the forums before you commit to installing it.If you don't like it the just reboot your machine without the cd and it's gone!! 

Other distros have live cd's also so you can have a play with others too. I have tried several, but always come back to ubuntu..

Hope you find what your looking for and good luck

Jonny

---

### Post by 3rdalbum on 2008-01-10
If you want an operating system that blows Windows out of the water, Linux is what you're looking for.

Gaming for Linux is not too bad if you like deathmatch FPSes, as there are a lot of open-source ones for Linux. But you might encounter troubles with your graphics card - ATI's drivers are pretty dang terrible when it comes to Linux, although they are improving.

I'm not sure where the Radeon 9800 is in the scheme of things, but your best bet would probably be to get an Nvidia card or run with the 2d acceleration on Ubuntu.

But yes, I think Ubuntu would be a good fit for your computer.

---

### Post by NullHead on 2008-01-10
One thing ... you're asking this question on Linux forums. Witch means that every user on here will encourage you to use linux, but If you're looking for something other than ubuntu there is[ PCBSD]("http://www.pcbsd.org/"), but I strongly encourage you use Ubuntu :biggrin:

---

### Post by Therion on 2008-01-10
I could have written that original post myself.  I'm a gamer as well (AMD 4200+ Dual Core, 2GB of Corsair, nVidia 8800) currently doing a Ubuntu/Winx XP dual boot.  The ONLY thing keeping that Windows partition going is Oblivion and F.E.A.R. at this point.  It grinds me, frankly, having to keep that XP partition because I would love to be 100% Windows free.  Unfortunately Linux is just not for those of us who play (certain) mainstream games at this point in time.  Well there is [Cedega]("http://www.transgaming.com/"), and depending on your situation that may or may not free you from needing a Windows partition to game on.  I've been tempted mightily to give it a go.  It could be just the ticket that allows me to kick XP to the curb once and for all.

Does Ubuntu blow WinXP out of the water?  In my estimation, absolutely.  It's certainly NOT Windows so yes, there IS a learning curve, but Ubuntu Linux has proven itself so absolutely superior to Windows in so many ways, and in such important areas, I dream of the day that it will support my games (or that my games will support Linux, whichever).  I can't suggest strongly enough you give it a go.

---

### Post by NullHead on 2008-01-10
OK I used this thread for oblivion and it worked flawlessly [http://ubuntuforums.org/showthread.php?t=349764](http://ubuntuforums.org/showthread.php?t=349764)
Keep in mind that you can use wine to play it (witch is free)

---

### Post by solucki on 2008-01-11
Thanks for all the help.  I have downloaded the live CD of ubuntu and I like it so far. Although I am having trouble accessing my files and my C:/ drive and not sure how to make it a dual boot system when I fully install it.  Is there a way to make it ask me which OS I want to use when I turn the computer on? Should I get a separate drive or just partition my drive?   I have a 180Gb drive with 60% used

---

### Post by nikoPSK on 2008-01-11
I never could find the files in my C;\ drive when I was using the live cd.... :lolflag:

---

### Post by Lostincyberspace on 2008-01-11
> **solucki said:**
> Thanks for all the help.  I have downloaded the live CD of ubuntu and I like it so far. Although I am having trouble accessing my files and my C:/ drive and not sure how to make it a dual boot system when I fully install it.  Is there a way to make it ask me which OS I want to use when I turn the computer on? Should I get a separate drive or just partition my drive?   I have a 180Gb drive with 60% used
You should be able to just install and grub should show it on boot. You could make a 20 gig partition using the Ubuntu install just makes sure you don't make it to big so you don't over write files. a second drive would give you more space though and you never know you might want it in a month or two

---

### Post by eolson on 2008-01-11
One word of CAUTION - Defrag your drive before you install Ubuntu.  Once is good, twice is better.  Windows scatters files all other the place, and you want them contiguous.

Setting up a Dual boot using the live CD is pretty simple.  It's pretty much take all the defaults.  When you reboot, you will be given (I think 10 seconds) to choose which operating system you want to boot.  After the alotted time if you don't pick one, Ubuntu will boot.

---

### Post by jan quark on 2008-01-11
Believe me or not
Ubuntu will change how you think about and how you perceive the digital world
you will see what I mean my friend:cool:

---

### Post by solucki on 2008-01-12
Alright guys, I have installed ubuntu on a separate partition and I still can't access any of my files I had in Windows and I also can't play any sound or video files.  I can't even access the files on the partition I made. What is wrong?

I go to my computer and try to open the C:/ Drive (also, no sign of the other partition that contains windows files)like I would ion windows and it gives me an error message:

"unable to mount Selected Volume"
and when I click more details I get this

error: device /dev/sda1 is not removable

error: could not execute pmount

---

### Post by dustman on 2008-01-12
what version of ubuntu did you install? cause i installed ubuntu gutsy gibbon (7.10) not 2 weeks ago and it mounted my windows partitions automatically. Don't you remember there at that screen when you had to partition your hard drive, did the windows partitions appear or not? now that you installed ubuntu, can you choose the windows partition at the grub loader? To play movies in Ubuntu, you could install mplayer or vlc player, and about the sound i also had trouble getting it working, but i found this post: [http://ubuntuforums.org/showthread.php?t=624002&page=3]("http://ubuntuforums.org/showthread.php?t=624002&page=3"), which solved my problem. 


Cheers!

Radu

---

### Post by ckuka on 2008-01-12
What steps did you go through when installing Ubuntu?  Are you certain you did't write over the windows partition?  If GRUB, the first screen you notice after rebooting, offers "Other Operating Systems" as an option after Ubuntu, are you able to boot into windows and access the files in windows using windows? 
Opening different media should not be wholly related to your problems not accessing dev\sda1. Try using the package manager to install or update a driver and play a file located in your linux partition. 
Good Luck! I hope this helps!

---

### Post by solucki on 2008-01-13
alright so I figured out what was wrong. I got the x86 version and should have had the amd64.  I got the newest amd64 gutsy gibbon version and everything is running better but now I'm having trouble with the flash player. I can't get adobe to work so I installed gnash instead and I can't get a lot of the websites to work right. Is there a different player I could use?

---

### Post by dustman on 2008-01-13
your could try this: [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727) , or this: [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727) . I heard that making flash player work on a x64 computer is kinda tricky, but is doable :)

---

### Post by solucki on 2008-01-13
I have an AMD64, what player can I use?  Adobe doesn't seem to make one for the AMD, I only see one for the x86.

---

### Post by dustman on 2008-01-14
damn i posted the same bloody link twice :redface: There should have been two different links, the other one was this : [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924) . Try the instructions posted by Kilz and you should have flash player on your AMD64.

---

### Post by solucki on 2008-01-14
that fixed it. well, mostly everything except my [pandora]("http://www.pandora.com") radio. I'll search the forums for hint on that but Thanks for everyones help, I am now enjoying my ubuntu experience \\:D/

---

### Post by nikoPSK on 2008-01-14
> **solucki said:**
> that fixed it. well, mostly everything except my [pandora]("http://www.pandora.com") radio. I'll search the forums for hint on that but Thanks for everyones help, I am now enjoying my ubuntu experience \\:D/

please mark this thread as "SOLVED" then.

Best,
nikoPSK

---

### Post by dustman on 2008-01-15
> **solucki said:**
> that fixed it. well, mostly everything except my [pandora]("http://www.pandora.com") radio. I'll search the forums for hint on that but Thanks for everyones help, I am now enjoying my ubuntu experience \\:D/

ubuntu is truly a great operating system. i won't change it for all the gold in the world :D.

Have fun!


Radu

---

