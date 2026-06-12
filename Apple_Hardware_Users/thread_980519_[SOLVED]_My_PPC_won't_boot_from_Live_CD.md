---
title: "[SOLVED] My PPC won't boot from Live CD"
date: 2008-11-12
forum: Apple Hardware Users
---

### Post by bug67 on 2008-11-12
I have a Dual 2.7 GHz PPC G5 that I eventually would like to make a dual-boot machine with OS X on one HD and Ubuntu on the other.  Problem is, I cannot get the machine to boot from Hardy LiveCD I downloaded from here: 

[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/) 

I've tried holding down the "C" key during re-boot.  I tried holding Command Option Shift Delete during re-boot.  And, I tried booting to open firmware and entering "boot cd:,\\:tbxi"

None of these things worked.  OS X always booted up as normal.  What am I missing?  I'm a complete Linux noob.  Only been running Intrepid on my Compaq laptop (Intel machine) for about 3 days.  Had no problems booting from that liveCD on that machine but, seems like I've hit a brick wall with the Mac.  Thanks in advance.

---

### Post by poebae on 2008-11-12
Are you using a PPC version of Ubuntu? You have to make sure the image you download is something along the lines of [ubuntu-8.04.1-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/hardy/release/ubuntu-8.04.1-alternate-powerpc.iso), not an i386 or amd64 suffix.

Unfortunately, PPC is no longer officially supported, so (from my experience at least) your hardware support will be very hit-and-miss, and you'll be lucky to get Flash working correctly, if at all.

I don't mean for this post to be FUD, but I tried to convert my Mac G5-using roommate to Ubuntu. He liked everything else, but eventually got frustrated and switched back to OSX after I couldn't get his wireless or Flash to work. 

It was a very frustrating process for both of us, and I'm annoyed that a potential convert was lost because of the bad experience. Of course it's not a fault with Ubuntu itself, but it reflected very poorly on Linux as a whole.

---

### Post by bug67 on 2008-11-12
> **poebae said:**
> Are you using a PPC version of Ubuntu?

Well, the version I downloaded *said* it was for PPC.  I looked at the packages inside and there were several things labeled PPC.  I'm assuming I got the right one.

Thanks for the quick reply.

---

### Post by stream303 on 2008-11-13
Are you burning the image as an iso - that is in OSX disk utility, drag the downloaded image to the left hand pane of disk utility.  Highlight the image file, then click burn,  CD-R recommended and at a slow speed if you can get that option.

You can also hold down the alt/option key upon startup if the cd is already in the drive, and get icons to choose the startup disk as well.  Worth a shot there..

Disconnect anything but the keyboard and mouse.

---

### Post by stream303 on 2008-11-13
> **poebae said:**
> It was a very frustrating process for both of us, and I'm annoyed that a potential convert was lost because of the bad experience. Of course it's not a fault with Ubuntu itself, but it reflected very poorly on Linux as a whole.

You can do your best to stop the FUD by looking at it from a different angle as a whole. :)  Don't let it reflect poorly on Linux - in fact it is just the opposite considering the amount of hassle most of us go through to get it working.

What you should see reflected is a group of dedicated programmers and users trying to do their best to support ppc when no vendor is interested in passing along hardware docs or specs to make the job any easier.
 
Apple PPC hardware was not designed to be linux-friendly, nor respond in many cases to probing during install, so the installer just tries it's best, and we have to fine tune it.  Not to mention that it has no way of knowing about old firmware quirks.

What you are seeing in front of you is the community support that Canonical has handed off to us.  Yes, there may be bugs and other things which are out of our control, like perfect flash, 3d video, etc, but that doesn't stop them from making releases, providing update repos, and even a shared Apple forum from which you can get help.

They could drop this like a hot-potato at any time.  At least this is better than nothing.

I know your frustration as I felt the same way when I started out with it, until I learned what a huge hassle it is to support.

And that's what should be spread - that ppc Linux exists at all despite these immense problems and lack of hardware vendor support.

