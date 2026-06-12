---
title: "Preparations before installing Ubuntu"
date: 2005-09-03
forum: Absolute Beginner Talk
---

### Post by tedwoo on 2005-09-03
[COLOR=sandybrown]**Hello, I'm one of many who are new to Ubuntu here, and I thought I might start another thread :D**[/COLOR]

I'm on the edge of switching to Ubuntu right now, but I still have a few questions that I need to sort out before I take "the big jump".

I've been getting help on another forum with these questions and they are already somewhat solved, but I'm still not really sure. Here they are:

[SIZE=3]**1.**[/SIZE] The question that I see many have asked here, as far as I understand dualbooting with windows and ubuntu is possible but tricky, and I hear about Grub which I belive is a bootoption thingy for selecting windows or ubuntu when booting, is this so?

[SIZE=3]**2.**[/SIZE] If now dualbooting is possible, which is the easiest way to do it? Is it by having two separate harddrives? Because I have one drive with windows on right now, but I want to keep it just in case everything screws up(which I don't really belive) and I have some stuff on it that I'd like to keep so formatting is not an option there really.

[SIZE=3]**3.**[/SIZE] My third question is about gaming, If im suppose to use Ubuntu, and skip windows totally, I need to be able to play games, so, which are the best options here? With the help on the other forum, I've found out(or been told anyway) that Cedegea is the best for gaming, but that gets me two more questions; 

[SIZE=3]**3.1.**[/SIZE] I have an **ATI Radeon 9500pro card**, Do I need to install the drivers for linux or windows if I'm going to use Cedegea for gaming? I don't understand how that works, maby if I had it in front of me but I'd like to get things solved before I get my hands dirty ;-). 

[SIZE=3]**3.2.**[/SIZE] And with Cedegea, If it is as I think it is, is it possible to run games in fullscreen mode?(this I take for granted but I just want to be sure.. :D) Is there a preformace loss of any kind, like lower fps or graphic corruption or something etc. etc.? 

[SIZE=3]**3.3.**[/SIZE] And the last question in this subject(I promise! :D) the drivers for my ATI Card, are they any diffrent from the Windoze Drivers? (like lower fps etc.)

[SIZE=3]**4.**[/SIZE] I'm far from a pro, and it's only a hobby of mine, but I make music in a program called [Reason 3.0](http://www.propellerheads.se), will I be able to use this? As far as im concern, I can't use this with linux so I need an emulator for it, and I belive I need Wine(cedegea?) for that, and there I have the same question, will there be a performace drop?

There, that should be all for now(must stop myself before this becomes a book ;)), Answers are welcome! Thank you in advance!  :grin:

---

### Post by TristanMike on 2005-09-03
Pre-Welcome to the wonderful world of Ubuntu. I will try and shed some light on some of your questions.

**1.** Dual Boot - A large number of people, I would say, do this(if not triple and quadruple boot  :shock: ). It can be "tricky" as you put it, mostly in my experience, because it was new and no fancy G(raphical) U(ser) I(nterface), but very simple and powerful. It will let you partition, format into filesystems, among other things. Very nice. Check these two places for a preview of things to come...he he. [http://mrbass.org/linux/ubuntu/install/](http://mrbass.org/linux/ubuntu/install/)  and [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html). Grub is the way to go and yes it is the thingy for choosing between Ubuntu and other OS's.

**2.** You can have two seperate or one single. It's up to you really. I suppose if you have it, why not 2. Anyway, the general practice is to install Windows first, then Ubuntu. And usually creating a seperate FAT32 partition/drive is also recommended(if using XP and Ubuntu). This is because Ubuntu cannot write to NTFS but both OS's can read/write to FAT32 with no problems. 

Maybe you might want to think about using 1 drive for both XP and Ubuntu, and use the spare drive for shared files. In which case you would either reinstall everything from scratch(which is not an option), or just resize your XP partition. You don't have to though, everything would still be fine if you kept Ubuntu and the "shared" on the same drive and XP on a different one. That's just how I would do it if I had a second drive :(

**3.** Ahh, gaming. First have a look at the Uber-List here [http://www.ubuntuforums.org/showthread.php?t=5153](http://www.ubuntuforums.org/showthread.php?t=5153) Second, to play 99% of commerical Windows games, you need the use of an emulator. Cedega, is a very popular Windows emulator, however it costs money for updates and such ($5.00/mo. i think) but there is Wine, from which Cedega evolved, and it is free and included in the Ubuntu repository. 

Either way, you will need a Windows Emulator to play Windows native games (or applications for that matter) under Ubuntu/Linux, which I'm sad to say, is most. But again, check out the list for an idea of what's out there, though I'm sure there must be more. I don't really use Wine or Cedega as the games under Linux have been keeping me entertained. If it is a huge problem, or you wanna ease you way into it, keep XP, just for games or those very special programs that are close to your heart.

**3.1** Well, it's ATI, that's not bad, but then again, it's not great either. I say this, because there apparently is poor support from ATI for linux, however, have no fear, it still works, and if there is a problem there are plenty of ATI related threads ie. [http://www.ubuntuforums.org/showthread.php?t=22496&highlight=ATI+9500](http://www.ubuntuforums.org/showthread.php?t=22496&highlight=ATI+9500) where  you can hopefully solve any problem you might have. Usually once everything is up and running correctly, the performance equals or surpasses Windows.
[B]
3.2[/B] I don't know, I don't use a Windows emulator. Sorry :)
[B]
3.3[/B] See 3.1

**4.** Well, as for "Reason", I checked, and it doesn't seem to support Linux so you have a few choices. A) Use Wine or Cedega and try installing it there. B) Find a suitable replacement in Linux, there are usually very comprable Linux versions of your favorite programs/games (here shows some those comprable versions [http://www.ubuntuforums.org/showthread.php?t=33183)](http://www.ubuntuforums.org/showthread.php?t=33183)). C) Just keep the XP partition/drive for your favorite programs until you 1) get tired of Windows 2) Find a suitable replacement 3) get tired of Ubuntu....I shudder at the thought.  :razz: 

Well, there ya go, not the best in the world, but I hope it answered some questions. I'm no pro either, heck I wouldn't even call myself Intermediate, more like somewhere between Absolute Begginer and Intermediate, but Ubuntu is a pretty unbelieveable OS and very exciting. I still keep Windows around for a "Just In Case" but I don't use it. Perhaps my next step is to learn Wine or Cedega so I can just free up the space for Linux. :)

---

### Post by tedwoo on 2005-09-03
oh my.. Thank you so much, I was expecting "search the forums" answer but you got em' all! :grin:  almost anyway, the emulator questions still remains, anyone else out there who are good with that?

Cheers :D

---

### Post by davmac on 2005-09-03
I'm a big fan of Reason. I've had very little success with audio stuff within Ubuntu nor with Reason or Cubase within wine. If you're interested in Audio on linux I'd strongly recommend checking out Agnula/DeMuDi. As far as I can tell - state of the art linux audio distribution.

I've ended up with a triple boot solution; WinXP for Cubase and Reason, Agnula for all the rest of the audio work and then Ubuntu for everything else.

---

### Post by Mustard on 2005-09-03
[QUOTE=tedwoo]oh my.. Thank you so much, I was expecting "search the forums" answer but you got em' all! :grin:  almost anyway, the emulator questions still remains, anyone else out there who are good with that?

Cheers :D[/QUOTE]

I think without even answering the emulator questions it seems to me you need at least a dual boot XP/Ubuntu system using GRUB to switch between operating systems and a FAT32 partition for sharing files. You will probably spend most of your gaming time on XP and your 'productive' time on Ubuntu.  I find it helps keep the two from merging into one. :)

Starting with a dual boot system gives you a chance to ease into the installation of Ubuntu too.  You can take the time to study the different issues you might face with your particular hardware setup, while still maintaining a fully functional computer.

---

### Post by tedwoo on 2005-09-03
> **davmac]I'm a big fan of Reason. I've had very little success with audio stuff within Ubuntu nor with Reason or Cubase within wine. If you're interested in Audio on linux I'd strongly recommend checking out Agnula/DeMuDi. As far as I can tell - state of the art linux audio distribution.

I've ended up with a triple boot solution said:**
> 
Got some links for Agnula/DeMuDi?
[QUOTE=Mustard]I think without even answering the emulator questions it seems to me you need at least a dual boot XP/Ubuntu system using GRUB to switch between operating systems and a FAT32 partition for sharing files. You will probably spend most of your gaming time on XP and your 'productive' time on Ubuntu.  I find it helps keep the two from merging into one. :)

