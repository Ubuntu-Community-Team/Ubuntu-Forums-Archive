---
title: "First attempt at install from a &quot;Live CD&quot;"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by splitrimmz on 2007-12-15
I purchased from the internet a Ubuntu Live CD 7.10 Gutsy Desktop.  I also purchase a tutorial CD which explains the live CD and how you can boot it and get a feel for Ubuntu and later install it all on a hard drive.  I tried the live CD and after it goes through the graphical boot bar it gives me a black screen.  I waited 5 minutes with the black screen as the tutorial says the CD takes longer.  Nothing happened.

I booted a second time and selected the option that was something about bypassing graphics.  This time I didn't get the black screen at first, I got four lines of messages, looked like checks of memory, battery and some other things.  Then the screen froze, I waited 5 minutes, nothing.  I'm at a loss as to why it won't boot, I'm a newbee.    I searched a little for something about the "Live CD" but wasn't successful.   I also ran the check on the CD and it reported "No Errors".

I don't want to try to load it on my Harddrive until I at least see if it works and runs most things on my computer.  

Any help or suggestions appreciated.  

Splitrimz

---

### Post by Ripfox on 2007-12-15
What type of computer do you have? Is it older? Have you tried booting to "safe graphics mode"?

---

### Post by splitrimmz on 2007-12-15
Computer is Pentium R4 2GHZ, 1GHZ RAM.  Yes I tried booting in the no graphics mode, see Paragraph above where I mention that in that mode it started outputting some text messages which included a memory check and battery check among others, and then it hung.

---

### Post by tekwerx on 2007-12-15
Hm.  You "purchased" the CD?  From where?  It might be the company you bought it from did a bad burn job and corrupted something.  Just wondering, but why dont you download and burn your own ISO?  Its free, except for the CD and your time.  Also yeah...what machine are you running on?  Especially, what CD/DVD/combo/etc drive do you have (if you can tell)?  Ive had to replace many a drive because it didnt like Linux CD's.

---

### Post by tekwerx on 2007-12-15
What exactly happens when you do a regular boot from the CD?  Normally, it shouldnt take more than 2-3 minutes for a livecd to boot.  Does the drive just sit there, or does the light still flash and you hear it working?

---

### Post by splitrimmz on 2007-12-15
The drive is an HP cd/dvd/r/rw.  It boots the CD, the ubuntu screen comes up, it starts to load, the progress bar moves to the right, gets all the way to the end ............and the screen goes black.

---

### Post by tekwerx on 2007-12-15
> **splitrimmz said:**
> The drive is an HP cd/dvd/r/rw.  It boots the CD, the ubuntu screen comes up, it starts to load, the progress bar moves to the right, gets all the way to the end ............and the screen goes black.

Great!  It seems your CD and your drive are working, but it seems your video card may not be supported (just a guess at this point).  What kind of video card do you have installed?  Also, when the screen goes blank, do you hear any noises?  Ubuntu has some startup sounds, and when you cant see anything, you can still hear those and it usually lets you know its still working - something just isnt configured right.

---

### Post by splitrimmz on 2007-12-15
Hello, Graphics card is NVIDEA GFORCE FX 5700LE.  I here the speakers "thump" when the CD is booting up but other than that no sound when the boot process is done and I get ...........the black screen.

Where can I find a list of compatible devices?  I would have thought that the boot process would configure the video card.  

thanks

---

### Post by tekwerx on 2007-12-15
Hm, you just hear a thump?  The sound at startup is a few seconds long, got some drums and some jingles in it.  :)

Your video card is supported, and yes, it should be configured for runing at bootup.  Hm.  

Well, sad to say, at this point, theres not a whole lot to do, as you cant even get in to do anything to try and troubleshoot.  I do have one other suggestion - download another distribution like PCLinuxOS or openSUSE and see what happens when you try booting off of one of those.  If those work when you boot, then there might be something wrong with the Ubuntu CD youre trying to boot from, or there might be something about your hardware that Ubuntu doesnt like.  In any case, my recommendation is to try PCLinuxOS.  Its the one I would run if I couldnt run Ubuntu or Debian (and no, I dont recommend you try debian - its more of an intermediate/expert distro).  

