---
title: "[SOLVED] I want to do this right this time......"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-04-04
I currently have an old tnt2 video card and want to upgrade to a PNY Verto GeForce 6600GT that a friend gave me.  Other posts I have made detail the trials I have gone through trying to get a driver and configuration that will work in Ubuntu.  The end result is this:

I have a "new" motherboard (new to me) - KT7-RAID and a new power supply to support it ready to install.  When doing so, I also want to start completely from scratch on an install of 7.10.  Here's where I need a little help, please:

- I've tried the LiveCD with the new card in and it doesn't work.  Do I need to try some form of alternate installation method?

- I've tried Envy and directly downloading the driver from nVidia - can't get anywhere.  Some have suggested all I need do is enable restricted drivers.  Doing so with the old card in installs the legacy stuff, and the "new" card won't run off it.  If I try to install the "new" stuff via Synaptic, I get errors saying it can't copy over the top of a file (I can do it manually but the process can't).  So - starting from scratch with just the new video card in, how can I get/enable the new restricted driver stuff when I can't get to a GUI??

- To use the restricted drivers, what do I put in the driver in xorg.conf?  "nv" doesn't work, and apparently I never get the new installed as "nvidia" says it isn't installed.

Based on the above, can somebody give me a pretty fail-safe method of doing the following:

With the "new" motherboard and processor, the new power supply and the "new" video card (the PNY Verto GeForce 6600GT), install Ubuntu and get the video driver installed and working.

That doesn't seem like much to ask, but previous attempts with the video card have left a very sour taste in my mouth.  I want to install everything from scratch.  I know the card will do graphics, because it at least runs Windows 98SE even without the nvidia driver.  Ubuntu won't even work with the VESA driver.  Sometimes it seems close - I get a checkboard of black and white boxes and can move what appears to be a big box it thinks is the mouse cursor.  I have tried various refresh rates, etc., and just don't seem to get anywhere.

The monitor is a CRT - KDS Xtreme Flat 17", if that can help anyone to help me.

I know I make a lot of posts, and I suppose most are being ignored anymore, but I really do need help here.  Prior to this I have run Ubuntu as my primary OS, with just a small driver with Win98SE on it for Family Tree Maker.  I'd really like to be able to continue to do so.

Thanks in advance!  :)

---

### Post by The Titan on 2008-04-04
Unless i don't understand you correctly, that sound slike the right method to install it.  After you do a fresh install of 7.10 it will give you the option to install the restricted drivers, and there will be nothing to install them over so it will work,  As for the alternate install method you could try the "Alternate" CD that doesn't have the live option.  and after you install the restricted drivers type "sudo nvidia-settings" in the terminal and it gives a GUI to set up your xorg.conf file.

---

### Post by anewguy on 2008-04-04
> **The Titan said:**
> Unless i don't understand you correctly, that sound slike the right method to install it.  After you do a fresh install of 7.10 it will give you the option to install the restricted drivers, and there will be nothing to install them over so it will work,  As for the alternate install method you could try the "Alternate" CD that doesn't have the live option.  and after you install the restricted drivers type "sudo nvidia-settings" in the terminal and it gives a GUI to set up your xorg.conf file.


Here's what's got me stumped (maybe I'm just stupid :) ) - I can't get to  GUI with the new card, so I can't install from the LiveCd (I tried - won't work).  So if I go to the alternate Cd route, how do I go about installing the restricted drivers from text mode (a big apt-get??) ?  Once the restricted drivers are installed, how do I enable them from the command line?

Thanks - I'll get started on the alternate CD download right now. :)

---

### Post by .nedberg on 2008-04-04
The installed system from alternate cd and Live cd is not different. After installing Ubuntu you can start the restricted-manager and install the drivers as needed. Alterante cd just does not use the live system to install.

---

### Post by paydaydaddy on 2008-04-04
Are you getting any display at all with the new viddy card? Are you able to boot into and configure your bios?

---

### Post by anewguy on 2008-04-04
> **.nedberg said:**
> The installed system from alternate cd and Live cd is not different. After installing Ubuntu you can start the restricted-manager and install the drivers as needed. Alterante cd just does not use the live system to install.

I know the end result Ubuntu is the same, only the installation procedure is different.  What I'm concerned about is since I've never been able to produce a readable GUI screen (this includes via the installation on the LiveCD) I'd like to know that the alternate CD method isn't going to get to some point and want to use a GUI (not just the terminal-mode GUI of the config scripts) and I won't be able to go any further.  Keep in mind this card has not produced a readable GUI even with the vesa driver at 640x480.  I want to be SURE I'm not missing something such that I'm going to end up with either a can't proceed any further installation method or an unusable GUI.  That's why I asked if there are text-mode methods of retrieving the restricted drivers, installing them and enabling them, since all I have seen with Gnome and KDE are true GUI based ways - ways I can't get to with the card.

Thanks!  :)

---

### Post by anewguy on 2008-04-04
> **paydaydaddy said:**
> Are you getting any display at all with the new viddy card? Are you able to boot into and configure your bios?

