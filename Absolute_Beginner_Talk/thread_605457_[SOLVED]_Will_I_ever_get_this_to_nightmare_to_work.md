---
title: "[SOLVED] Will I ever get this to nightmare to work?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by DawnDisciple on 2007-11-07
Several posts here, but all are problems I am having. I have tried now 3 times to install Ubuntu and failed, once losing all my data and needed to reformat.


I have win xp installed and want to install Ubuntu on the same drive (duel boot), I only have the one sata drive and have created a second partition for Ubuntu, problem is when I come to install Ubuntu I cannot understand what the partition menu is all about, it makes no sense, what option to press, I am frightened that is will destroy or re-partition my XP install.  I have asked about this on many sites but seems no one can give me a straight answer, they either don't know or they want to keep it to themselves.

I have a Athlon 64 along with a 64bit capable machine, which should I install 32 or 64 I have burned both in preparation. Also what is best for the absolute beginner (Me) Ubuntu or Kubuntu

Whenever I boot my live cd Ubuntu amd64 I get the loading menu then screen goes blank, I hear a tune then my monitor goes to sleep. I can get no further than this.

---

### Post by hyper_ch on 2007-11-07
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Sef on 2007-11-07
> I have a Athlon 64 along with a 64bit capable machine, which should I install 32 or 64 I have burned both in preparation. Also what is best for the absolute beginner (Me) Ubuntu or Kubuntu


Since you are having problems with the 64-bit, I would go with the 32-bit.  There are a few things that are easier to install on it.

---

### Post by ugm6hr on 2007-11-07
> **DawnDisciple said:**
> Whenever I boot my live cd Ubuntu amd64 I get the loading menu then screen goes blank, I hear a tune then my monitor goes to sleep. I can get no further than this.

Which CD are you using to get you to the partition menu?

I would suggest you ensure that a live CD allows you to install before trying again.  Perhaps try the i386 LiveCD.

Installing with the alternateCD gives greater compatibility, but if the LiveCD doesn't work, there is no way to know whether Ubuntu will work once installed.

PS: I would try Ubuntu rather than Kubuntu, simply because it is easier to ask for advice here.

---

### Post by TeaSwigger on 2007-11-07
Relaxed and methodical will get you there. Nobody knows any of it at first, we all learn as we go. Osmosis. Live and learn. Etc...

Plus it's good to learn partitioning, because the knowledge can serve you well in a Windows or Linux system, both in possibly rescuing either system, in reinstalling either, in saving you money from needing paid help, and in allowing you options to set things up in customized ways later on. Details differ but many concepts are the same for most all computers. In addition to the above links, this site has a lot of information:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I use Kubuntu but for you starting in it, I suggest Ubuntu. 64bit may be harder to handle and require more learning steps as you go, but then you could have even better performance from your computer - depends how much you're willing to work for it. With open source linux, it's your computer now to make or break ;)

---

### Post by DawnDisciple on 2007-11-07
First I tried the Kubuntu 32 bit install which trashed my XP install, so I got a little weary of it after that.
I was told later that I may as well install the 64 bit version seeing I was set up for it, but as you read all I get is a blank screen.
So I have given up with Kubuntu and am now going to try Ubuntu.  What you have to understand is I can make any windows OS sing and dance but this linux thingy is hogwash to me, I am a fast learner but know not where to start.
All searches for help reveal the same thing, they speak as if you where a old hand at the Linux OS, I haven't a clue what they are on about.
I just want simple instructions on how to duel boot my XP with Ubuntu 7.10 so that I can make a start at learning, bad advert when you can't even install the sucker.
I get the impression from the many sites I have been on and questions asked that nobody actually knows much about the install of the  Linux beast, but somebody must, who ever wrote it must have shared their knowledge with someone.:)

---

### Post by Metal Mick on 2007-11-07
Hi DD,

I am quite new to Ubuntu, and like you, I struggled to get it up and running, although in different areas.

I cursed the text install mightily for it seemed profoundly intractable, but found the graphical install (from the live CD) far easier. Correct me if I'm wrong, but you're having trouble understanding the partitioner or feeding the thing what it wants. I can tell you what I did, in the hope it helps.