Anyway, enough of my rant - I know you meant well.

---

### Post by mkvnmtr on 2008-11-13
As the other poster said you have to have the right iso and you have to burn it correctly. Then you need to check that it was burned correctly. I believe on disk utility the call it verify. Then when you restart you need to press the c key or option key after you hear the start up sound. Don't let up on the key until you see the linux icon come up on the screen. The first thing you will probably see is the Mac icon. Continue to hold the key until the linux icon appears. Then wait until the little ball quits spinning and click on the linux icon. If I remember then you need to click on the start icon. If you don't hold the key long enough or you press it too late it will just boot into Mac.

---

### Post by bug67 on 2008-11-13
Thanks, everyone, for your replies.  Unfortunately, none of the solutions posted are working.  I am certain I am burning the correct .iso and that I am burning it correctly.  However, no matter what I do, none of the disks I have burned will boot.  Oh well.  At least I can still play on my Presario laptop.  :)

---

### Post by IQRules on 2008-11-13
> **bug67 said:**
> Thanks, everyone, for your replies.  Unfortunately, none of the solutions posted are working.  I am certain I am burning the correct .iso and that I am burning it correctly.  However, no matter what I do, none of the disks I have burned will boot.  Oh well.  At least I can still play on my Presario laptop.  :)

I did not use Live CD. I can confirm 8.10 does not work on iMac G3, and ubuntu-8.04.1-alternate-powerpc.iso works out on it.
I can install it and in rescue mode I can mount the / root.

---

### Post by bug67 on 2008-11-13
> **IQRules said:**
> 
I can install it and in rescue mode I can mount the / root.

That *sounds* promising but, I'm afraid may be beyond the scope of my abilities.  I would need a step-by-step for dummy noobs type instruction.  

I don't want to install Ubuntu on my G5 just yet.  I just want to run it off the Live CD and feel it out.  I'm afraid I may mess stuff up if I start having to run command line stuff just to get it to boot.

---

### Post by IQRules on 2008-11-13
> **bug67 said:**
> That *sounds* 
I don't want to install Ubuntu on my G5 just yet.  I just want to run it off the Live CD and feel it out.  I'm afraid I may mess stuff up if I start having to run command line stuff just to get it to boot.

Is it just 1 sata drive here? Swap a drive or install 2nd one for testing. To be save I will unplug OSX drive.

I did re-install the OSX on my iMac G3, took a long time for over 1.5 hour. Yours G5 (dual/desktop) ?

---

### Post by stream303 on 2008-11-14
I'm clutching at straws now, but you never know.. :)

Are you holding down the "C" key long enough to hear the cd start to boot - I have to hold it down for quite awhile.

I've also heard of powering on with the cd in the drive, and THEN after a VERY short while, hold down the C key long enough to hear the cd do it's thing.

And, again with the cd in the drive, boot up but this time hold down the ALT key (also seen as option key) until disk icons appear.

Crossing fingers. :)

---

### Post by bug67 on 2008-11-14
I am holding down the "C" key during the entire boot process from the moment I hear the Mac "chime" until, inevitably, OS X boots.  I can hear the CD spinning in the drive during the entire process but, nothing happens.

When I, alternately, hold down the option (alt) key during start up, I am taken to a screen with a lock icon and a place to enter my password.  Nothing happens when I enter my password.  I am forced to reboot by holding down the power button.


Another thing I tried as far as trouble shooting:  I'm noticing that in disk utility, when I highlight the Ubuntu disk and select "Verify,"  that's not working either.  I'm getting the message: 

[I]"Disk Utility stopped verifying "(null)" because the
following error was encountered:

Filesystem verify or repair failed."[/I]

Also, when I go to "Startup Disk" in System Preferences, The Ubuntu disk is not there.  Should be right?  If it's a viable start up option?

This is leading me to believe that I am, somehow, not burning the disk correctly in the first place.  I am downloading the .iso, dragging it into Disk Utility and clicking "burn."

