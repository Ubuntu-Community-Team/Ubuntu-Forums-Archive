---
title: "I fail at Ubuntu"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by SlyReaper on 2008-01-30
Well it looks like my ubuntu installation is well and truly buggered.  Display errors, WIFI connectivity (or lack thereof) are driving me nuts.  Looks like ubuntu runs better on my wheezing broken down old laptop than it does on my shiny new desktop.  I'm fed up trying to bump my "please help me!!" thread.

So what's the best way to go about removing ubuntu from my desktop system?  I've got it on a dual boot with XP, with 110GB for windows, 30GB for ubuntu.  I'd like to be able to reclaim those 30GB for windows, without them being on a separate partition.

I'm sure it's not a popular question to ask in an ubuntu forum, but any pointers would be greatly appreciated.  Thanks.

---

### Post by angryfirelord on 2008-01-30
Relax! You're just trying to get accustomed to a new way of doing thing. Please post *specifically* what hardware isn't working (and any errors that may pop up) and we'll try to help you.

---

### Post by Scarath on 2008-01-30
First off I would say 'simmer down' if you really want to know what Failing at linux is like install Slackware and then you will know (i fail at Slackware every few months when i forgot the terror or trying to install it and give it another chance).

point 1b. relax, leave it till ur in the mood for messing and then try again, no point uninstalling in a fit of rage :D

Second in XP go: control panel, admin tools, disk/storage or sommin, then u shud see all ur partitions, delete the ubuntu one or reformat it or whatever. Something like that i dont use XP anymore.

---

### Post by regomodo on 2008-01-30
google gparted livecd. it'll let you wipe that partition and resize the ntfs xp partition. Shouldn't be any harder than that.

---

### Post by Philo1 on 2008-01-30
I've googled allot to stuff myself, but the forums are excellent for doing research. I haven't posted much at all, but this "all" really takes some practice. I am fairly advanced with Windows, which I loathe. Just hang in there, ask questions and enjoy the ride, good luck!

---

### Post by SlyReaper on 2008-01-30
Tried that in my other thread, but OK I'll try again.

On startup, it tells me it can't detect my screen or graphics card properly, and that it's going to start in safe graphics mode.  I click the button to manually configure my screen and graphics card, and select the ATI Radeon card from the list, and for screen, Generic -> 1680x1050 LCD panel (which it is).  I click OK, and the computer just completely disregards what I just did and starts in safe graphics mode anyway.  The maximum resolution I can get is 800x600, except occasionally when it allows me up to 1400x1050.  Of course, when it gives me this option, all the colours are corrupted.  For example, the default desktop is bright green.  

When I enable the ati restricted drivers, it tells me to reboot.  Upon rebooting, nothing has changed - it won't let me chose a resolution higher than 800x600.  

Even more annoying is the WIFI connection.  It lets me connect to the internet, but without warning it will just cut me off.  If I try to reconnect, it asks me for the network key over and over again.  Rebooting fixes it, but only temporarily.  It's not the router's fault because I have another computer which has no such issue.

For reference:
Graphics: ATI Radeon HD2600 Pro
Monitor: CIBOX 22 inch 1680x1050 LCD
WIFI: Edimax 802.11g 54Mbps PCI card

My laptop has had ubuntu running on it since Christmas without troubles like these.  It has Intel integrated graphics, and a 1280x800 screen.  No idea what sort of WIFI it has.

---

### Post by ugm6hr on 2008-01-30
> **regomodo said:**
> google gparted livecd. it'll let you wipe that partition and resize the ntfs xp partition. Shouldn't be any harder than that.

Or you can do the same with the Ubuntu LiveCD (just a bit slower).

In System-> Administration-> Partition Editor:
Select the Ubuntu partition and Linux swap partition and delete them (you may have to unmount first - right-click on the bars).
Then select the XP partition for resizing.

If you want to persevere with Ubuntu - people here will help if possible.  However, if you have a *very* shiny new  desktop, it is possible that Gutsy (now 4 months old) does not have the drivers for some of your new components built-in.  Installing drivers can be easy (sometimes).  If not your cup of tea - maybe try again with Hardy (in April).

I have seen your display error post.  While it is frustrating - people often wait for a day or two before getting a post that solves the problem.

Wifi is another issue.  It is likely you can get it to work - but not everyone can.  If you want help - ask.