When I looked to partitioning, I found I could create or nominate an area on a HD as ext3 format for my main Ubuntu workspace (an equivalent of a Windows directory). I had to then tell the partitioner that I wanted it to have amount point of "/", so I had to go into the partitioner a second time and change the mount point from whatever it was to simply "/". Then I nominated a smaller partition for my swap - the Windows equivalent of virtual memory - and asked that it be formatted as a "swap" partition. This needs no mount point. The sizes of each partition is up to you, but the partitioner will have a caution about minimum sizes.

I was using a second HD in my machine, which I wanted for the specific purpose of housing my Ubuntu install, with room left over for some data that I could access from Windows or Ubuntu.

hyper-ch has put some useful links up for you to read - the second is a stepwise series of screens that the liveCD installer will take you through. The first discusses the reasons for partitioning and recommends courses of action.

I hope I've been able to help.

Regards,

Michael P

---

### Post by DawnDisciple on 2007-11-07
> **TeaSwigger said:**
> 


[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I use Kubuntu but for you starting in it, I suggest Ubuntu. 64bit may be harder to handle and require more learning steps as you go, but then you could have even better performance from your computer - depends how much you're willing to work for it. With open source linux, it's your computer now to make or break ;)

Already been to that site, no real help.
For instance if I was installing Vista 64 and my display went west, I would log on and there would be 1000+ threads on how to fix it or a MS hotfix.  When reading threads from people having the same problem as me with Linux, the answer was always the same "Install the 32 bit version".  Nobody seems to know what's going on.

---

### Post by DawnDisciple on 2007-11-07
> **Metal Mick said:**
> Hi DD,

I am quite new to Ubuntu, and like you, I struggled to get it up and running, although in different areas.

I cursed the text install mightily for it seemed profoundly intractable, but found the graphical install (from the live CD) far easier. Correct me if I'm wrong, but you're having trouble understanding the partitioner or feeding the thing what it wants. I can tell you what I did, in the hope it helps.

When I looked to partitioning, I found I could create or nominate an area on a HD as ext3 format for my main Ubuntu workspace (an equivalent of a Windows directory). I had to then tell the partitioner that I wanted it to have amount point of "/", so I had to go into the partitioner a second time and change the mount point from whatever it was to simply "/". Then I nominated a smaller partition for my swap - the Windows equivalent of virtual memory - and asked that it be formatted as a "swap" partition. This needs no mount point. The sizes of each partition is up to you, but the partitioner will have a caution about minimum sizes.

I was using a second HD in my machine, which I wanted for the specific purpose of housing my Ubuntu install, with room left over for some data that I could access from Windows or Ubuntu.

hyper-ch has put some useful links up for you to read - the second is a stepwise series of screens that the liveCD installer will take you through. The first discusses the reasons for partitioning and recommends courses of action.

I hope I've been able to help.

Regards,

Michael P

Thank you for trying to help Michael, but you lost me after the line "in the hope it helps." :)

---

### Post by Doggles on 2007-11-07
OK let's start at the beginning and change the bits that aren't working...

If your liveCD doesn't work, you're screwed from the start, so try a different one (how about the 32 bit version, just to see if that's causing a problem?) - also, is there an option to check the disk, or does it just go blank?

If your screen is going black then it sounds to me like the live CD maybe  isn't recognising your screen properly and is trying to send an unsupported resolution or refresh rate - or maybe it's a corrupt CD.

Once you get a live CD talking to your system properly then we can use gparted to have a look at your partition setup and take you through the install properly. I wouldn't plough on through a text based installer blind as a beginner, it will be much better if we can get a live CD working.

Actually - come to think of it, ANY ubuntu-type live CD will do. Once we've had a look at your partition setup and made sure what we're dealing with from a live CD, then we can proceed with alternative types of install for the OS that you would prefer.

I understand you exasperation with this one, it doesn't give you much of a chance to sort things out if you can't even get into your system! - stick with it, get a live CD, any live CD, to display a working desktop on your screen then post again.

One other option - look up gparted live CD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/) - this might give you a glimpse of your partitioning set-up at least so we can see what we're up against if we do decide to try a text-based manual install.