Starting with a dual boot system gives you a chance to ease into the installation of Ubuntu too.  You can take the time to study the different issues you might face with your particular hardware setup, while still maintaining a fully functional computer.
 ](*,) 
This is kind of what make's me sad about linux.. Anyway, isn't there some dist that makes these kind of things work? The thing is that I want to get rid of xp, I'm so sick of it.. :sad: ... *sigh*

---

### Post by TristanMike on 2005-09-03
[QUOTE=tedwoo]Got some links for Agnula/DeMuDi?[/QUOTE]A quick search in google with "Agnula/DeMuDi" as my query retrieved this....[http://www.agnula.org/](http://www.agnula.org/) You should really make Google your best friend. :)

[QUOTE=tedwoo]This is kind of what make's me sad about linux.. Anyway, isn't there some dist that makes these kind of things work? The thing is that I want to get rid of xp, I'm so sick of it.. :sad: ... *sigh*[/QUOTE]What "kind of things" do you mean? If you mean "make my windows programs work", then Wine/Cedega and/or dual booting are you only real options(If I'm wrong, please correct me guys/gals). If you want to get rid of Windows completely for what ever reason, then I would suggest you plug you nose and jump in, the water is fine once you dunk your head. Otherwise, you can just reinstall everything, start fresh, install XP with minimal space, like 10GB or so, give or take, install the couple of programs you like, and leave the rest for Linux (and maybe a small FAT partition). But in the end Windows is Windows and Linux is Linux, two different OS's with similar capabilities.