[http://www.pclinuxos.com](http://www.pclinuxos.com) to get you started.  I wish you luck, and post here in this thread again to let me know if you got it working off the cd or not.  Oh, and when burning the ISO, burn it as slow as you can.  Yeah itll take a while, but youre ensuring a good burn, with little chance for errors.

---

### Post by patrick71797 on 2007-12-16
I have the exact same problem when I try to install 7.10 64 bit edition. I did a check sum of the ISO and it was correct so I burned a second ISO boot CD and it fails in the same exact manner of the first ISO boot CD. If I select the install option it dosent do much but maybe a few commands or loads the kernel and then my screen will go black with my monitor power button light flashing on and off and same with my keyboard lights, flashing on and off and the screen is just black.  Same thing happens when I try and do a check CD option.  It just locks up in any option to install so I just gave up and was checking the forums to see if anyone else was having problems like this. I'm not a linux guru more of a newbie and this was my first ever attempt at installing a linux distro...not very encouraging when you can't even get the install going :(

I'm running, AMD Athlon 64 3200+
1.5 GB of Ram DDR 400
ATI X800 Pro
MSI K8n Neo Platinum MOBO with Nvidia Nforce3 250gb chipset
Ide (0) Primary Master Western Digital 250Gb HD w/ 2 primary partitions one for XP pro and XP pro 64
Ide (0) Secondary Slave Maxtor 40Gb (was gonna use this one for Linux)
Ide (1) Master Sony DVD RW 
Ide (1) Slave CD RW
also have 1 SATA Maxtor 60Gb HD with Vista on it. 

I do have a copy of Ubuntu 7.04 64 bit and 32 bit that I got from my Unix class I took but have not tried installing that version yet.  I was told going from 7.04-7.10 is like in MS terms going from XP to Vista so I was hoping to get 7.10 running.  Any ideas would be much appreciated, again I not really a linux guy, so you have to pretty much speak to me like I am a five year old, total newbie here.

---

### Post by chupy on 2007-12-16
Hello, I have the exact same problem too when I try to install 7.10 32 bit edition. The "Live CD" was air-mail to me from Netherlands to Malaysia after I requested it for a free copy from the official website.

Anyway, my laptop is Acer TravelMate 280, current spec (which I upgraded) as following:
- P4 M 2.4GHz
- 1.25GB RAM
- Graphic Card: Intel 82845G
- DVD-RW Drive
- Maxtor Harddisk: No other OS, fresh install with 30GB free disk space.

Any idea? Thank you.

---

### Post by tekwerx on 2007-12-16
> **patrick71797 said:**
> I have the exact same problem when I try to install 7.10 64 bit edition. I did a check sum of the ISO and it was correct so I burned a second ISO boot CD and it fails in the same exact manner of the first ISO boot CD. If I select the install option it dosent do much but maybe a few commands or loads the kernel and then my screen will go black with my monitor power button light flashing on and off and same with my keyboard lights, flashing on and off and the screen is just black.  Same thing happens when I try and do a check CD option.  It just locks up in any option to install so I just gave up and was checking the forums to see if anyone else was having problems like this. I'm not a linux guru more of a newbie and this was my first ever attempt at installing a linux distro...not very encouraging when you can't even get the install going :(

I'm running, AMD Athlon 64 3200+
1.5 GB of Ram DDR 400
ATI X800 Pro
MSI K8n Neo Platinum MOBO with Nvidia Nforce3 250gb chipset
Ide (0) Primary Master Western Digital 250Gb HD w/ 2 primary partitions one for XP pro and XP pro 64
Ide (0) Secondary Slave Maxtor 40Gb (was gonna use this one for Linux)
Ide (1) Master Sony DVD RW 
Ide (1) Slave CD RW
also have 1 SATA Maxtor 60Gb HD with Vista on it. 

I do have a copy of Ubuntu 7.04 64 bit and 32 bit that I got from my Unix class I took but have not tried installing that version yet.  I was told going from 7.04-7.10 is like in MS terms going from XP to Vista so I was hoping to get 7.10 running.  Any ideas would be much appreciated, again I not really a linux guy, so you have to pretty much speak to me like I am a five year old, total newbie here.

Patrick, try a 32 bit edition, and also try the 7.04 and see what happens.  The upgrades here in Ubuntu arent *that* bad, in my opinion.  You just have to be careful as to what you are doing.  Anyhow, try out the 7.04 32 bit version CD and let us know what happens. Also, by your lights blinking, that does tend to indicate that Ubuntu isn't liking something about your hardware.  I'm unsure as to what that would be though.

---

### Post by tekwerx on 2007-12-16
> **chupy said:**
> Hello, I have the exact same problem too when I try to install 7.10 32 bit edition. The "Live CD" was air-mail to me from Netherlands to Malaysia after I requested it for a free copy from the official website.

Anyway, my laptop is Acer TravelMate 280, current spec (which I upgraded) as following:
- P4 M 2.4GHz
- 1.25GB RAM
- Graphic Card: Intel 82845G
- DVD-RW Drive
- Maxtor Harddisk: No other OS, fresh install with 30GB free disk space.

Any idea? Thank you.

Chupy - Your machine locks up too?  Is there any way you can try to download Ubuntu 7.04 and burn it?

---

### Post by chupy on 2007-12-16
> **tekwerx said:**
> Chupy - Your machine locks up too?  Is there any way you can try to download Ubuntu 7.04 and burn it?

Yes, I encountered the exact same problem as described by Splitrimmz. But I will try download the 7.04 later and install it again. Thanks.

---

### Post by tekwerx on 2007-12-16
> **chupy said:**
> Yes, I encountered the exact same problem as Splitrimmz. But I will try download the 7.04 later and install it again. Thanks.

Yeah, give that a whirl and see how it goes...and I'll give you the same advice as I did above: if that doesnt work, try a different distribution that has a livecd.  It could be that theres something about Ubuntu that doesnt like your hardware.  :(  I hope not, but its something to try.  

If that still doesnt work, then sadly, its out of my league.  Im not an expert, just a moderately knowledgeable linux user.

---

### Post by kajillin on 2007-12-16
Try the text based installer, a simple solution that works.

---

### Post by splitrimmz on 2007-12-16
Thanks for your help in this attempt to get it running.  I'm kind of ticked off that I spent money to order a CD.  However, life goes on.  I was really needing Linux to interface with my Nokia N800.  

Splitrimz

---

### Post by jcats on 2007-12-16
I had a whole bunch of ¨hang¨ problems when I tried to install on a laptop.  I tried 2 different versions of Ubuntu. I downloaded the Alt. version and it sailed right through the install. It asks a bunch of questions but it&#347; a pretty simple proceedure. See if this helps.

jcats

---

### Post by AnonCat on 2007-12-16
Try installing using your integrated graphics instead of the Nvidia card.  When I installed Ubuntu I had to place the lines "Blacklist intel_agp" in the blacklist file in the /etc/modprobe.d folder before I could get my Nvidia card working.

---

### Post by splitrimmz on 2007-12-16
"Try installing using your integrated graphics instead of the Nvidia card. When I installed Ubuntu I had to place the lines "Blacklist intel_agp" in the blacklist file in the /etc/modprobe.d folder before I could get my Nvidia card working."  

Thanks but that is way beyond my level of expertise at the moment.  Splitrimz

---

### Post by splitrimmz on 2007-12-16
> **jcats said:**
> I had a whole bunch of ¨hang¨ problems when I tried to install on a laptop.  I tried 2 different versions of Ubuntu. I downloaded the Alt. version and it sailed right through the install. It asks a bunch of questions but it&#347; a pretty simple proceedure. See if this helps.

jcats

Thanks, I'll try that - I'm in a time crunch at the moment.  Splitrimz

---

### Post by apostate on 2007-12-17
Hey guys,

There is another factor at play besides the graphics card...the monitor. Some refresh rate/default depth combinations do not agree with the limited abilities of the Live CD environment, and this generally goes away once/if you can get ti installed, and use the whole array of xorg options available. When the progress bar fills up all the way, and then the screen goes black, that sounds like (and this is ONLY a theory) your OS has booted successfully, but then once the desktop environment kicks in, the graphics mode is unsupportable.   There are a few things you could try:

#1 - boot up the LiveCD, wait till the progress bar fills up, and the screen goes black. Hit CRTL+ALT+F2

Do you get a terminal and a Linux command prompt? If so, Linux is running, and my theory is definitely correct, your fall-back graphics mode is jacked up. 

#2 - There are some options you can actually type in to the boot menu to force VGA mode, NO FANCY graphics modes whatsoever. This will give you the bare minimum 264 color depth graphical display....enough to get to the desktop and see what you are doing.  Lemme look into it, every distro is different and I don't recall off the top of my head what you need to hit at the menu to enter the command line options, but you can force it to dumb down the graphics even more than "Safe Mode".  This might help on a laptop, or on a system with certain kinds of DELL flat-panels.

Just $0.02

---

### Post by The Cog on 2007-12-17
I don't remember the details, but I think there are also some options you can choose (at the boot prompt where it asks if you want to install, rescue etc). It may be worth trying options like noapic or nolapic.

---

### Post by splitrimmz on 2007-12-17
Good News! for me at least.  Per the quoted suggestion, I can boot it up in non-graphics mode and get a command prompt by typing cnt-alt-f2.  I think it is a command prompt ie. ubuntu@ubuntu:~$  I don't know any commands but I can type in "help" and the command list will scroll (to the end), I don't know how to stop it.  

Now where from here?  I am not literate enough to trouble shoot this obvious graphics and possibly sound problem.  Any help appreciated.

I have a Sony LCD with the NVIDA card listed in a previous post.

Splitrimz







> **apostate said:**
> Hey guys,

There is another factor at play besides the graphics card...the monitor. Some refresh rate/default depth combinations do not agree with the limited abilities of the Live CD environment, and this generally goes away once/if you can get ti installed, and use the whole array of xorg options available. When the progress bar fills up all the way, and then the screen goes black, that sounds like (and this is ONLY a theory) your OS has booted successfully, but then once the desktop environment kicks in, the graphics mode is unsupportable.   There are a few things you could try:

#1 - boot up the LiveCD, wait till the progress bar fills up, and the screen goes black. Hit CRTL+ALT+F2

Do you get a terminal and a Linux command prompt? If so, Linux is running, and my theory is definitely correct, your fall-back graphics mode is jacked up. 

#2 - There are some options you can actually type in to the boot menu to force VGA mode, NO FANCY graphics modes whatsoever. This will give you the bare minimum 264 color depth graphical display....enough to get to the desktop and see what you are doing.  Lemme look into it, every distro is different and I don't recall off the top of my head what you need to hit at the menu to enter the command line options, but you can force it to dumb down the graphics even more than "Safe Mode".  This might help on a laptop, or on a system with certain kinds of DELL flat-panels.

Just $0.02

---

### Post by Quakindude on 2007-12-17
I have the same exact problems, but with newer hardware. 

I can install the 32-bit version with zero problems. Just can't install the 64-bit version. 

I'll try downloading and running the 7.04 though.

---

### Post by apostate on 2007-12-17
Ok. Let's stick with the 32-bit version of 7.10, because the 64-bit version is honesty still more trouble than it is worth for most users, you won't see a big performance difference, and the world is still not quite ready for 64 bit OSes it seems....a lot of application issues. So.....

Boot up the LiveCD, and at the menu, hit F6.

You should see a line of code appear at the bottom, terminating in --

After the -- enter a space and then 

NOAPIC VGA=771

And hit enter to boot it.

Let me know how that goes.

---

### Post by splitrimmz on 2007-12-18
Hello, I entered NOAPIC VGA=771 and it still booted up to the blank screen.  Any other suggestions appreciated.  Splitrimz

---

### Post by AmericanYellow on 2007-12-18
I have a HP tx1220 and I had the same problem. My understanding of the problem after reading multiple posts in the forum is that certain hardware components are preventing Ubuntu from booting. In my case, I had to do the following to get Ubuntu to boot:

Load Live CD and at the menu press "F6". A boot line came up and I added the following to it:
[I]
doscsi noapic nopcmcia[/I]

also my laptop came with a remote and I had to remove it during the the boot.

This fix was specific to my laptop model and it might not work for you. You should search the forums for others that I have a similar laptop and see what worked for them.

---

### Post by itseffinkasey on 2007-12-18
Hello all. I had the exact same problems that you are having when i was trying out the LiveCD. After about 30 minutes of messing around I finally found out that I had to press F6 and then just type noapic and hit enter, and everything worked fine from there. Honestly I'm a noob and I was searching the forums to find out why exactly I have to enter noapic when I'm either installing from the initial boot menu. Again I am no expert not even close and I don't know how I ever came up with the idea that I had to type in "noapic" all on my own.

---

### Post by Quakindude on 2007-12-18
I got the 64-bit version of 7.10 installed and running now. However, I had to swap in my 7950GT video card to do it. I'll have to find a way to get my 8800GTS working in this version because the 8800GTS didn't work in 7.04, 6.10 or 6.06LTS.

---

### Post by bubblefish on 2007-12-18
Man, I was lucky, I guess. I have a Dell Inspiron B120, cheapest Dell laptop I could get. I first loaded in Xandros distro which came with a Linux Magazine (I forget which). It installed like a dream, but it wanted to sell me stuff from Xandros. Next, I got a disk with a book of "Ubuntu Linux for Dummies" (that's me). I deleted the partition Linux was on and installed Ubuntu 6.10. No problems at all. It asked me if I wanted to upgrade to 7.10, and I clicked yes, and voila! Maybe I inadvertantly did what was suggested: load a 32 bit linux first. I got the book at Barnes and Noble. It cost 30 smackers, but what the heck, Windows cost a lot more. I might just push XP out the window and go all Linux if I can figure out how to make everything work.:)

---

### Post by jken146 on 2007-12-18
> **splitrimmz said:**
> Good News! for me at least.  Per the quoted suggestion, I can boot it up in non-graphics mode and get a command prompt by typing cnt-alt-f2.  I think it is a command prompt ie. ubuntu@ubuntu:~$  I don't know any commands but I can type in "help" and the command list will scroll (to the end), I don't know how to stop it.  

Now where from here?  I am not literate enough to trouble shoot this obvious graphics and possibly sound problem.  Any help appreciated.

I have a Sony LCD with the NVIDA card listed in a previous post.

Splitrimz

That's good news, in a way.  If I were you I'd download the alternate CD and install Ubuntu anyway.  If you're not sure you want to do an install yet, I secondthe suggestions made above about trying other distos' live CDs.

---

### Post by splitrimmz on 2007-12-18
NOAPIC VGA=771 did not work, booted up to black screen.  NOAPIC by itself did not work either.

Splitrimz


> **apostate said:**
> Ok. Let's stick with the 32-bit version of 7.10, because the 64-bit version is honesty still more trouble than it is worth for most users, you won't see a big performance difference, and the world is still not quite ready for 64 bit OSes it seems....a lot of application issues. So.....

Boot up the LiveCD, and at the menu, hit F6.

You should see a line of code appear at the bottom, terminating in --

After the -- enter a space and then 

NOAPIC VGA=771

And hit enter to boot it.

Let me know how that goes.

---

### Post by AmericanYellow on 2007-12-19
did you try *noapic nopcmcia* ?

---

### Post by splitrimmz on 2007-12-19
did you try noapic nopcmcia ?

Yes, same result, blank screen..

---

### Post by apostate on 2007-12-19
Ok.

When it gets to the blanks screen, hit CRTL+ALT+F2 to get a command line interface like this:

ubuntu-user@ubuntu:$

Type 


*startx*

And press ENTER. You will probably get an error code, please post what it is.

---

### Post by splitrimmz on 2007-12-19
STARTX

(WW) VESA: no matching device section for instance (busid pci:1;0;0) found
(EE) VESA(0); CANNOT READ V.BIOS (3)
(EE) SCREENS FOUND, BUT NONE HAVE A USABLE CONFIGURATION
XIO: FATAL IO  ERROR 104 (CONNECTION RESET BY PEER) ON X SERVER "0.0" AFTER 0 REQUESTS (0 KNOWN PROCESSED) WITH 0 EVENTS REMAINING 

iT SOUNDS PRETTY DRASTIC TO ME...!

---

### Post by apostate on 2007-12-19
Ok.....the NVidia card + your monitor just aren't getting along. You can try this at the command line 

sudo dpkg-reconfigure xserver-xorg

And see if there is another driver you could use.  Ostensibly, you want VGA mode, VESA should work...but it didn't, so I don't know if there is a "safer" driver than that.  

My conclusion:  You need an NVIDA driver, it's as simple as that. So....you could try using the command I gave you above, and using the "NV" driver, which is the open-source NVIDIA driver. Or, failing that, try the alternate install disc, with the Debian installer. 

The LiveCD relies on getting a Gnome desktop up, which means you need a driver that will get you there so you can install a driver...catch 22. Rest assured, your NVIDIA card does work under Ubuntu, you just need to get it installed. If using the NV driver doesn't work for you, you will prolly need to abandon the LiveCD and just get the installer disc.

Sorry, I'm running out of ideas.

---

### Post by apostate on 2007-12-19
That machine doesn't have a cheap-o onboard graphics card you could fall back on just for the install, does it?

---