Finally - you say that Kubuntu trashed you XP install - I can understand that it might have done this if you picked the "use entire disk" option, but if you do "manual install" option and don't overwrite your XP partition, then it should be fine. The only issue then is where grub gets installed. If you install grub to the MBR, then there is a chance that you won't be able to boot into XP straight away - this does not necessarily mean that your XP install is borked, it just means that Grub needs setting up to correctly boot it. We can go through all of that when we get you to a position where you're ready to install - first we need to get a live CD working!

Cheers

---

### Post by Barrett Hageman on 2007-11-07
DD, 

  I understand your frustration, As I do not have much advanced information to offer. I can offer my Newby input. I have been trying to run Linux for 10 years. I have found this Distro to be the easiest. My recomendation is Ubuntu amd 64 as I have a similar system minus the graphic card. I installed from the 7.10 dvd install rather than the live cd. BTW the dvd install runs like the live cd.  I had troubles with the live cd in the beginning, and the dvd install seemed to do better for me. As for partitioning I can not offer much wisdom for I have 2 150g hds, and I have winxp on one, ubuntu on the other. But after little hassle, 2 format/reinstalls I am running Ubuntu on 2 computers one desktop, one laptop. Keep with it you will not be sorry, as I am getting rid of winxp soon, and will be running only Ubuntu.

---

### Post by bharris25 on 2007-11-07
Download linux Mint latest live cd and try that to just boot your computer.  Go out and buy an external hard drive use Mint to access your hard drive and copy all your files over and remember to always back up before messing with partitions, make sure you enable ntfs write support on Mint to write to that external hard drive.  Then after that do a Manual install with the live cd and resize your windows partition which is probably sda1 to whatever size you want it but not smaller than the amount of data on it.  You will click on the last partitions and delete them, then you will click on your windows partition and click edit, resize to what you want, I suggest giving linux at least 15 gb.  With the newly aloccated free space you will click on that and make a swap partition of at least 256 mb but it should be the amount of ram you have.  Next you will click on the rest of the free space and make a ext3 partition (with a mount point of /).  Now you should have no more free space and be ready to click forward.  It will show you which partitions will be formated and your windows partition should not be on that list. Begin installing the system.  Linux Mint is based on Ubuntu and uses the same repositories for software.  It comes with Beryl pre-installed which gives it a nice shine and it is very easy to use.  Mint is really going after ease of use and it has some codecs required to play mp3 and mpeg video installed out of the box.  You should try it out even if you don't install it, It's worth looking at.  Hope I helped.

Also as for the blank screen after loading screen try hitting Ctrl alt f1 and that may bring up the loading screen again and you might see text scrolling down the screen and it should boot up.

---

### Post by Harpoon on 2007-11-07
In an effort to het you going, let me offer a simpler solution to the partitioning problem.

If you have windows up and running, and have a copy of partition magic, then fire up PM and resize your windows partition (leaving free space at the end).

When you look at the onscreen display you should see your Win partition, and a greyed out "unallocated" block which you can use for your Ubuntu install.

Second best solution (for windows users) is to download a copy of Gparted live cd.  Put it on a disk and boot into that.  Use it in the same way as you would use partition magic - - resize, keep unallocated free space.

Fire up the live cd - - or whatever - -  and when you get the partitioning part you can tell it to use the "largest available free space".  Somewhere in that sequence it should also tell you that it found a Win partition and ask if you want to keep it.  Say yes, of course.

Way too many people have a hard time navigating the partition screens, and it seems the time is well past for someone to re-work the instructions for those that are new to all of this.

As for the screen issue, I can't help.  But I chugged the Gutsy live CD into my laptop, had some other problems, and decided that I would keep my reliable Feisty (64)  until I can free up another partition to experiment with.  Try Feisty, I bet you like it.

---

### Post by Harpoon on 2007-11-07
Sorry, typing errors are a consequence of ageing eyesight, incompetance, or insanity.  Perhaps all three.

---

### Post by hyper_ch on 2007-11-07
> **Harpoon said:**
> Way too many people have a hard time navigating the partition screens, and it seems the time is well past for someone to re-work the instructions for those that are new to all of this.