*Seems* to burn correctly.  When I then open the burnt CD in Finder, I see the following:

Folder named "Casper"
Folder named "dists"
Folder named "etc"
Folder named "install"
Document named "md5sum.txt"
Folder named "pics"
Folder named "pool"
Folder named "ppc"
Folder named "preseed"
Unix Executable named "README.diskdefines"

Should go, right?

I even downloaded and burnt a live CD copy of Gentoo Linux thinking maybe a different version of Linux might work.  No go, however.  All the same stuff as I just described happened.  I'm just not getting something.  :confused:

---

### Post by crapple on 2008-11-14
You can try holding option and click on the cd drive. 
Hope this helps.

---

### Post by bug67 on 2008-11-14
> **crapple said:**
> You can try holding option and click on the cd drive. 
Hope this helps.

Nothing...

:popcorn:

---

### Post by stream303 on 2008-11-14
By now I know we must be driving you crazy. :)

AH!  Have you searched for any Apple firmware updates to the drives from the apple download site?  I've seen a few in the past regarding this, although you'll have to go back a few years.  Then again, I thought a normal osx software update would include this.

[http://www.apple.com/downloads/macosx/apple/firmware_hardware/](http://www.apple.com/downloads/macosx/apple/firmware_hardware/)

Are you using CD-R's?  Have you tried a different brand?  

If you can, perhaps try burning it on another machine, and preferably one you can burn at a very low speed with.

It looks like you are doing everthing right, although maybe an md5sum error might indicate something else...

Maybe there's just one little thing in here overlooked:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

although you've probably been here.

Frustrating for sure when you can see that the files were properly burned, but reading the boot track seems to go nowhere...

---

### Post by alwayshere on 2008-11-14
i had alot of trouble trying to boot as well i ended up burning about  6 disks and just kept on trying them the one that worked had also not worked earlier i think its some sort of bug or something .
the install that work for me on my macbook 1.1 was a 
txt base install.

I did this with no osx installed as i dont use it .

hope this helps

---

### Post by pxwpxw on 2008-11-14
> **bug67 said:**
> Nothing...

:popcorn:

Just wondering if you checked if it will boot from Macosx install dvd.

---

### Post by letriste on 2008-11-15
> **bug67 said:**
> When I, alternately, hold down the option (alt) key during start up, I am taken to a screen with a lock icon and a place to enter my password.  Nothing happens when I enter my password.  I am forced to reboot by holding down the power button.

I had the same problem on my powerbook 1.25. what you are encountering is the open firmware password. To work around this, Open your 'Applications' folder, go on to 'Utilities' and run 'Open Firmware Password.app'.

If you can't find it, it's on your OSX installation CD/DVD, somewhere in the 'Applications' folder. Just copy it onto your HD and run. If you disable the OF password, you can boot from CD holding 'C'.

This is my first post here. Hope it helps. I'm a Linux n00b too, and was finally able to crack this issue yesterday after 3 or 4 days...

Tríste

---

### Post by bug67 on 2008-11-15
> **letriste said:**
> "...If you disable the OF password, you can boot from CD holding 'C'..."

This got me further than I've been so far!  :)

I was actually able to begin the boot process but, as soon as the kernel started loading, my system(s) crashed.  Tried it on both my G5 Tower and my G4 PowerBook.  

I got the Gentoo Linux disk to boot as well however, that one doesn't have an actual GUI.  It's all command line and I don't know any commands.  I neeeeeeeeeeed a GUI!

I'm gonna try some other stuff later on.  One of the suggestions from another poster was to try burning the CD on another machine.  I'm going to give that a go as well.  The Great Experiment continues!  :)

---

### Post by tiresia on 2008-11-15
> **bug67 said:**
> I was actually able to begin the boot process but, as soon as the kernel started loading, my system(s) crashed.  Tried it on both my G5 Tower and my G4 PowerBook.  