Whatever your choice, good luck.

---

### Post by tedwoo on 2005-09-03
[QUOTE=TristanMike]A quick search in google with "Agnula/DeMuDi" as my query retrieved this....[http://www.agnula.org/](http://www.agnula.org/) You should really make Google your best friend. :)[/QUOTE]
LoL, that was really lazy of me, sorry :D
Thanx though :D
[QUOTE=TristanMike]
What "kind of things" do you mean? If you mean "make my windows programs work", then Wine/Cedega and/or dual booting are you only real options(If I'm wrong, please correct me guys/gals). If you want to get rid of Windows completely for what ever reason, then I would suggest you plug you nose and jump in, the water is fine once you dunk your head. Otherwise, you can just reinstall everything, start fresh, install XP with minimal space, like 10GB or so, give or take, install the couple of programs you like, and leave the rest for Linux (and maybe a small FAT partition). But in the end Windows is Windows and Linux is Linux, two different OS's with similar capabilities.

Whatever your choice, good luck.[/QUOTE]

I do not care about my regular windows programs, as more than half of them are either under GPL or free in some way(and available for linux aswell or replacable) so that isn't really the problem. But I'm still determined that I only want to use 1 OS. 
Do you know if dists like Linspire are any good? Because that could be an alternative. But I haven't heard any good about it really. Though I read today that it is possible to get it for free, but I wonder how free it really is[with upgrades and such]...

---

### Post by TristanMike on 2005-09-03
Please, somebody correct me if I am missing the point but no program or game or any software that is designed for Windows will work in Linux unless 1) Use Emulator 2) It has a naitive installer or patch of some sort.

Each distro I'm sure has it's strengths and it's weaknesses. Just like Windows has its own. Ubuntu has been getting alot of recognition, I enjoy it emmensly it serves my needs quite well. But no Linux distro will be able to support Windows software without the above prerequisites, but then again, neither will Mac, unless, it specifically has a naitive installer or a patch of some kind. I hope this clarifies, if this was you question.