IMHO the problem is not with the partitioning screens but that the people don't know what they mean and do... Most ppl IMHO have never had dealings with partitioning and hence it's unfamiliar. I know some people that just go buy a new computer if the old windows isn't working anymore... they don't even try to re-install it or fix it...

---

### Post by DawnDisciple on 2007-11-07
I have just got back from the shops and am running though all this new info, thanks everybody.
 First thing I have to do is make sure I have the live CD/DVD.  Now before I start should I partition my drive into 2, I can use partition manager that formats .ext2 and .ext3, My winXP is using very little of my hard drive at the moment so space is no object.

The reason we found out later, for the Kubuntu install trashing my xp install was because I had mixed hard drives IDE/SATA  this seems to be a known problem.  I have since removed the IDE drive.

---

### Post by hyper_ch on 2007-11-07
well, if you have IDE and SATA mixed it poses as few challenges but it's managable (if you know how) ;)

If you partition in windows, leave the space for linux unpartitioned... or make directly a setup that you want with swap, root, home partitions.

---

### Post by rpankn1 on 2007-11-07
Hello Dawn Disciple.  What you're trying to do is possible -- I've had a XP 32 bit and Ubuntu 7.04, then 7.10, 64 bit on a dual boot.  I don't know if this will be of help to you, but here's what worked for me and what I found the easiest.  By the way, I have a Dell XPS 410n with a 250 GB SATA HDD, 2 GB RAM, and 2.6 GHz Intel Core Duo.

If you choose to go this route, make sure you have a good block of time to do everything because you're going to be in front of your computer for awhile.  First, back up anything you want to save to a CD or DVD.  I started out fresh by nuking my hard disk drive using Darik's Boot and Nuke for 64 bit processors because I've ended up having issues with the XP partition by just doing a simple reformat.  DBAN is a free program, available here: [http://sourceforge.net/project/showfiles.php?group_id=61951&package_id=72235&release_id=504756](http://sourceforge.net/project/showfiles.php?group_id=61951&package_id=72235&release_id=504756) (Choose the 2007042900 version).  But be forewarned, there will be nothing left on your HDD and it takes awhile for DBAN to do its magic.  I set it to go right before I went to sleep because it took about 5 hours for the entire process on my HDD, so when I woke up, my system was ready to go.  Next, XP should be installed first (it's possible to do it the other way around, but it's a bit complicated, and not worth the hassle in my opinion, because XP will write over GRUB, the boot loader program).  Then, install the drivers for your system, followed by all the XP updates, and then all the applications you're going to want to use on XP, including, of course the anti-virus and firewall programs, etc.  

Next, go to Download.com and get these programs: CCleaner, WinASO Registry Optimizer and Auslogics Disk Defrag -- they're all free utilities.  Run CCleaner -- both the disk and registry cleaning options.  After that, run WinASO, using the 'Clean Registry', 'Privacy Eraser', 'Speed Up System', and registry defrag functions.  Then run Auslogics disk defrag, followed by XP's own disk cleaner and disk defrag utilities.  Restart your system and run XP's disk defragmenter a few more times.  The goal here is to get as much of the XP installation to one "side", so to speak, of the HDD as possible because it will lessen the chance that XP's master boot record will get messed up when you install Ubuntu.  I can't stress enough how important this is and not to take any shortcuts.

Then, of course, grab a copy of Ubuntu 7.10 64 bit and burn the ISO to CD.  I used the disk image program provided on Ubuntu's download page and burned it at a low speed, which is crucial because it lessens the chance of errors, or corrupted files, on the CD.  Once you've done that, test out the CD you just made as a Live CD by going into your system's BIOS and changing to boot order so that your system boots from the CD/DVD drive first.  When the splash menu comes up, look for the option to check the CD for errors and run it.  If everything's fine, reboot and try out the live CD.  It will take some time to load up, so don't let the slow start worry you.  I did this because even though 7.04 worked pretty good on my system, I wanted to make sure my system and peripherals still worked ok with 7.10, or if something would require a fix.  And, if that was the case, I could go back into XP and search online to figure out what to do about it before installing Ubuntu.  But in my case, everything worked fine, so I proceeded to install 7.10.  