Yep - I can boot fine, configure the BIOS, etc., it's just if it try's to start an X GUI the screen becomes unusable.  It even works in graphics mode in Windows 98SE without anything but the default driver from Windows (obviously needs a driver if I want "true" colors, higher resolution, etc., but Windows runs, open/closes windows etc.) and that is what has frustrated me with my attempts in Ubuntu - it HAS to be a driver problem, but I just don't seem to be able to get around it!  

Thanks!  :)

---

### Post by anewguy on 2008-04-04
Want to start this tonight, so I thought I'd put out one more plea for opinions/instructions.

Thanks!  :)

---

### Post by crjackson on 2008-04-04
> **anewguy said:**
> Want to start this tonight, so I thought I'd put out one more plea for opinions/instructions.

Thanks!  :)

Put in the LiveCD and boot.
Hit F6 and delete the word "SPLASH" and continue booting (don't delete anything els from the comman line)
If it boots continue to install.

If installed don't reboot.

Open a terminal and type
```
gksudo gedit /boot/grub/menu.lst
```

When the file opens, search through and find the kernel line and change the word "SPLASH" to "NOSPLASH"

If you're not sure what the kernel line is, just use the find function and change all instances of splash to nosplash.

save the file and reboot.

Hope this gets you going.

---

### Post by anewguy on 2008-04-05
Okay, here are some results.  Be forewarned I'm getting pretty ticked right now but I'll try to hold things together here.

splash/nosplash makes no difference - the problem is when it goes to actually start the desktop on the LiveCD I end up with scrambled video and wouldn't respond to anything except pushing reset.

The alternate Cd installation went to 97% complete, said it was cleaning up, then just hung there.  Reboot revealed that indeed I couldn't boot the install yet.

This is getting maddening!!!!  I remember once quite a while ago reading about putting in a video driver at boot time - I just don't know 2 things for that (at least):  (1) what the heck driver disk do I need for nvidia  (2) how do I do it?

Up until now I have loved Ubuntu.  While I know a driver problem isn't Ubuntu's direct problem, this entire experience is really souring.

---

### Post by crjackson on 2008-04-05
> **anewguy said:**
> Okay, here are some results.  Be forewarned I'm getting pretty ticked right now but I'll try to hold things together here.

splash/nosplash makes no difference - the problem is when it goes to actually start the desktop on the LiveCD I end up with scrambled video and wouldn't respond to anything except pushing reset.

The alternate Cd installation went to 97% complete, said it was cleaning up, then just hung there.  Reboot revealed that indeed I couldn't boot the install yet.

This is getting maddening!!!!  I remember once quite a while ago reading about putting in a video driver at boot time - I just don't know 2 things for that (at least):  (1) what the heck driver disk do I need for nvidia  (2) how do I do it?

Up until now I have loved Ubuntu.  While I know a driver problem isn't Ubuntu's direct problem, this entire experience is really souring.

Okay - I understand your frustration.  I've never run across your particular problem before.  it's 6AM on SAT morning here, and I don't have my glasses on.  I gust got up to get a glass of water and I always check back here.

When I get up later today, I'll check around and see if I can find anything else to try.  While waiting, you could download the Hardy Beta and see if it gives the same results.  You may have done that already, but I don't remember and can't see good enought without my glasses to go off reading right now...

I'll check in later...

---

### Post by anewguy on 2008-04-05
> **crjackson said:**
> Okay - I understand your frustration.  I've never run across your particular problem before.  it's 6AM on SAT morning here, and I don't have my glasses on.  I gust got up to get a glass of water and I always check back here.

When I get up later today, I'll check around and see if I can find anything else to try.  While waiting, you could download the Hardy Beta and see if it gives the same results.  You may have done that already, but I don't remember and can't see good enought without my glasses to go off reading right now...

I'll check in later...


Thanks - I'll try the Hardy download if it will work while on the LIveCd (I have to run on it again with the old card so I can do anything).  I'm a time zone behind you - central time, and I've been up all night working on this x!<?+{" thing again.  I'll probably try to start the download and just go to bed.  My god, if it's this difficult with nvidia, and everyone seems to say get nvidia not ati for Ubuntu, I can't imagine what it must be like for someone with an ATI card.

---

### Post by maniac_X on 2008-04-05
anewguy... you might want to check this thread out. Maybe there is a clue in there for your problem. I didn't read the whole thread but some people had issues with stock drivers not working. Maybe it will give you a direction to look in.
[http://ubuntuforums.org/showthread.php?t=221313&highlight=geforce+6600gt](http://ubuntuforums.org/showthread.php?t=221313&highlight=geforce+6600gt)

.

---

### Post by anewguy on 2008-04-06
Well, it's official, I have officially failed for the last time with this !@#$ video card.  I have spent many, many, many hours on this, tried everything everyone has suggested, gone through countless threads, etc., and I just can't make this !@#$ thing work.

I'll mark this as solved so there is no more activity on it.  I really wanted that card to work - it would be so much better than this old Diamond Viper 770 with 32 meg (ancient).  Now I don't know what to do - maybe I'll just give completely up and go back to Windows.:(

---