Do you have the same problem on both your macs? The G5 is a powerpc64, so at boot prompt hit TAB and choose a powerpc64 option (like 'live-nosplash-powerpc64')

---

### Post by stream303 on 2008-11-15
That's great news about being able to boot the cd's!

Tiresia's suggestion at the boot: prompt is great.  I might even go further and add these options:

```
Linux live-nosplash-powerpc64 video=ofonly
```

If the gui doesn't come up, you can still go to a virtual terminal (CTRL-ALT-F2) and see if the commandline works for now with some simple commands such as:

```
uname -r
or
cat /proc/cpuinfo
```

Thing is, you have reached a point where user-customization is mandatory to revive the gui.  Because of the fact that Apple hardware isn't Linux-friendly, you'll have to gather up some known values to plug into the config files that the installer or live-cd has no way of knowing about.

Since the live-cd operates in ram, you *could* manually edit /etc/X11/xorg.conf, shut down the xserver, log out and log back in, and see if  your changes worked.  At this point, it just might be easier to install the system onto the drive, which is not just a quick look-see kind of thing.

Unfortunately, this is something most of us face.  You'll need to gather your horizontal and vertical frequency data for your monitor, and most likely make sure the driver is right for your radeon card, and then make a custom xorg.conf file.  I got some specs for your machine at everymac.com, and also see that it supports two drives.

In some models, two drives presents a problem that early version of yaboot couldn't handle without manual changes if that model actually has two hard drive controllers.  Fortunately, yaboot in Intrepid 8.10 is smarter and should be able to deal with this, but you'll still have to manually configure your video.

So you see where this is going - to test out Ubuntu PPC, you'll probably find that you'll have to just install it and see how far you get with manual configuration.  Along the way you'll probably have to get involved with the commandline, text editors, etc and may reboot the machine more than you'd like. :)  In any case, make sure you have a full working backup of OSX, or are willing to reinstall everything.

Everyone here is happy to help, but just take into account your personal frustration level. :)

---

### Post by bug67 on 2008-11-15
> **tiresia said:**
> The G5 is a powerpc64, so at boot prompt hit TAB and choose a powerpc64 option (like 'live-nosplash-powerpc64')

BINGO!!!  :)

Got it to boot on my G5.  I am backing up my HD now to prepare for an install.  I'm sure I'll have many more questions after.

Thanks!

---

### Post by stream303 on 2008-11-15
Gulp. :)  Ok, here we go.....

The easiest way in my mind to do this if you want to dual-boot, is to reinstall OSX first to only half the drive.  So, at the start of the fresh OSX install, go up to disk utility, and repartition your drive into two partitions - one for OSX extended journaling, (no os9 compatability unless your are doing os9 stuff), and leave the second partition just open as "free space".  Then continue on with the OSX installation as normal.

Make sure OSX boots and works properly when done.

Then, when it comes time for Ubuntu installation, let guided partition install to "free space".  DON'T use "whole disk", or else it will wipe out your osx install.  At the end of installation, yaboot should notice osx, and include it in the yaboot boot prompt, usually with the "X" option.  Make sure that works before doing anything else.

Then comes the fun part of tying to get the gui going in ubuntu later.

Definitely take your time, and try to make it fun. :)

---

### Post by bug67 on 2008-11-15
Ok.  I don't want OS X and Ubuntu on the same disk.  Is it possible to leave my OS X HD intact and just install Ubuntu on the second HD?

---

### Post by tiresia on 2008-11-15
> **bug67 said:**
> Ok.  I don't want OS X and Ubuntu on the same disk.  Is it possible to leave my OS X HD intact and just install Ubuntu on the second HD?
Yes, of course. I do the same. If you are not expereinced, but even if you are, backup important data! Are you trying to install Hardy?

---

### Post by bug67 on 2008-11-15
> **tiresia said:**
> Yes, of course. I do the same. If you are not expereinced, but even if you are, backup important data! Are you trying to install Hardy?