During the installation process, when you get to the partitioning section, let Ubuntu do it automatically for you, unless you're trying to set up a shared partition for XP and Ubuntu, or a separate partition for Ubuntu's home folder.  In that case, maybe someone here can help with that because I've never attempted either one, and didn't see a need to set up a separate partition for my home folder because I learned the hard way about backing up my important stuff regularly after a RAID configuration went bad on XP a couple years ago.  

Anyway, once Ubuntu is finished installing, take the CD out when it tells you to and restart.  Pay close attention after the BIOS starts up for GRUB to appear, and select to boot into XP -- you only get 10 seconds to do this.  When XP boots up, you'll get the two-tone blue screen.  However, this is nothing to worry about because XP just noticed that some things have been moved around and will run a few diagnostics to get everything back in order.  When the desktop comes up, wait a few seconds because XP will also reinstall a driver -- can't remember off hand which one though.  After that's done, reboot and go into Ubuntu and you should be set with a XP/Ubuntu dual boot.  I know this sounds like a lot of work and time, but it's what's worked for me.  



> **DawnDisciple said:**
> Several posts here, but all are problems I am having. I have tried now 3 times to install Ubuntu and failed, once losing all my data and needed to reformat.


I have win xp installed and want to install Ubuntu on the same drive (duel boot), I only have the one sata drive and have created a second partition for Ubuntu, problem is when I come to install Ubuntu I cannot understand what the partition menu is all about, it makes no sense, what option to press, I am frightened that is will destroy or re-partition my XP install.  I have asked about this on many sites but seems no one can give me a straight answer, they either don't know or they want to keep it to themselves.

I have a Athlon 64 along with a 64bit capable machine, which should I install 32 or 64 I have burned both in preparation. Also what is best for the absolute beginner (Me) Ubuntu or Kubuntu

Whenever I boot my live cd Ubuntu amd64 I get the loading menu then screen goes blank, I hear a tune then my monitor goes to sleep. I can get no further than this.

---

### Post by DawnDisciple on 2007-11-07
Okay I got me a shinny new copy of ubuntu 64 v 7.10, I am going to resize my 200 gig hard drive to 150gig leaving 50 gig of free space, the 150 gig partittion will hold my Win XP, I don't want to lose this.
When thats done I will attempt to live boot Ubuntu, maybe I can post here from the live cd when I get to that stage.

---

### Post by Doggles on 2007-11-07
...holds breath ... crosses fingers ...

---

### Post by antony11 on 2007-11-07
Hiya DD. Ive only installed Ubuntu a few days ago so I can sympathise with your problems. But the advise you have received here is sound good advise. I havent had the same issues as you but Ive certainly benenfited from the support. Keep it up :)

---

### Post by DawnDisciple on 2007-11-07
Well I mean to give it another shot after 3 nightmares, so if anything I must be determined.:)

I am on my backup computer while my main is partitioning ready for my install, you know what I'm really looking forward to? playing scorcher tanks.

Tell you something you guys on this forum are all right, I expected you all to be dead snooty with plums in your mouths.:)

---

### Post by DawnDisciple on 2007-11-07
No same thing, booted my Live Ubuntu and after the nice little line going back and to I get a blank screen and my monitor goes to sleep.  Is there something I should be adjusting in my Bios to get the graphics to work?

---

### Post by hyper_ch on 2007-11-07
well, ATI is generally a problem...

---

### Post by DawnDisciple on 2007-11-07
Well if I can't see it, I can't install it.  I am not the only one having this problem is there no solution yet?

---

### Post by DawnDisciple on 2007-11-07
Has it got something to do with my LCD and digital output?

---

### Post by Doggles on 2007-11-07
How's your monitor connected to your PC? - old fashioned blue VGA or fancy new white DVI? - try the blue one...

Ati graphics can be a pain under linux, but not this early into the install - you should at least see something! - my old 9800XT worked until it finally blew up, I've gone NVidia since then.

Failing a bit of cheeky cable-swapping, I think we're looking at a text install, using all available space, installing grub to MBR, then logging into recovery mode and configuring xorg from there. If this fails, then installing grub to the MBR might make it look like your XP install is borked, but it won't be, you might want to have a floppy with FixMBR at the ready just in case.