---

### Post by tedwoo on 2005-09-04
anyway, I'm downloading Linspire now as torrent, now that it's "free" just to try it out. Might get back to ubuntu someday.. :(

---

### Post by Knyven on 2005-09-04
[QUOTE=tedwoo]anyway, I'm downloading Linspire now as torrent, now that it's "free" just to try it out. Might get back to ubuntu someday.. :([/QUOTE]

Is linspire really free? i might be mistaken, it is the first distro i used, i thought it was free but they only give the live CD free not the install CD, so how was it?

---

### Post by tedwoo on 2005-09-04
[QUOTE=Knyven]Is linspire really free? i might be mistaken, it is the first distro i used, i thought it was free but they only give the live CD free not the install CD, so how was it?[/QUOTE]

I don't really know, it's rather confusing as said [here](http://freespire.jasp.com/).

As far as I understand this, Freespire is not free but Linspire is free for a [COLOR=Orange]limited time[/COLOR], but [COLOR=DeepSkyBlue]Squiggle[/COLOR], which seem to be based on Linspire [COLOR=DeepSkyBlue]is[/COLOR] [COLOR=Lime]free[/COLOR].

But I'm still a bit confused.  :confused:

---

### Post by xequence on 2005-09-04
> **tedwoo][COLOR=sandybrown]**Hello, I'm one of many who are new to Ubuntu here, and I thought I might start another thread :D**[/COLOR]

I'm on the edge of switching to Ubuntu right now, but I still have a few questions that I need to sort out before I take "the big jump".

I've been getting help on another forum with these questions and they are already somewhat solved, but I'm still not really sure. Here they are:

[SIZE=3]**1.**[/SIZE] The question that I see many have asked here, as far as I understand dualbooting with windows and ubuntu is possible but tricky, and I hear about Grub which I belive is a bootoption thingy for selecting windows or ubuntu when booting, is this so?

[SIZE=3]**2.**[/SIZE] If now dualbooting is possible, which is the easiest way to do it? Is it by having two separate harddrives? Because I have one drive with windows on right now, but I want to keep it just in case everything screws up(which I don't really belive) and I have some stuff on it that I'd like to keep so formatting is not an option there really.

[SIZE=3]**3.**[/SIZE] My third question is about gaming, If im suppose to use Ubuntu, and skip windows totally, I need to be able to play games, so, which are the best options here? With the help on the other forum, I've found out(or been told anyway) that Cedegea is the best for gaming, but that gets me two more questions said:**
> **3.1.**[/SIZE] I have an **ATI Radeon 9500pro card**, Do I need to install the drivers for linux or windows if I'm going to use Cedegea for gaming? I don't understand how that works, maby if I had it in front of me but I'd like to get things solved before I get my hands dirty ;-). 

[SIZE=3]**3.2.**[/SIZE] And with Cedegea, If it is as I think it is, is it possible to run games in fullscreen mode?(this I take for granted but I just want to be sure.. :D) Is there a preformace loss of any kind, like lower fps or graphic corruption or something etc. etc.? 

[SIZE=3]**3.3.**[/SIZE] And the last question in this subject(I promise! :D) the drivers for my ATI Card, are they any diffrent from the Windoze Drivers? (like lower fps etc.)

[SIZE=3]**4.**[/SIZE] I'm far from a pro, and it's only a hobby of mine, but I make music in a program called [Reason 3.0](http://www.propellerheads.se), will I be able to use this? As far as im concern, I can't use this with linux so I need an emulator for it, and I belive I need Wine(cedegea?) for that, and there I have the same question, will there be a performace drop?

There, that should be all for now(must stop myself before this becomes a book ;)), Answers are welcome! Thank you in advance!  :grin:


1. Dualbooting is very easy. After you install ubuntu it will install grub which will let you have a choice of operating systems when you start your computer.

2. You divide the hard drive into partitions, which is like dividing one hard drive into two. Or more if you like.

3. YOu can use Cedega, but you need to pay. Its 15$ for a download and three months of updates. You can still use it after that. YOu can probably download it from P2P somewhere anyway. I have heard it doesent slow down gameplay very much, if any. I havnt got it to work very well, I installed it on another linux OS and it froze on two microsoft games. BUt it might very well work on ubuntu.

3.1, 3.2, 3.3 - I have no experience with drivers on linux, everything automatically worked great for me.

4 - Many programs work in Wine (which is free). It isnt an emulator though it says on its website. It says it uses its own non microsoft code to do everything. Cedega is a different version of wine made by different people. It is one of the few programs that cost money in the linux world. It is supposed to be good with games...

I have gotten wine to work on MS Notepad and some other little things in windows... I have also got it to install google talk (which is only for windows) but I cant run it for some reason. (YOu can go on google talk with another program included with ubuntu...) I have also gotten photofiltre to work (its a free art program). Paint shop pro 7 didnt work however.

---

### Post by tedwoo on 2005-09-04
Thank you for your reply xequence.

I'm still torn apart though, but I might have 1 solution though:

I keep my old drive keeping windows as it is then I buy another drive, make like 3 partitions or something, install Ubuntu, Agnula/DeMuDi, and Linspire(freespire??)/Squiggle..

And then just test my way until I find the OS that is right for me. :D

Though, is gaming suppose to work in Linspire? As far as I understand it should.

---

### Post by Steve1961 on 2005-09-05
I started out by buying an extra hard disc about three months ago to try different distros.  I dual-boot with XP and to be honest I was scared that writing grub to the mbr of my xp disc would screw things up, so I opted for an xp package called Acronis disc director which has a seperate boot manager and can create and manage partitions.  This allowed me to simply save grub to the linux root partition, and not the mbr, and the boot manager picked it up as soon as I rebooted and allowed me to launch whichever operating system I wanted.  I still use this but if I was starting from scratch I think I'd just use grub now that I've gained more confidence.

Anyway, the point I want to make is try as many distros as you can when first starting out, and a seperate hard disc is always a good idea.  At one point I was quad booting XP, Ubuntu, Fedora and Xandros.  But after a few weeks I settled on Ubuntu, deleted the other Linux partitions on the second drive and created a single Fat32 partition that I could share with XP.  I couldn't get wine to work properly, so I bought cross-over office so that I could run MS office (which I need for work unfortunately) in Ubuntu.

Distros such as Linspire and Xandros are very windows like, and initially I liked Xandros a lot, which is a free download.  However, simply because of personal preference, there's something about kde's bouncing icons that drives me mad.  I also felt less 'restricted' with Ubuntu, which isn't trying to be just another windows clone.

As far as Linspire is concerned, I think its a lot like Xandros, but its built on a modified version of wine so you can use some windows programmes - but not all.  Happy experimenting!

---

### Post by tedwoo on 2005-09-05
Hi Steve1961, this is what I want to hear. Someone who actually done the things I'm about to do :D

Do you know of an like step to step guide on how to do it? Using grub and all, because I don't really get that.

What do you mean with "kde's bouncing icons"? I don't know if I would bother about it, though if u can't turn it off... 

Is it possible to run games on Xandros? Did you try that? I _really_ want it to be possible[I just can't let that tought go :)] :D

---

### Post by Steve1961 on 2005-09-05
OK, lets take this step by step.

1. Do you know of an like step to step guide on how to do it? Using grub and all, because I don't really get that.

I'm not sure where you'll find a generic how to on installing lots of linux distros but for Ubuntu you need to read these before you start:

[https://wiki.ubuntu.com/Installation/I386](https://wiki.ubuntu.com/Installation/I386)
[https://wiki.ubuntu.com//WindowsDualBootHowTo](https://wiki.ubuntu.com//WindowsDualBootHowTo)

After you've read these I'd suggest the following:

First buy a second hard disk and install it in your box as the secondary hard drive.  From windows you can use a partitioning programme to create partitions. although I believe you can also do this for free with programmes like qparted which come on liveCD distros such as knoppix - in fact I'd download a copy of knoppix anyway because it gives you access to your system if you get into trouble and lets you repair it.  Another advanatge is that knoppix doesn't load anything to your hard drive when you run it, but it gives you the chance of seeing if a debian based distro will recognise your hardware before you do a hard disk install.  

Anyway, to start with, create a single ext3 partition of whatever size you want plus a linux swap partition (1-1.5GB should be more than enough).  Then reboot and make sure you set your bios to boot from CD.  Insert your distro of choice in the drive and start the install.  Every distro has a slightely different installation routine but when it comes to the partitioning stage avoid the automatic routes - these usually take over the entire hard drive.  Choose to manually partition and point the distro to the first partition you've created and mount it as root /.  It sounds more complicated than it is, most installation routines are fairly self-explanatory when you get to this stage, especially the likes of xandros.  You don't need to mount the swap partition as your distro should recognise this for what it is

After this stage, which is the most complicated, just let the installation run until it gets to the part where you install the bootloader - grub.  The default is usually that grub is installed in the mbr.  This is what you want so just press Ok and continue until the installation finishes.  When you reboot, rather than seeing the XP splashscreen, you'll see the grub screen with options to boot linux or XP.  Just use the arrow keys to choose your o/s and press OK.

When you want to install another distro just create a new partition and install the distro into it.  You don't need a second swap partition as all the distros will share the same one.  Once again, when you get to the grub stage allow it to install into the mbr and overwrite the old configuration.  When you reboot you should have the option of booting XP and both your linux distros.  Do the same again if you want a third distro.

2.  What do you mean with "kde's bouncing icons"? I don't know if I would bother about it, though if u can't turn it off...

I just don't like the look and feel of kde.  It's always struck me as a bit cartoonish, but its just a personal preference.  I also dislike the way the cursor bounces up and down when you launch a programme.  A minor irritation, but as gnome is an alternative in Ubuntu I much prefer that.  In the likes of Xandros and Linspire you're stuck with kde.

3. Is it possible to run games on Xandros? Did you try that? I really want it to be possible[I just can't let that tought go 

I didn't try, but I think you'd probably need to install an emulator.  Cedega I think it's called.  That said, Xandros does come with a trial version of crossover office so you could test install a game and see what happens.

Hope this helps.

---

### Post by tedwoo on 2005-09-06
Thank you again steve, now everything is clear for me :D

Just gotta order that hd then..  \\:D/

---

### Post by poofyhairguy on 2005-09-06
[QUOTE=tedwoo]
Though, is gaming suppose to work in Linspire? [/QUOTE]

Cedega is the program to get that to work. Works as well in Linspire as Ubuntu. Is the only Linux solution.

But....I can honestly tell you....I have had bad luck with ATI and Cedega.

---

### Post by ygarl on 2005-09-06
I am a home studio user, and I HIGHLY recommend Dyne:Bolic. It is a LiveCD distrobution, which you don't need to install at all (though you have the option of partial or complete installing).
However, I've never had the need to install it. It quite happily recognises my Samba shares (for those with 2 or more PCs), gets me online with 3 different web browsers, has FTP programs etc, and HUGE numbers of amazing audio packages including a wonderful excecution of Ardour - a hard-disk multi-track recording program which basically made me throw away my 4-track and scrap all plans to get an 8-track machine forever. 
Loads of sequencers, MIDI programs, synth editors, Hydrogen - a very slick drum machine program with multiple soundfonts, etc etc.
It also mounts all your drive partitions, floppies and USB devices as well as having CD ripping and burning facilities.

And if you don't like it, just throw away the CD - just like that (or record over it) - no harm done!

Seems to work great on my dual boot Ubuntu/Windows XP/98 system...

I tried Agnula/Demundi and ran into serious 'dependency hell' issues - where you need one program to install another, but that one needs a version of another program which isn't on the repositiories, so you compile it only to find you need another library which hasn't been upgraded on thier servers (or is called something ALMOST the same! ARRRGH!) so I reinstalled Ubuntu for my 'serious' Office and Gaming stuff and just boot up Dyne Bolic for Music-making.

Your milage may vary...

---