Yes.  Trying to install Hardy.  I'd like to upgrade to Intrepid after but, one thing at a time.  I am backing up now.  I'm just thrilled that I was able to boot from the Live CD at this point.  That was the major first step.

---

### Post by stream303 on 2008-11-15
Is this drive bootable, like firewire?

Intrepid's new yaboot is supposed to take care of external hd issues, and what I did in the past was to hold down the "alt" or "option" key when booting after installation to it to get the icon-drive boot drive choice to select the firewire.

You may have to do the same here.

I was able to get Ubuntu Intrepid installed onto an external firewire drive, and the new yaboot seemed to perform ok, but for some reason, I couldn't get it to boot unlike I did in the past - could be user error, but I didn't look into it too much and decided to dual-boot on the internal drive.

Soooo.... If you've got nothing to lose on that external firewire, I'd try Intrepid first, but if it doesn't work immediately, guess what - more manual editing, possibly a downgrade to Hardy 8.04 with more manual editing...

So give Intrepid a shot if you feel like it.  Your results would help out other users here for sure...

---

### Post by bug67 on 2008-11-15
> **stream303 said:**
> Is this drive bootable, like firewire?

I am wanting to install Hardy on a second *internal* drive.  

I would be going directly for an Intrepid install but, I couldn't find a *PPC* download for 8.10.  Hardy was the most recent version for PPC I could find.  I am just assuming I can upgrade after I install Hardy?

But, as far as *where* I install, I would like Ubuntu bootable from my G5's *2nd Internal* hard drive if at all possible.

---

### Post by mkvnmtr on 2008-11-15
There is a 8.10 alternate install disk but you can't play with it like you can a live disk. There is a live disk also but some of us have not been able to get it to boot. since this is your first time 8.04 will probably be better for you. Then when you have a little experience another install only takes about one hour. Good luck

---

### Post by bug67 on 2008-11-15
Ok.  I am typing this from within Firefox onboard my freshly installed Hardy Heron equipped Macintosh G5 computer.  The installer asked me which drive I wanted to install on.  I naturally chose the one that OS X *wasn't* on.  All seems well.

Right off the bat, 2 things:  

1.  I have 2 monitors and Hardy is wanting to mirror them.  I un-checked the "clone screens" in the screen resolution settings in system settings but, my screens are still mirrored.  Also clicked on "Detect  Displays" to no avail.

2.  It seems that I am unable to use the numeric key pad portion of my key board.  **(_EDIT_: )**  Got this one figured out.  :)

I'm doing a software update right now so, maybe after that and a re-start, we'll see how things go.  

I think this particular thread has served it's purpose so, any further questions and I'll start a new thread.  

Thank you all for you help.  I look forward to getting to know you as well as Ubuntu/Linux.  :)

> **mkvnmtr said:**
> "...There is a live disk also but some of us have not been able to get it to boot..."

Where can I find it?  I'd like to give it a go.  I've been using 8.10 on my old Compaq laptop for about a week and a half now.  **(_EDIT_: )** Never mind.  I found it.  :)

---

### Post by stream303 on 2008-11-15
Congratulations!  Don't ya' love it when a plan goes easier than expected? :)

How large is your monitor, and is it crt or lcd?

Even though the kernel is smp by default, I'd doublecheck to make sure you are running on both cylinders.  A quick way to do this is to run "top" in a terminal, and hit the "1" key.  Now cpu0 and cpu1 should show up in the upper left of top's display.

Also, you may want to make sure that the cpu frequency scaler, powernowd is actually working, otherwise you may be running at full cpu speed all the time.

One way to do this is to right-click on the top panel, and "add to panel" the cpu-frequency-scaling applet.  In fact, add *another one*.  When the applets appear, right-click on the second scaling applet, and change the 2nd scaler app preferences to monitor cpu1.

Now you should see if both of your cpus are scaling back properly.  If not, a quick workaround is to replace the default powernowd, with cpudyn via synaptic.

Anyway, enough of that - go have fun and welcome to the world of Ubuntu on your ppc mac!

---