Just a thought - graphics went a bit screwy while I was using Xubuntu liveCD ages ago, I was losing patience with having to restart, then I had to go out, and left it at the corrupted screen - don't know what happened, but when I got back I had a working liveCD desktop - it just seemed to sort itself out after being left for a while. Maybe you could try leaving it for a bit? - seems really lame I know, but it worked for me once -  anything's worth a try. Also - other distros have live CDs so you could check one out just to see if it's an Ubuntu-specific issue.

One other thing to try, you could maybe re-enable on-board graphics if you have it on your mobo, then try plugging your monitor in there - that would rule out the graphics card perhaps - could just make things more complicated though!

Sorry to hear that it's still causing you grief - and further to your earlier comment about this forum being a helpful place - yeah sometimes you do see the odd idiot being sarcastic, but the vast majority of us really try our best and want to see Ubuntu work for as many folk as possible - glad to see that you approve!

keep on truckin'...

---

### Post by DawnDisciple on 2007-11-07
Okay I gave up trying to get the 64 bit to work and have just booted the live 32 bit version, I got a error message something to do with gnome but I am now actually on the Ubuntu desktop, what now?

---

### Post by hyper_ch on 2007-11-07
click the "install" icon (or test ubuntu first to see whether you really want to install it)

---

### Post by DawnDisciple on 2007-11-07
> **Doggles said:**
> How's your monitor connected to your PC? - old fashioned blue VGA or fancy new white DVI? - try the blue one...

Ati graphics can be a pain under linux, but not this early into the install - you should at least see something! - my old 9800XT worked until it finally blew up, I've gone NVidia since then.

Failing a bit of cheeky cable-swapping, I think we're looking at a text install, using all available space, installing grub to MBR, then logging into recovery mode and configuring xorg from there. If this fails, then installing grub to the MBR might make it look like your XP install is borked, but it won't be, you might want to have a floppy with FixMBR at the ready just in case.

Just a thought - graphics went a bit screwy while I was using Xubuntu liveCD ages ago, I was losing patience with having to restart, then I had to go out, and left it at the corrupted screen - don't know what happened, but when I got back I had a working liveCD desktop - it just seemed to sort itself out after being left for a while. Maybe you could try leaving it for a bit? - seems really lame I know, but it worked for me once -  anything's worth a try. Also - other distros have live CDs so you could check one out just to see if it's an Ubuntu-specific issue.

One other thing to try, you could maybe re-enable on-board graphics if you have it on your mobo, then try plugging your monitor in there - that would rule out the graphics card perhaps - could just make things more complicated though!

Sorry to hear that it's still causing you grief - and further to your earlier comment about this forum being a helpful place - yeah sometimes you do see the odd idiot being sarcastic, but the vast majority of us really try our best and want to see Ubuntu work for as many folk as possible - glad to see that you approve!

keep on truckin'...

You sir are a genius, I dug out the old analog cable and replaced my digital with it and guess what?
Yes, the display now works, and I am in the process of installing the 64 bit version. I love the look of it.
I was about to install the 32 bit version until I seen this post and thought, why not Ill give it a go before I commit.

---

### Post by Doggles on 2007-11-07
Excellent... and thanks!

Right then, now we get to the bit where you install Ubuntu, and then reboot, and start screaming because it looks like either Windows or Ubuntu have disappeared... hee hee - whatever happens next, don't panic - I'll keep checking this thread to see how you're getting on...

---

### Post by DawnDisciple on 2007-11-07
Thanks Doogles, I have gone a lot further than I dreamt possible, must be my lucky day, please wait while I get this of my chest.....

Yeeeeeeeharrrrrr, yes,yes, whoopie, waaaaaaaaaa, brilloooooooooooo I doooooonnnnnnneeee iiiittt.

That's better, I successfully installed Ubuntu 64 bit, it restarted with a cute little menu where my Win XP was included, so I tested XP and it works lovely, restarted, got to my new Linux desktop and got invited to install new graphics driver and updates, done both and restarted, my screen is hanging a little to the left, not sure how to fix that.  But up to now I just love this system, it's so cool, I have so much here to learn about and fool about with.  I think I may be asking lots of questions.