EDIT:
Please stick to 1 post for support regarding the display issue - I will merge these if you like:
[http://ubuntuforums.org/showthread.php?p=4238418#post4238418](http://ubuntuforums.org/showthread.php?p=4238418#post4238418)

EDIT2: For wifi - post output from:
lspci
lshw -C network

---

### Post by jordanmthomas on 2008-01-30
Step 1:  Boot off a Windows Install disk and go to the recovery console when you get the chance.
Step 2:  Log in to your Windows install (in recovery console) and type ```
FIXMBR
```
This reinstalls the Windows bootloader so you don't get a scary error message later.
Step 3:  Use a gparted / Ubuntu CD to delete your Ubuntu partition(s) and resize your Windows partition.


It's actually pretty easy (luck you :)  )

---

### Post by SlyReaper on 2008-01-30
> **ugm6hr said:**
> 
EDIT:
Please stick to 1 post for support regarding the display issue - I will merge these if you like:
[http://ubuntuforums.org/showthread.php?p=4238418#post4238418](http://ubuntuforums.org/showthread.php?p=4238418#post4238418)

Sorry about that.  I'm used to lurking in forums where bumping your own threads is frowned upon :)

---

### Post by emarkd on 2008-01-30
This is an excellent example of how certain hardware manufacturers make things so much worse.  Years old integrated Intel video works better than brand new cutting edge ATI stuff.  It's not Linux's fault; its the hardware manufacturers.  For some people, Ubuntu's not worth the hassle, and that's ok.  Come on back if you ever want to give it another shot.

By the way, did you ever try to reconfigure your graphics using dpkg-reconfigure xserver-xorg?  It may be worth a shot if you haven't...

---

### Post by flyinsqrl on 2008-01-30
don't give up, i installed ubuntu a week ago, and when i would get frustrated working on it, i would go play xbox or just leave it alone for a while and when i felt like it i would start working again, and after a while i started to get the hang of it and enjoying it, now i'm starting to get used to it and i love it.  My ubuntu box (crap old pc i resurrected) hasn't been restarted yet and its running great :D  just keep it up man don't get rid of the linux yet, give it time ;)

---

### Post by SlyReaper on 2008-01-30
> **emarkd said:**
> This is an excellent example of how certain hardware manufacturers make things so much worse.  Years old integrated Intel video works better than brand new cutting edge ATI stuff.  It's not Linux's fault; its the hardware manufacturers.  For some people, Ubuntu's not worth the hassle, and that's ok.  Come on back if you ever want to give it another shot.

By the way, did you ever try to reconfigure your graphics using dpkg-reconfigure xserver-xorg?  It may be worth a shot if you haven't...

Yep.  I did that.  It just ignored the options I chose.

Anyway my graphics card isn't that cutting edge.  It's only a HD2600 I picked up for just over 50 quid.  Cutting edge is HD3780 or something.

Obviously I would prefer to have ubuntu working on my desktop than completely removing it.  If nothing else, things work so much faster on ubuntu than they do in windows (on my laptop at least) and I want that for my desktop too! :)

Sorry if I came over as an angry windows user earlier - been trying to get it working all day with no progress ](*,)

I've just had a look over the specs for my WIFI card.  Looks like it only supports windows operating systems.  What a pain.  Should I get a new WIFI card that supports linux, or will there be a driver out there that will make it work?

---

### Post by emarkd on 2008-01-30
Did you try the Envy script for your video? - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Lots of windows-only wifi can be made to work using ndiswrapper, but I've got no experience with that.

Don't be sorry, by the way.  We all get frustrated with our computers sometimes.

---

### Post by SlyReaper on 2008-01-31
OK that envy thing sounds promising, I'll give it a try when I get home.  Thanks.

---

### Post by ugm6hr on 2008-02-02
> **SlyReaper said:**
> I've just had a look over the specs for my WIFI card.  Looks like it only supports windows operating systems.  What a pain.  Should I get a new WIFI card that supports linux, or will there be a driver out there that will make it work?

It is worth connecting without Network Manager, since it does sometimes behave unusually (especially with WPA encryption).

But first - let us know your specs!  Post the output from:
```
lspci
lshw - C network
iwconfig
```

What encryption do you use on wifi router?

This is a good How-To (and kevdog offers help there): [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

If that is not something you want to try, Wicd is an alternative to Network Manager (see link below - Wicd for wifi).

---

