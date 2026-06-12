---
title: "Display drivers (nouveau / nv) for iMac G4 700/800"
date: 2013-04-02
forum: Apple Hardware Users
---

### Post by rsavage on 2013-04-02
This post is for nVidia users who can't get the nouveau driver working.  Early iMac G4 users typically seem to fall into this bracket.  For more detailed information see here [https://wiki.ubuntu.com/PowerPCFAQ#Troubleshooting](https://wiki.ubuntu.com/PowerPCFAQ#Troubleshooting) .

These instructions are for 12.04 only.

1. Download an 'alternate' iso or 'mini' iso and install as normal.  If you want to use a 'live/desktop' iso then you can follow or adapt the instructions in this [http://ubuntuforums.org/showthread.php?t=2079873&p=12336938#post12336938](http://ubuntuforums.org/showthread.php?t=2079873&p=12336938#post12336938) post.

2. After installation, make sure you have an ethernet cable connected and boot into single user mode. So at the yaboot prompt type:
```

Linux nomodeset single

```
This will boot you into a root prompt so be careful what you type next!

3. The best alternative to the nouveau driver is the nv driver.  You can compile it yourself (there are instructions linked in the FAQ), or you can install a pre-compiled version:
```

wget -O /tmp/nv.deb http://ubuntuone.com/6QVpmfHCU3YmHlik7lred9
dpkg -i /tmp/nv.deb

```

4. Now you need to create an xorg.conf. This is a basic one:
```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nv"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

The following will download the above file and move it into the right place for you:
```

wget -O /etc/X11/xorg.conf http://ubuntuone.com/6loNPRkiKluH2ZOXt8HENV

```

5. Edit your yaboot.conf file to add the 'nomodeset' parameter permanently:
```


nano /etc/yaboot.conf

```

Add 'nomodeset' at the end of the append line(s).  For example:
```

image=/boot/vmlinux
    label=Linux
    read-only
    initrd=/boot/initrd.img
    append="quiet splash nomodeset"

```
Every parameter inside the quotes should be separated by a space. Save (ctrl+o) and exit (ctrl+x), then type the command
```

sudo ybin -v

```
to copy the file across to the boot partition. 

6. You can now reboot into a desktop:
```

reboot

```

Lots more information in the FAQ and Known Issues pages:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by str8bs on 2013-04-02
Not certain, but in addition to iMac G4 users, I think this workaround may apply to any PPC with geforce mx or geforce go.

---

### Post by clickgear on 2013-04-11
Thank you for this set of instructions.  It appears to have gotten me past the hang on boot problem that I was having with my PowerMac 3,5 Nvidia GeForce2 MX.  However, when I ran the dpkg command I got errors, saying it couldn't configure the installation.  Is it OK to ignore this?

Thanks,

Kurt

---

### Post by rsavage on 2013-04-11
What is the error message?  It doesn't sound like it has installed correctly, and if that is the case it won't work.

---

### Post by rsavage on 2013-04-11
Oh I see the problem from the other thread you are posting on.

> 
I used the mini-iso CD to try and install the base system (without even any desktop yet)


If you haven't got any xorg packages installed then it will throw an error.  

Sometimes when you install the missing package dependencies (in this case the xorg packages) the failed package will continue with its installation.  Sometimes you will have to re-run the dpkg command.  I can't say with certainty what it will do.

---

### Post by mörgæs on 2013-06-26
Thanks for a good guide. I added some [advice]("http://ubuntuforums.org/showthread.php?t=361236&page=86&p=12707046&viewfull=1#post12707046") for the G4 in case someone else is struggling to get it working.

Is there a chance of getting a pre-compiled nv driver for 13.04, please?

---

### Post by abtabt on 2013-06-27
> **mörgæs said:**
> 

Is there a chance of getting a pre-compiled nv driver for 13.04, please?

i think we have same hardware [http://www.everymac.com/systems/apple/imac/specs/imac_800_fp_macosx.html](http://www.everymac.com/systems/apple/imac/specs/imac_800_fp_macosx.html)

you can try a usbstick with live Lubuntu 13.04 and use nvidiafb driver (in my case 768 mb memory but i think you can have less to get it work

read [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F)

To copy an iso to a USB stick
and
Persistent Live USB

both work for me ( Persistent Live USB work very well too try if things works )

i choose OS/HDD/USB with alt key pressed

---

### Post by mörgæs on 2013-06-27
Thanks, I'll give it a try. 
Do you have a guide for activating nvidiafb?

---

### Post by abtabt on 2013-06-28
> **mörgæs said:**
> Thanks, I'll give it a try. 
Do you have a guide for activating nvidiafb?


you need to unhash nvidiafb in /etc/modprobe.d/blacklist-framebuffer.conf

code

sudo nano /etc/modprobe.d/blacklist-framebuffer.conf

change to
#blacklist nvidiafb


you need a xorg.conf 

code

sudo nano /etc/X11/xorg.conf 

###with this xorg.conf , if not you get 8 bit 
###TBA@
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nv"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "nVidia"
	Monitor    "Monitor"
        DefaultDepth  16
	SubSection "Display"
		Viewport   0 0
		Depth     16
                Modes   "1024x768"
	EndSubSection
EndSection

this is for Persistent Live USB 

if you will use only Live usb read this  [http://ubuntuforums.org/showthread.php?t=2090462](http://ubuntuforums.org/showthread.php?t=2090462)

and the boot time will take some time (usb 1.1 and if the usb is slow so wait some minutes)

---

### Post by moore.bryan on 2014-01-19
I know this thread is ancient and unlikely to be followed much any more, but I'm going out on a limb here. 

I've successfully installed 12.10 on my flowerpot, but can't get x to run for the life of me. I've compliled the nv driver and written an xorg.conf file, but when I try and start xfce I get a black screen with a non-blinking cursor and nothing useful in three Xorg.log.0 file. 

Any ideas and/or suggestions would be great!

---

### Post by este.el.paz on 2014-01-19
moore_bryan:

How's the weather in hatboro these days?  I grew up near there . . . .  I don't know if I can help you, either I don't know enough, or can't tell enough from what you have posted to know what might have been missed by you.  But, first the iMac is apparently one of the more difficult platforms to get linux running on . . . .  And, whether it is relevant or not, is the 12.10 version the "PPC" version?  Other than that, if you can get to single user you might be able to find the boot parameters that will get you into a GUI . . . .  I recall that when I was trying to get my iMac to run something linux I had a long list after the "live nomodeset . . . ."  They were all listed when I hit the "tab" key after the first log in window, and I just strung them together.

But, the gentleman who might be able to give detailed help is "abtabt" or the OP of this thread "rsavage" if either of them stop by.  In lieu of that I'd suggest the "rsavage" thread "Tester's wanted for 12.04" and try reading through there for any tips . . . which is my best suggestion . . . first try to get 12.04 running on your computer before trying to move forward . . . .  rsavage was offering an .iso with the pre-compiled nv driver there, but had to take it down.  But it's not the only choice; with "str8bs" help I set up an xorg.conf file that used the fb driver, and that was fine as well . . . nv is more "native" for the iMac I suppose.  I now am running Xu 12.04 with an nv driver that I compiled following the ubuntu PPC wiki . . . and all is well, except for no "suspend" function, and I get a "the system has crashed" error every time I log into it . . . which I think was part of the beta version of it.

The other option is to try a Lubuntu for PPC .iso and see how that goes, "Philw" seems to have some instructions out there for 13.10?? but, since it has been so difficult and time consuming for me to get something to run at all on my iMac G4 . . . I'm sticking with 12.04 until support runs out or maybe longer . . . .  At one point I was downloading the LiveDVD's of Lu for PPC and testing them out, but very difficult to get them to work; on my iBook with the radeon driver it's a lot easier to move up . . . .  Good luck, hopefully someone else can jump in and offer some pointed questions; if not, you'll have to try to read more to find the right string of boot params to get you started; or figure out where you need to make some adjustment, perhaps something in your xorg file, etc . . . .

e.e.p.

---

### Post by moore.bryan on 2014-01-19
Thanks for the quick reply on what I thought might be a dead thread, e.e.p; where in Hatboro? Small world...

Well, long story short I'm authoring this response on my iMac "Flowerpot" running a jerry-rigged version of Saucy. I originally installed Quantal and after endless hours of fiddling, got a GUI. I then, stupidly, upgraded when prompted to 13.10. Everything was fine until I tried to install Lubuntu because XFCE is shockingly slow on this machine and something SNAFU-ed. Eventually, I identified the issue as an xserver package being update and not playing nicely with my self-compiled nv driver. 

I tried recompiling the driver, but there's a reference somewhere in the build to a file which no longer exists in Ubuntu and, alas, there's no way to work around it without rewriting the whole code. So... I tried downgrading the one xserver package and, voila, here I am. 

I am, however, considering going back to Openbox for my DE because XFCE is so unbelievably slow on this machine.

---

### Post by este.el.paz on 2014-01-19
m.b:

Well, the thread probably is dead, but I'm subscribed to a number of these "old" iMac threads . . . .  Saucy running on an iMac, OK, well you obviously are light years ahead of me in terms of skilz, I think "abtabt" might also have, is that 13.10? running on his iMac, but apparently took some fiddling somewhere to get that to work.  One of my constraints in terms of details is that I believe I did my Xu 12.04 install in Dec of '12? after a number of months of trying different linux's on it . . . it began to have multiple kps, making it hard to figure out if it was the install or the hardware . . . and I finally stopped using it for 7 or 8 months . . . .  And then a few months ago took in to a shop for diagnosis . . . and we're back . . . but in terms of the "retro-nv" install process that I followed from the PPC wiki . . . at that time there was no problem with the process . . . no errors.  And I recently did a major update after the idle time, and nothing "broke" in terms of the video . . . perhaps with the system upgrade something might get changed that would then "mess" with the nv driver . . . so far for me that hasn't happened.

But, in terms of the "slowness" of XFCE, running Xubun 12.04 partition I would not say that it is "slow" at all . . . compared to 10.4.11 it is "faster" on the internet . . . and so forth . . . mousing around is faster.  It does take a moment or three to launch some apps, like Mail, there is a moment of "hmmm, let's think carefully about this, before we do anything untoward . . . ."  But, once loaded things move just fine . . . .  I would use it most of the time just to make a point of it, but, unfortunately for me the lack of suspend thingie makes it not so practical . . . so for the most part I'm running my 10.4.11 partition using TFF . . . overall OSX does a very good job still of running the computer.

"abtabt" seemed to suggest that he had overcome the suspend issue using Lu 13.10???, but when I asked him/her about it, wanting more details from him, there was no response . . . must be too "complicated" to try to talk about online . . . ???  But, it seems like you got passed your non-flashing prompt window . . . if you think Openbox is faster then by all means try it out; I think at one point I had the option of booting into an Openbox session in my iMac and it just went to a black screen . . . so in the midst of all the other problems I was having with the computer I just went back to Xubun and left it at that . . . .  Main thing is, if you get anything to run on the iMac, be happy . . . .

e.e.p.

PS:  Not "of" Hatboro . . . grew up in Montgomery cnty . . . somewhere nearby to Hatboro . . . but, a long time ago.

---

### Post by abtabt on 2014-01-20
Hi

this is a way to test even  suspend  without install on hd

[http://ubuntuforums.org/showthread.php?t=2090462](http://ubuntuforums.org/showthread.php?t=2090462)

i use for day jobbs Lubuntu 12.04 LTS 

if you need more info you are welcome

i like Persistent Live USB

edit nvidiafb is not in 13.10 , 13.04 is last with nvidiafb

---

### Post by este.el.paz on 2014-01-20
> **abtabt said:**
> Hi

this is a way to test even  suspend  without install on hd

[http://ubuntuforums.org/showthread.php?t=2090462](http://ubuntuforums.org/showthread.php?t=2090462)

i use for day jobbs Lubuntu 12.04 LTS 

if you need more info you are welcome

i like Persistent Live USB

edit nvidiafb is not in 13.10 , 13.04 is last with nvidiafb

@abtabt:

Thanks for posting here to help give more insight into the iMac and what works . . . how to test out, etc . . . .  Looks like Bryan figured out how to get passed the black screen with his system, perhaps other issues will crop up for which there might be questions that you could help out with.  For me, the Xu 12.04 is fine enough, question will be whether the next LTS version will be able to work with PPC and/or the iMac . . . without the "retro-nv" or with it?  But it seems like you are saying "fb is not in 13.10" . . . so fb is no longer an optional driver after 13.04????  "moore.bryan" is reporting that he had some problem with compiling the retro-nv driver . . . ??

e.e.p.

---

### Post by este.el.paz on 2014-01-21
> **moore.bryan said:**
>  Everything was fine until I tried to install Lubuntu because XFCE is shockingly slow on this machine and something SNAFU-ed. Eventually, I identified the issue as an xserver package being update and not playing nicely with my self-compiled nv driver. 
I am, however, considering going back to Openbox for my DE because XFCE is so unbelievably slow on this machine.

@m.b:

Just to follow up on the "XFCE is slow, and I'm going back to Openbox" comments . . . so, you probably know that if you add the LXDE package, you also get Openbox?  And in the past when I tried to log in the OB I just found a grey screen, so I assumed it was a video problem.  But, based upon what you said, I tried it again and then clicked around on the grey . . . and then right clicked . . . and go the mini drop down menu toolbar . . . .  So I messed with it a bit, and yeah, maybe windows open a bit faster with it . . . the "heirloom-mail" app seemed to crash on launch . . . and then changed the window manager from "openbox" to Wfxm??  and lost everything.  Rebooted thru TTY and got it back . . . .  So, maybe a little interesting, maybe a little faster, but the grey desktop, with nothing on it . . . can that be changed?

e.e.p.

---

### Post by moore.bryan on 2014-01-23
With openbox, all you get is a desktop--i.e., no panel, no background, nothing--which was how its developers wanted it. You can use feh to set a background in the openbox config file... but I can't remember how to do it because it's been so long. So, I'm going to have to mess around with it a bit. I tried launching lxde and almost ruined my install. I think the slowness is a side-effect of coming from a modern Haswell to the iMac's well-aged processor. :-)

The openbox site has a plethora of info...
[http://openbox.org/](http://openbox.org/)

---

### Post by este.el.paz on 2014-01-23
> **moore.bryan said:**
> With openbox, all you get is a desktop--i.e., no panel, no background, nothing--which was how its developers wanted it. You can use feh to set a background in the openbox config file... but I can't remember how to do it because it's been so long. So, I'm going to have to mess around with it a bit. I tried launching lxde and almost ruined my install. I think the slowness is a side-effect of coming from a modern Haswell to the iMac's well-aged processor. :-)

The openbox site has a plethora of info...
[http://openbox.org/](http://openbox.org/)

Thanks for the further reply . . . yes, playing with Openbox w/o the desktop eye candy . . . is "faster" . . . .  But, it is curious how the same machine can be rendered "slower" or "faster" by the simple choice of DE . . . ????  I don't know why lxde would "almost ruin your install" . . . as Lubuntu remains a very viable choice for the PPC system . . . I have lxde, xubuntu, xfce, and openbox DE as choices I can log into . . . from 12.04 . . . so it's difficult to know if the 13.10 base system you installed was "back ported" or whatever for PPC, there might be some critical differences in some minor detail which cause a problem for lxde??  Meaning if it wasn't a "PPC" .iso . . . ???  Some folks here seem to think that doesn't mean anything, but then it seems like they know that "PPC" is different than Intel, etc . . . .

BTW, in the rsavage thread I mentioned "Tester's wanted for 12.04" . . . he posted some links for upgrading the xfce DE from something 4.8 to something 4.10???  and that ***might*** do something to speed it up??  I did do something with it on one of my PPC units, but can't remember what happened with it . . . it's not radically different.

e.e.p.

---

### Post by moore.bryan on 2014-01-25
Different DE's use differing amounts of RAM and CPU cycles to simply operate; just look at GNOME Shell vs. Unity vs. KDE vs. XFCE, etc...

I can't even use a login manager, for some reason, as both lightdm and lxdm breaks my system; so, I login via CLI and manually launch XFCE.

I installed my system from a 12.10 PowerPC disk and then upgraded--stupidly at first until I fixed the broken packages and downgraded xserver--to Saucy via the dist-upgrade program that autoruns.

I think I'll hit-up rsavage's thread and see about upgrading XFCE...

Nevermind about upping XFCE, as I already have 4.10... which makes sense because I'm running Saucy...

---

### Post by este.el.paz on 2014-01-25
m.b:

Interesting that you can't get lightdm to work . . . since it is "light" . . . and seems to be the choice of the hardcore slim to none linux guys--the smaller the footprint the better, etc.  You might still read through that thread because there was some discussion there about the iMac with rsavage and or str8bs or abtabt . . . all of whom seem to have some real insights into the issues of getting something linux to run on the iMac . . . .  

It seemed like it keyed around the nv driver and getting the xorg.conf file set up right . . . .  I'm not sure, but I don't think the 12.10 had the nv driver any more . . . you mentioned having some issues with that, perhaps that's a key point??  You obviously can run saucy on it, but, with various problems . . . .  abtabt might be able to comment on that if he gets a chance . . . i.e., how far forward you can go on the G4 iMac vs upgrading.

My only wish/bucket list wish for the iMac would be to get "suspend" working . . . rsavage says "not gonna happen with nvidia card" . . . abtabt seems to say "it's easy" . . . .  Finally got the iMac set up with more RAM, but still no dice; my iBook does do suspend with its radeon card, but lately it's been finicky on revival . . . not always doing it and needing the TTY log in to reboot, etc--it seems to be hit or miss in the PPC realm.

Anyway . . . it's all part of the fun . . . the almost working, the not working except during the full moon, etc.

e.e.p.

---

### Post by moore.bryan on 2014-02-03
I have no need for suspend, so it means nothing to me... I would like my iLamp to *reliably* start-up every time I hit the button, though. With neither rhyme nor reason, it just won't load at first; however, if I just keep forcing shut it down and restarting, eventually it works. Weird.

---

### Post by este.el.paz on 2014-02-03
> **moore.bryan said:**
>  With neither rhyme nor reason, it just won't load at first; however, if I just keep forcing shut it down and restarting, eventually it works. Weird.

@m.b:

Perhaps someone with some more technical knowledge will reply to this issue . . . I've mentioned the "nv" driver as being the better driver, although I did get the fb driver to work, somebody said that fb driver isn't available any more--I don't know if you've posted back on which driver you are using?  

But, when you say "it just won't load at first" . . . what does that mean, specifically?  Nothing happens when you push the power button?  You get a black screen?  You get to the splash window?  Or, you get to the cli after the first boot window, and then you get to  . . . "xx x x prominent . . . something" . . . and then it goes black and doesn't recover?  More details might be more helpful.  

Personally I experienced a lot of kp's in the last year on my iMac . . . and it took awhile to figure out that's what was happening, because I was moving back and forth between OSX & linux . . . so all kinds of problems were happening with the computer, trying to boot it, etc . . . spent a lot of time trying to figure out what might be the problem with the operating system . . . ran the apple hardware test . . . nothing showed up, except in the linux disk utility one sector was showing bad . . . .  Finally took it in to a pro shop and it too them a long time to find out there was "bad RAM" . . . they replaced it and I got it back after a month . . . and, instant KP . . . took it back to them and they replaced the replacement and the kps are much better, if not almost non-existent . . . .  

But, before the RAM was replaced, many problems trying to get linux to boot, trying to get an internet connection to . . . intermittent booting . . . .  I noted much of that in that [PPC] Tester's wanted for 12.04 thread because I thought it was relating to getting it running on the iMac . . . so you might recognize something from what I posted there???

e.e.p.

---

### Post by moore.bryan on 2014-02-04
> **este.el.paz said:**
> Perhaps someone with some more technical knowledge will reply to this issue . . . I've mentioned the "nv" driver as being the better driver, although I did get the fb driver to work, somebody said that fb driver isn't available any more--I don't know if you've posted back on which driver you are using?  
I'm using the nv driver. Although there are those who've gotten nouveau to work with a similar set-up, mine seems particularly unique for some reason.

> But, when you say "it just won't load at first" . . . what does that mean, specifically?  Nothing happens when you push the power button?  You get a black screen?  You get to the splash window?  Or, you get to the cli after the first boot window, and then you get to  . . . "xx x x prominent . . . something" . . . and then it goes black and doesn't recover?  More details might be more helpful.  
During boot, after yum, I'll get some boot messages on the screen and it will just "hang" sometimes. Checking all boot, dmesg, and Xorg logs provide no insight. If I hard reboot once--sometimes two or three times--it seems to "unstick" the hang and I get to a CLI, at which I can login and start X.

> ... "bad RAM" . . . they replaced it and I got it back after a month . . . and, instant KP . . . took it back to them and they replaced the replacement and the kps are much better, if not almost non-existent . . . .  
New(er) RAM, so I don't think that's the problem...

> 
But, before the RAM was replaced, many problems trying to get linux to boot, trying to get an internet connection to . . . intermittent booting . . . .  I noted much of that in that [PPC] Tester's wanted for 12.04 thread because I thought it was relating to getting it running on the iMac . . . so you might recognize something from what I posted there???
Yeah, I looked through the thread, but nothing stuck-out as the same--or even similar--to what I'm experiencing, though; thanks, any way!

---

### Post by este.el.paz on 2014-02-04
> **moore.bryan said:**
> I'm using the nv driver. Although there are those who've gotten nouveau to work with a similar set-up, mine seems particularly unique for some reason.

During boot, after yum, I'll get some boot messages on the screen and it will just "hang" sometimes. Checking all boot, dmesg, and Xorg logs provide no insight. If I hard reboot once--sometimes two or three times--it seems to "unstick" the hang and I get to a CLI, at which I can login and start X.

New(er) RAM, so I don't think that's the problem...

Yeah, I looked through the thread, but nothing stuck-out as the same--or even similar--to what I'm experiencing, though; thanks, any way!

@Bryan:

Only other question I have is just like with Bosler whom I asked, "Do you have OSX installed on your computer?" . . . same question to you.  Seems like the general PPC/Mac wisdom is to have OSX loaded on a partition to make certain firmware tasks easier . . . maybe not too important for firmware at this late date, but, for testing to see whether your issues are happening in both OSX or just linux . . . it might be helpful or instructive for diagnostic purposes . . . to distinguish software v hardware issues???

But, in terms of what you are describing with "nothing showing up in dmesg" etc, etc, and the various boot problems, that actually is very similar to what I experienced.  Is that in and of itself traceable to RAM problems?  Difficult to know, since for now my version of 12.04 is installed and the retro-compiled nv driver process I did while all this wackiness was going on with the iMac, my next install would probably be the next LTS version if it will be ported to PPC, rather than messing with getting a non-LTS version . . . .  Meaning, I'm not going to experiment with 13.10 to see if I can crash my computer in the process . . . just sayin' : - )))  

But, in getting back to RAM, not sure if you can rule that out, as I had a brand new RAM stick installed . . . professionally . . .  and they "tested it" and ran it for whatever time, and literally within a couple hours of me getting it back . . . same problems with KP crashes, etc.  Took it back and after testing it for a long while they found it to be "bad" already; got a second new stick under warranty and so far, so good . . . finally seems like the 12.04 error reports of "Your system has crashed now or in the past" seem to be . . . not happening . . . .

e.e.p.

---

### Post by rsavage on 2014-02-09
You might like to combine forces with this chap [http://ubuntuforums.org/showthread.php?t=2203756](http://ubuntuforums.org/showthread.php?t=2203756)

---

### Post by stefanos3 on 2014-04-04
Hi Bryan,

Could you please let me know how you solved the 'black screen with non-blinking cursor' issue? I'm having exactly the same with debian wheezy, running the nv driver (backported from jessie), with nouveau blacklisted. I'm running an imac G4 800MHz (the 'lamp' model)

Thanks

---

### Post by moore.bryan on 2014-07-29
Sorry I didn't get around to checking this thread until now, stefanos3, are you still having an issue?

---

### Post by digerati2 on 2014-09-02
I have an iMac G4 800MHz and am trying to install Ubuntu 14.04.1 alternate. As to be expected, I am having graphics card issues. When I boot normally, I get a screen that changes colors and eventually goes dark. When I boot with 'Linux nomodeset', I get a normal Ubuntu loading splash screen and then a black screen with a multi-color mouse pointer forever. When I boot with 'Linux nomodeset single', everything works very well from the command line. 

I tried to download the nv.deb file mentioned by the OP, but the file is no longer available from ubuntuone. Does anybody know where I can obtain this driver? 

Also, looking for some advice whether to recycle this old machine or if it will be a decent linux server. Any feedback regarding stability? I'm already very satisfied with the performance, but 10.4 is no longer a viable operating system so I'm hoping to turn this into a usable machine. 

Thanks,
Brett

---

### Post by este.el.paz on 2014-09-02
> **digerati2 said:**
> I have an iMac G4 800MHz and am trying to install Ubuntu 14.04.1 alternate. As to be expected, I am having graphics card issues. When I boot normally, I get a screen that changes colors and eventually goes dark. When I boot with 'Linux nomodeset', I get a normal Ubuntu loading splash screen and then a black screen with a multi-color mouse pointer forever. When I boot with 'Linux nomodeset single', everything works very well from the command line. 

I tried to download the nv.deb file mentioned by the OP, but the file is no longer available from ubuntuone. Does anybody know where I can obtain this driver? 

Looking up the the list in this thread to "stefanos3" he mentions "backporting" the nv driver "from Jessie" . . . in terms of how to do that or which distro Jessie is part of . . . don't know.

>  Also, looking for some advice whether to recycle this old machine or if it will be a decent linux server. Any feedback regarding stability? I'm already very satisfied with the performance, but 10.4 is no longer a viable operating system so I'm hoping to turn this into a usable machine. 

Thanks,
Brett

Brett:

I have 12.04 Xubuntu/Lubun  on a partition of my iMac 800, personally I would say to try 12.04 . . . because it seems like PPC support in 14.04 is a diminishing reality . . . i.e., the nv driver being difficult to find . . . .  I just upgraded my iBook G4 to 14.04 when software updater asked me if I wanted to upgrade . . . .  Previously in 12.04 on the iBook the install was flawless . . . whenever that was 1.5 years ago???  The iMac was more difficult and I have no thought to try to bring it up to 14.04 . . . but, I don't know what I'm doing in linux . . . I just follow instructions from people that do.  But, if you go back to the beginning of this thread, guys like STR8BS who were giving detailed help . . . are no longer spending time here . . . .  So, if you read through the thread recently you can see that moore.bryan seems to have a "working" version of 14.04 on an iMac 800 . . . but, no "suspend" . . . and I believe that "sound" seems to have problems in PPC 14.04 . . . and then the "video" issues that you are experiencing.  So, more and more problems are creeping in and/or are not being dealt with as they previously were . . . .

So, that was my subtle way of saying that right now on my iMac 10.4.11 with Ten4Fox for the browser is actually running the iMac better than 12.04 . . . mainly because I "need" suspend/sleep . . . watching videos is something that now both OS's have issues with . . . 6 - 8 months ago I was complaining to the Ten4Fox dev that "I can watch videos in 12.04 FireFox" . . . but . . . now, no . . . .  So Ten4 has some suggestions for "Mactubes" or something and it sorta works.  But, I recently punched the RAM on the iMac to a raging 1 GB and I use it mostly to do what I'm doing here . . . check emails and post of various linux or OSX related forums . . . for that the iMac is fine.  For a server?  don't see why not, Debian is the original server distro, so check into them . . . Ubuntu is known for its more user friendly desktop/GUI . . . .  In terms of getting back to the iMac and installing 14.04, for sure you will need an xorg.conf file for the iMac . . . possibly from some thread here written by "rsavage" or "str8bs" . . . or from the "linux.be"  web site . . . and then you will need a driver . . . at one point before I got the nv driver "retro-installed" str8bs gave me instructions for using the "fbdev"??? driver . . . which was fine, so if you could find that thread it might give you the details . . . .  It's not the easiest install on the iMac . . . but it can be done--I'd say try 12.04 Xubuntu for starters . . . .

e.e.p.

---

### Post by moore.bryan on 2014-09-03
I'd agree, completely, with este.el.paz; having played with pretty much all releases on my iLamp, precise plays nicer than them all. I've been able to compile the nv driver from source on trusty and utopic, but it won't work and gives the same multicolor screen as the failed nouveau driver does. At one point, I was able to successfully use nvidiafb to get a usable desktop, but that seems to have just been dumb luck.

Like I wrote, I'd install precise and use that if I were you...

---

### Post by este.el.paz on 2014-09-03
> **moore.bryan said:**
> I'd agree, completely, with este.el.paz; having played with pretty much all releases on my iLamp, precise plays nicer than them all. I've been able to compile the nv driver from source on trusty and utopic, but it won't work and gives the same multicolor screen as the failed nouveau driver does. At one point, I was able to successfully use nvidiafb to get a usable desktop, but that seems to have just been dumb luck.

Like I wrote, I'd install precise and use that if I were you...

@m.b:

Thanks for the comments . . . I think I've also moved through a number of drivers trying to get 12 to work . . . rsavage was offering a version of 12.04 Xubuntu that had the nv driver installed, but had to take it down . . . by that time I had already followed the FAQ?? instructions and retro-installed it.  

But, along with the driver there was some adjustment in the xorg.conf file for the horz/vert refresh rates that seemed to finally "get it right" . . . all of this might be find-able . . . possibly on the "Tester's wanted for 12.04 PPC"?? thread, if that is available.  Not sure if anybody posted a working xorg.conf file in this thread, I saw rsavage put an abbreviated one early in the thread showing "nv" as the driver and not much else . . . str8bs helped me out with the one I'm using . . . .  The fastest might be wget-ing one from Jereon D's "linux on mac" site . . . and test them out until the best one is found.

Also rsavage has been commenting about getting the "nouveau devs to get their driver to work for the iMac" . . . haven't had time to deal with that process, but might be a key point in being able to move the iMac up in the upgrade cycle . . . .  But, also mentioning again that the fbdev driver was not that bad . . . but, don't know if that is still around or also has gone the way of the . . . Jedi . . . .  : - )

e.e.p.

---

### Post by moore.bryan on 2014-09-03
> **este.el.paz said:**
> But, along with the driver there was some adjustment in the xorg.conf file for the horz/vert refresh rates that seemed to finally "get it right" 
For me, I *couldn't* set the refresh rates or it wouldn't work; I did, though, always have to set a default depth. In fact, setting a modeline also left everything "broke."

[quote=este.el.paz]Also rsavage has been commenting about getting the "nouveau devs to get their driver to work for the iMac"[/QUOTE]
rsavage is an invaluable resource... if nothing else, beg his help!

---

### Post by dawg161 on 2014-11-24
Hi everyone. First, thank you all, especially str8bs, linuxopjemac and este.el.paz for all the work you've done trying to get the iMac G4 to remain useful. It seems this model is unique in its quirks, which is unfortunate given what a beautiful object it is. The trick is to find some use for it as it gets harder and harder to use.

The last GNU/Linux system that I successfully got working on mine was Debian Squeeze. I've never got the thing to boot without nomodeset for nouveau. It seems that y'all have found workarounds (such as compiling nv from the gnu/bsd port) to get it through the Wheezy/Precise life cycle. That's good, since Precise will be supported for a while yet. But I'm worried this trick is coming to an end

I tried compiling the nv driver for Debian Jessie about a week ago, and got the non-blinking cursor that others have described. Depressingly, it was clearly linked to the compiled version of nv. With no xorg.conf file, the machine would still pick nouveau with nomodeset, and boot x with terrible colors. But if nouveau was removed, or if xorg.conf specified nv, I got the nonblinking cursor. I'm at the end of my ability, and I don't think it's reasonable to expect that the Debian developers are going to spend time and resources on this old, quirky machine. If they'd just supply an updated nv, it would be great, but as far as I can tell from searching, it's just a few of us that need this.

I tried Gentoo, but never could get yaboot to compile. So that was a dead end for me.

My solution has been to give NetBSD a try. It needed several workarounds even from the PowerMac G4 instructions on the NetBSD website, but I managed to figure out everything but getting HFS formatting on the boot partition (something's wrong with the utility so I'm just booting from the bootloader on the install CD.) I need to post my method in some appropriate place.  But the computer's back in use. At this point, even with Squeeze, I was just using the thing to display recipes (it sits on my kitchen counter) and control the home media center. So I have a very minimal NetBSD install, with just twm as a window manager. I run banshee and iceweasel from the Debian server that is our home media center over X, and the graphics look great. KDE, GNOME, and XFCE are also available, but I'm happy with what I've got. 

Anyway, if you successfully have something working on the iMac, keep it! But if not, NetBSD is a nice option

---

### Post by dawg161 on 2014-11-24
I added my steps to get NetBSD up and running to this wiki as a comment

[http://wiki.netbsd.org/tutorials/how_to_install_netbsd_on_a_power_macintosh_g4___40__grey__41__/](http://wiki.netbsd.org/tutorials/how_to_install_netbsd_on_a_power_macintosh_g4___40__grey__41__/)

---

### Post by este.el.paz on 2014-11-25
> **dawg161 said:**
> I added my steps to get NetBSD up and running to this wiki as a comment

[http://wiki.netbsd.org/tutorials/how_to_install_netbsd_on_a_power_macintosh_g4___40__grey__41__/](http://wiki.netbsd.org/tutorials/how_to_install_netbsd_on_a_power_macintosh_g4___40__grey__41__/)

@dawg:

Thanks for sharing your story, yeah, it does take a little fiddling to get the iMac up and running a linux flavor.  What was now several years ago a gentleman on one of the straight (no chaser) linux forums also suggested "Freebsd is the best option for the G4 iMac" . . . but the installation process then and still now looks too complicated.  When it looked like 14.04/10 was not going to run on my G4's I tried to play around with the FreeBSD install disk, but it seemed to change settings on the computer in spite of not installing, just booting . . . didn't seem to "understand" dual boot . . . .

To each his own, and if you got something to work that's great, my iMac has again "blown its RAM" and is taking a rest.  But, main reason for posting is your comment on the wiki that "The iMac 'needs' nv . . ." . . . that isn't strictly true . . . it may and does run better or look better using the nv driver, but if you read through possibly this thread, where str8bs was helping me through the "black screen" problems . . . we used the "fbdev" driver, with the proper screen refresh rates set up in the xorg.conf file . . . and the GUI was just fine.  There may have been another driver that was or can be used . . . it just has to "connect" the lsmod choices to the xorg.conf file.  So, in terms of systems that are "friendly" on the iMac, still the Xubuntu 12.04 ppc is probably the easiest on install and "relatively" easy to get going . . . except as you found it seems that the nv driver is no longer retro available . . . possibly fbdev is???

e.e.p.

---

### Post by dawg161 on 2014-11-26
Hey Este

Sorry the ram thing is still bothering you. Do you think it's a defective machine, or some process it can't handle?

I do remember the fbdev discussion you had with str8bs. I've been following this discussion for 2 years now here, and at the mintppc boards, and I've tried most of what you all did, I've just never had anything to contribute until now. I didn't try that on the most recent go at getting Debian Jessie to work... if I hadn't gotten what I needed with NetBSD that might be something else to try. I feel like I didn't have any luck getting it to work with Wheezy but it might have just been my xorg.conf

Like you, I had no luck on the iMac G4 with FreeBSD. When I booted it, it just gave a blank screen. It's probably the same issue that NetBSD has after being installed with the console not being configured correctly, but with no sshd running it's hard to do anything with it. The install cd for NetBSD boots to a usable shell and a systinst program that partially works for ppc (hence the instructions on that wiki).

I've no beef with any open-source system. I'm always just amazed and grateful at the work done by competent people on my behalf. I'm more familiar with Debian GNU/Linux and then Ubuntu, but I'll work outwards from what I know and into unfamiliar territory when needed. In the course of this quest I tried Debian 7 Wheezy, Debian 8 Jessie, Vine, Gentoo, FreeBSD, and finally, NetBSD. I'll be honest- when I was having all the trouble with Wheezy, it didn't occur to me to try Ubuntu or MintPPC because I figured it would be the same issues. Since 12.04 is LTS (at least on the i386 and amd64 architectures), I agree that if it can be patched with nv or fbdev it's the way to go at the moment if you want a full desktop environment on the iMac.

That said, I'm thrilled with NetBSD and it got me thinking about my iMac's future and how it can remain useful. I've got nothing installed other than the base system and X, with the simple twm as a window manager. It's got crystal clear graphics, and since X was originally designed for sharing resources on a large computer among multiple video terminals, I think it makes complete sense to use the resource limited iMac for this purpose too. I have a home server with Debian Wheezy hooked up to my TV (actually a similarly ancient but more supported Pentium 4,) but when the TV's off it's usually running headless. Since I need Google Chrome for work (no powerpc support) and I don't have the crazy speakers that came with the iMac, using it for simple work and playing music hasn't been possible since I stopped using OSX. Now I can, and since the server would be on anyway, it doesn't really cost me anything. Plus I'm not worried about the next upgrade or anything- as long as X support exists on some GNU/Linux or BSD system that my server can run (I know Wayland is coming), the iMac is in business. 

I wouldn't characterize the NetBSD install process as particularly hard, once you figure out the quirks of your particular machine. There's less forums out there to help, but there are some. It's no harder than Arch or Gentoo, and far easier than all the work you've had to do with xorg.conf. If you set the machine up the way I have, its honestly a 20 minute process: boot, drop to the shell, partition disks, format disks, make 4 directories, edit fstab, put the base system on, edit fstab again and write 4 lines in rc.conf, and you're good to go. 

Bottom line: Thanks for all the work everyone has done on this system. I think this thread needs to stay active, because it's absolutely the most current information out there on this computer and I know there'll be a small but steady stream of people who find an old iMac in a closet or a tag sale and want to keep it going. 

take care 
tim

---

### Post by abtabt on 2014-11-26
dawg161

hi 

i have use USB boot before install new version off Lubuntu ,Ubuntu 

[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F)

Persistent Live USB  is the best to use to save and make changes to see if the system work before  install 
and all changes you need to do like unhash nvidiafb etc

 and the best is there when you reboot its still thereNVIDIA Corporation NV11 [GeForce2 MX/MX 400]

i have 14.04 in my iglobe, and i use Persistent Live USB about two  week before i install on the hard drive

and  use fbdev in xorg  and  modul nvidiafb

Lubuntu Ubuntu Debian dont use same config for the kernel 

so in Lubuntu 14.04 works fbdev  but not in debian latest stabil and Ubuntu can have a Diffrent config 

so Lubuntu 14.04 and off course 12.04  on a iglobe/ with NVIDIA GeForce2 MX 
with fbdev in xorg.conf and modul nvidiafb activ i have use this conf for some year 12.04 and now 14.04 from stable and the system is 
updated this morning  no problem

and i think imacg4 and som  computer  with NVIDIA GeForce2 MX  card cant use nouveau driver with out uggle desktop

so it will be great if you have time to try this with Persistent Live USB stick to compere with NetBSD (Lubuntu 14.04)

[http://www.everymac.com/systems/apple/imac/specs/imac_800_fp_macosx.html](http://www.everymac.com/systems/apple/imac/specs/imac_800_fp_macosx.html)

i dont now if you have same model

boot time for USB live  is ca 5 min from yaboot to desktop (USB 1.1) its Faster then OSX 10.4.11 on USB Boot

and suspend works

---

### Post by este.el.paz on 2014-11-26
@dawg . . . and hello again to abtabt:

On the iMac implosion . . . probably the motherboard . . . firewire port is gone, third time it's spindled the RAM . . . I **may** try to operate on it at some point.  But, funny on the "two years" . . . yeah, it's been a long strange trip on the iMac . . . covering many of the options that you named . . . all in the search for an OS that would keep the browser somewhat current on a machine that was basically quite fine.  I started with the "apple technology"?? sub-forum on the apple forums, it would have been cool if there was some help from apple to show how to get down to the unix kernel and add some basic features to keep the system viable and not have to do a whole re-install or change the system kernel . . . connecting to "macports" or whatever it is.  But, only advice I got there was for "fink" . . . fink had an 8 hour install and every few hours would break down because a dependency was "broken" . . . just not worth the time . . . other options had similar issues, breaking on upgrade.  Debian was fine, just a little "retro" . . . and now attention for ppc is breaking up a tad, but, at least the buntu flavors for the most part work once they get set up . . . .

But, really, not too important, although as this other fellow said awhile back, seems like the "BSD" options are "more native" for apple hardware . . . if it's working then, work with it . . . .  Have to see if I can revive the iMac once again and see how long it will "live" . . . .

e.e.p.

---

### Post by dawg161 on 2014-12-03
Hi abtabt

That's really interesting you got Lubuntu 14.04 to work. It seems to have Linux version 3.13.xx, correct? Since 14.04 is supported on i386 and amd64 until 2019, if someone wants an iMac G4 to work independently then your advice is clearly the way to go.

As for me, I do believe my family will kill me if I put any more time into playing with the OS on the iMac. It's working now with NetBSD, and since its job is to show recipes on the kitchen counter, taking it off will irk both me and the other users. I'm making chili tomorrow night and need it for that. But if something goes wrong I'll try the process you mentioned.

Este, sorry about the troubles yours is having. Mine has had one line of the LCD fail (it's just bright cyan, permanently) but fortunately nothing on the motherboard. Again, thanks for all your help.

---

### Post by Michael_Cramblet on 2015-09-12
[I]so Lubuntu 14.04 and off course 12.04  on a iglobe/ with NVIDIA GeForce2 MX 
with fbdev in xorg.conf and modul nvidiafb activ i have use this conf for some year 12.04 and now 14.04 from stable and the system is 
updated this morning  no problem

[/I]Would it be possible to get exactly what and how you are using to get Lubuntu 14.04 working? I'm a total newbie, trying to breath some life into this same model (except mine came with OS 9, as well as OS X). I have Lubuntu 14.04 .03 nstalled and the video is working, but I can't boot into the desktop, I'm stuck at the command line screen. I get an error with my xorg.conf and the fatal error of: (EE) no screens found (EE). 

Would it be possible to get a copy of your conf file or guide me as to what exactly needs to be added to my conf file and how to do so? I feel that I'm close to getting this to work. Originally, I didn't get any video with Lubuntu 12.04, I made the changes from the first post of this thread and got the video working to the command line screen. I thought that updating to 14.04 might help, but I'm stuck in the same spot, can't boot into the desktop environment. Any help would be appreciated.

---

### Post by este.el.paz on 2015-09-12
> **Michael_Cramblet said:**
> [I]so Lubuntu 14.04 and off course 12.04  on a iglobe/ with NVIDIA GeForce2 MX 
with fbdev in xorg.conf and modul nvidiafb activ i have use this conf for some year 12.04 and now 14.04 from stable and the system is 
updated this morning  no problem

[/I]Would it be possible to get exactly what and how you are using to get Lubuntu 14.04 working? I'm a total newbie, trying to breath some life into this same model (except mine came with OS 9, as well as OS X). I have Lubuntu 14.04 .03 nstalled and the video is working, but I can't boot into the desktop, I'm stuck at the command line screen. I get an error with my xorg.conf and the fatal error of: (EE) no screens found (EE).

@michael:  I'll reply now in case abtabt doesn't get back to you right away, which BTW you should put "@abtabt" at the beginning of your data, so readers can know.  First thing, if you are a linux newbie, try to get Xu or Lu 12.04 installed, not only should it be a tad easier, but it has "sound" and other stuff.  

> Would it be possible to get a copy of your conf file or guide me as to what exactly needs to be added to my conf file and how to do so? I feel that I'm close to getting this to work. Originally, I didn't get any video with Lubuntu 12.04, I made the changes from the first post of this thread and got the video working to the command line screen. I thought that updating to 14.04 might help, but I'm stuck in the same spot, can't boot into the desktop environment. Any help would be appreciated.

So, it is a tad interesting that you can get a command line video, but not a desktop; often if there is no video there is no CLI either.  But, if abtabt can provide his xorg.conf that would probably fix the problem; if he doesn't get back to you you can read the "PowerPCFAQ" on "How can I set up an xorg.conf file" via the CLI, it is very simple.  However, there are some "issues" that come up with the iMac 800, many of them have been covered here or in the thread "Tester's wanted for 12.04 PPC"  something like that.  Any posts by abtabt, str8bs, or rsavage tend to be higher validity, there are others, it looks like Bryan Moore had no major issues getting his install set up, but these other guys tended to provide more data.  Previously the best driver was the "nv" driver, but that doesn't seem to be accessible, so next best is the fbdev driver.  Check the "lsmod" read out and see that it is there, then it should be listed in the xorg.conf . . . and lastly the ***secret*** to the iMac is that the "horz/vert" specs have to be set in the xorg.conf.  My iMac is basically toast, so I  can't just check what I have, and all my notes for it are in legal pads extending back to 3-4 years ago . . . but, try some variation of "live-nosplash-powerpc video=ofonly: 1024x768-32@60" as boot params for a live dvd, or from command line "Linux video=ofonly xxx " with those same numbers from the install and see if that gets the desktop . . . not sure about the "video=ofonly" part of it because I'm going by the "radeon" params that I needed to get a Lu 14.04 livedvd to boot on my '00 Powermac . . . the "@60" I remember I used for my iMac . . . .  Point being, search around here on google for posts here on the forum and read . . . most of the answers you need are here, or already in the PowerPCFAQ.  If you get 12 set up you can always upgrade through software center, easier, but more time consuming, but shouldn't need to set up new xorg.conf file, etc.

e.e.p.

---

### Post by rsavage on 2015-09-12
That is some mixed up waffle!

I'll provide an nv package for 14.04 later or tomorrow (on a different thread).  But there is a link on how to use fbdev on the very first post of this thread.

---

### Post by este.el.paz on 2015-09-12
> **rsavage said:**
> That is some mixed up waffle!

I'll provide an nv package for 14.04 later or tomorrow (on a different thread).  But there is a link on how to use fbdev on the very first post of this thread.

@r:

A rare sighting . . . with deft exposition of humor, you must be in a good mood.  But, all I can say is, that is some very clear and concise waffle . . . .  But, great news if you are able to produce an nv package for 14.04--too late for my iMac, but it might help the AmigaOne guys???

e.e.p.

---

### Post by Michael_Cramblet on 2015-09-12
[I]you need to unhash nvidiafb in /etc/modprobe.d/blacklist-framebuffer.conf

code

sudo nano /etc/modprobe.d/blacklist-framebuffer.conf

change to
#blacklist nvidiafb


you need a xorg.conf 

code

sudo nano /etc/X11/xorg.conf 

###with this xorg.conf , if not you get 8 bit 
###TBA@
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nv"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "nVidia"
	Monitor    "Monitor"
        DefaultDepth  16
	SubSection "Display"
		Viewport   0 0
		Depth     16
                Modes   "1024x768"
	EndSubSection
EndSection
[/I]
I did use this info above and created a xorg.conf file with it. Now though, when I boot up, I no longer get the command screen, I get a black screen with just a flashing courser.

---

### Post by este.el.paz on 2015-09-12
> [I]###TBA@
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nv"
EndSection
[/I]

@michael:

I'm going to get my ponderous waffle out of the way . . . now that rsavage has arrived on scene . . . .  Wait for him to provide the data on the nv driver, but if you check "lsmod" you either should not find "nv" listed, or it isn't available in 14.04 . . . so, without the access to the nv driver and how to install it, that line would be replaced by "fbdev" . . . .  With his clean and clear waffle connecting you to the nv driver data, then that xorg.conf should be closer to working . . . .

e.e.p.

---

### Post by Michael_Cramblet on 2015-09-12
I did find this conf file which is supposed to be for the iMac G4 800 iLamp Nvidia issue:

[http://mac.linux.be/files/xorg/imac8.txt](http://mac.linux.be/files/xorg/imac8.txt)

---

### Post by abtabt on 2015-09-13
Michael_Cramblet

change to 

Driver "fbdev"

in xorg.conf  and se if that will change anyting

---

### Post by Michael_Cramblet on 2015-09-13
I changed the conf file to "fbdev" and get the following fatal error when attempting to log into the GUI:

AddScreen/ScreenInit failed for driver 0

This iMac is ornery.

---

### Post by rsavage on 2015-09-14
Nice word, I had to look it up!

Get rid of your xorg.conf.  You don't need one.

Follow the first part of this [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F) replacing radeonfb with nvidiafb

On reboot, use 

```
Linux nomodeset video=offb:off
```

---

### Post by abtabt on 2015-09-14
> **rsavage said:**
> Nice word, I had to look it up!

Get rid of your xorg.conf.  You don't need one.

Follow the first part of this [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_load_a_kernel_module.3F) replacing radeonfb with nvidiafb

On reboot, use 

```
Linux nomodeset video=offb:off
```


rsavage 
i think we need some help from nouveau drivern /xorg,conf , if this is NVIDIA Corporation NV11 [GeForce2 MX/MX 400] (rev b2) card


i have use nvidiafb mode_option=1024x768-32@60    
 But its only get uggly 8 bit ,but if   Michael_Cramblet  get a desktop 
its a good start ,maybe he has more luck then 8 bit 

and blacklist-framebuffer.conf and fbdev-blacklist.conf to enable nvidiafb in 14.04, i dont think its in 12.04  both blacklist ???

---

### Post by rsavage on 2015-09-14
abtabt, I don't have an iMac or an NVIDIA card, I'm just posting from experience with radeonfb.  Does it work if you set a 16 bit colour depth, instead of 32?  I thought you had your card working?

It probably won't work at all beyond 14.04, because I couldn't turn off the openfirmware framebuffer.

I've put an nv package on another thread.  You could try that.

---

### Post by abtabt on 2015-09-14
> **rsavage said:**
> abtabt, I don't have an iMac or an NVIDIA card, I'm just posting from experience with radeonfb.  Does it work if you set a 16 bit colour depth, instead of 32?  I thought you had your card working?

It probably won't work at all beyond 14.04, because I couldn't turn off the openfirmware framebuffer.

I've put an nv package on another thread.  You could try that.


no i got only 8 bit when i use 16,24,32 bit  (nvidiafb mode_option=1024x768-32@60 )  on NVIDIA Corporation NV11 [GeForce2 MX/MX 400]

my card is working 16,24 bit with nvidiafb and xorg.conf  ( but maybe this card is strange let say i do X-configure  it will tell me that i have 
two ports but the second is only for mirror ,and two card is in the xorg.conf.new  and you only get 8 bit  desktop (memory is low for the screen but i belive the second port take a lot off memory but no output 

i have 15.04 mate working to on this ilamp 800 (nvidiafb) on a firewire disk ,but with downgrade xorg (mate is fast even on this old thing 

so if Michael_Cramblet get ugly desktop with nvidiafb mode_option=1024x768-32@60

then we can try my way

---

### Post by rsavage on 2015-09-14
It's good that you got 15.04 working.  You should be able to get 15.10 working too then if UM is your thing.  Did you do anything different to turn off offb?

You are right about the blacklist files, udev now puts a blacklist file in too (fdev-blacklist.conf).  I think maybe because you uncommented these files is why the etc/modules file is now seemingly not doing anything.....just guessing really.

It really shouldn't be necessary to define a large xorg.conf.  This should do it

```

Section "Screen"
  Identifier "Screen0"
  DefaultDepth  16
EndSection

```

---

### Post by este.el.paz on 2015-09-14
> **rsavage said:**
> abtabt, I don't have an iMac or an NVIDIA card, I'm just posting from experience with radeonfb.  Does it work if you set a 16 bit colour depth, instead of 32?  I thought you had your card working?

It probably won't work at all beyond 14.04, because I couldn't turn off the openfirmware framebuffer.

I've put an nv package on another thread.  You could try that.

@et al:  I don't know what happened, I guess my waffle disconnected me from the thread, haven't gotten the latest emails on it.

@rsavage:  I think your waffle is catching up with mine, I explained all of this in my waffle . . . the iMac traditionally does need an xorg.conf file, even for 12.04 . . . because you have to get abtabt's  horz/vert refresh rates listed in there to get a good resolution GUI . . . .  So, it can be a basic xorg.conf file, but a little bit more than you showed.

  And, fbdev is OK as one choice, but the nv driver was the best . . . so, don't be shy . . . either link it for Michael or tell him where you have it posted, then let him add the nv module and change the xorg.conf file to say "nv" . . . and that should get him going . . . .  He has the nvidia card, not the radeon . . . I believe . . . .  As abtabt says, there is some two port thing which creates the video problem for the iMac, but the basic "xorg Configure" command that is described in detail in the PowerPCFAQ should do it, I might have had to add the "horz/vert refresh" lines . . . it's been awhile . . . .

e.e.p.

---

### Post by abtabt on 2015-09-15
> **rsavage said:**
> It's good that you got 15.04 working.  You should be able to get 15.10 working too then if UM is your thing.  Did you do anything different to turn off offb?

[SIZE=4]yes i have UM 15.10 working (live cd ) UM have not the Window sluggish when i move window 

i use nomodeset and video=offb:off      (live and installed )    and unhash nividiafb (in both files ) and a xorg.conf
[/SIZE]

You are right about the blacklist files, udev now puts a blacklist file in too (fdev-blacklist.conf).  I think maybe because you uncommented these files is why the etc/modules file is now seemingly not doing anything.....just guessing really.

It really shouldn't be necessary to define a large xorg.conf.  This should do it

```

Section "Screen"
  Identifier "Screen0"
  DefaultDepth  16
EndSection

YES its ok no more but some times i need

 Modes   "1024x768" (ex)

```
now we wait for Michael_Cramblet

---

### Post by este.el.paz on 2015-09-18
[http://ubuntuforums.org/showthread.php?t=2294789](http://ubuntuforums.org/showthread.php?t=2294789)

Link to rsavage's thread providing various debs, including one for nv in 14.04 . . . keeping the waffle over here in this thread . . . .  Right now his thread is right over this one . . . .

e...

---

### Post by Roger-H on 2015-10-07
I am trying to get Ubuntu 12.04 running on an 800mhz iMac G4 and found these instructions. Now that Ubuntu One is down, where are these files being hosted?

---

### Post by rsavage on 2015-10-07
It is easy to compile them, but somebody posted pre-compiled versions of nv here [http://ubuntuforums.org/showthread.php?t=2294789&page=2&p=13360635#post13360635](http://ubuntuforums.org/showthread.php?t=2294789&page=2&p=13360635#post13360635) .

---

### Post by Roger-H on 2015-10-08
Those worked, thank you! Maybe the wiki can be updated with a link to that post.

---

### Post by rsavage on 2015-10-08
The wiki won't be updated by me.  Other people need to start taking ownership it.

---