BTW, if anyone else has their display go blank when installing Ubuntu you can tell them all they have to do is change their Digital lead for a analog on their monitor.

---

### Post by Metal Mick on 2007-11-07
Hi DD,

glad to hear you're up and running.

I didn't mean to confuse with my earlier posting.

Take care.

Michael P

Books do not exhaust words, words do not exhaust thoughts.

---

### Post by Doggles on 2007-11-08
So glad you're reaping the rewards of you perseverence. The cute little menu which includes an option for XP is your grub menu. Sounds like the installer has done a good job of setting this all up in your case - hurrah - so you don't need to do any mucking about with that at least.

As for your display being a bit skewed to one side - this happened to me too. There are some buttons on the front of my monitor which control the horizontal offset of the picture so I tweaked them to get it centred. You'll find that this moves XPs picture too though! - there's probably a setting in catalyst control under XP to correct for this, so you can probably get both of them displaying correctly without too much fiddling about. Personally I dropped XP after a couple of months, so it's not a problem anymore :)

---

### Post by corowakid on 2007-11-08
> **DawnDisciple said:**
> Already been to that site, no real help.
For instance if I was installing Vista 64 and my display went west, I would log on and there would be 1000+ threads on how to fix it or a MS hotfix.  When reading threads from people having the same problem as me with Linux, the answer was always the same "Install the 32 bit version".  Nobody seems to know what's going on.


Sorry to say that you're not looking like a guy that wants to look closely at recommended sites.


I was referred to Hermanzone when I was in a situation like you. I found a *step-by-step* instruction for doing exactly what you're trying to do. At first glance I thought "what the h...!". But I read it 3 or 4 times, and eventually things started to make sense.

Here's what I did - and I'm running 64bit.

First, I downloaded the Alternate Desktop version of 7.10. This allows you better partitioning than the other CDs. Reading Herman's tips I saw the "Manual" partitioning is the way to go - you get control over what happens. Using his guide (which I printed out), I was able to re-size my XP partition, using the free space generated to make the Root, Home and Swap partitions. Do make a Home partition - that way you get to keep your work if you need to re-install Ubuntu. Make sure you format it FAT32, so Windows can see it, and Ubuntu can write to it. Herman gives step-by-step instructions for all this - you need to spend time getting how it works; a single glance won't help you at all.

Now I've got 7.10 running, I visited [www.albertomilone.com](www.albertomilone.com) to get my nVidi card installed. Again, I read it 3 or 4 times, printed what I thought I'd need, and followed them step-by-step. Result? I'm using Compiz and all effects.

I'm not having a shot at you about this. But you join a long list of people that seem to be disheartened at not being able to learn Linux in a day. You mention you have no problems with Windows - have you added up how much work you had to do to get where you are, and equate that to what you need to do now.

The result of Linux will make a virtually unbreakable OS, heaps of software and services *free*, its faster and eventually more intuitive than Windows. Hang in there- the journey's worth it.

---

### Post by DawnDisciple on 2007-11-08
I don't know about dropping XP yet, for me its going to be a good while before I can juggle Linux the same way I juggle XP.
My fingers are sore though typing, my eyes are sore though reading, my brain is sore though trying to absorb and my pride is sore for being such a noob.  But small thing are starting to fall into place, I am starting to understand a little of this alien OS.

---

### Post by DawnDisciple on 2007-11-08
> **corowakid said:**
> Sorry to say that you're not looking like a guy that wants to look closely at recommended sites.

t.

My problem was major simple, and someone on this forum just popped on and gave me the answer.  All I had to do was change over my digital lead to analogue on my LCD for the install, then after the install I just changed the lead back to digital.

Its not that I don't wants to look closely at recommended sites its the fact I couldn't understand what most of them where on about, I wasn't at the authors level.

---

### Post by hyper_ch on 2007-11-08
Home partitions as Fat32 is not really recommended...

---

### Post by DawnDisciple on 2007-11-08
> **hyper_ch said:**
> Home partitions as Fat32 is not really recommended...

Looking at my partitions the Ubuntu install sorted it all out for me /home is .ext3

---

### Post by Doggles on 2007-11-09
Hey DD - how are you finding it so far then? - everything working OK?

---

