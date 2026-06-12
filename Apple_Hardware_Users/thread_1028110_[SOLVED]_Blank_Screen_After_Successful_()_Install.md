---
title: "[SOLVED] Blank Screen After Successful (?) Install"
date: 2009-01-02
forum: Apple Hardware Users
---

### Post by xosia on 2009-01-02
Greetings all,

I successfully installed (I thought) Ubuntu on my old G3 by scrounging info from these forums and following the excellent advice of many of the members here. I had to use the alternate install disk as I have only 384Mb RAM currently and trying to install from the Live-CD was a no-go, The last step I took was choosing the DE and installing it and then rebooting.

On reboot I now get nothing but a blank screen. (And actually my blank screen is even more annoying than a standard blank screen - the screen alternates between blank and white with a flashing "AGING..." message on it - it has always done this when the monitor is on and the computer is off, or if it went into powersave (screen off) mode, so this is nothing new. It's an old, very odd Dell monitor.) The hard drive makes noises, but I don't know what's going on because I can't see anything, no messages or errors. After a few minutes the computer actually beeped at me (one short beep) but then nothing after that.

I tried booting from the CD and using "rescue" (I think that's correct), but I can't seem to even boot from the CD any more. I hold down the 'C' key upon restart and the disk spins a bit in the drive and then... nothing. I've tried control-alt-F1 but also nothing. I don't think it gets far enough along in the boot process to allow that to do anything. 

Have I just killed my computer? Does anyone have any suggestions as to how to get a terminal even back?

My specs:
Power Mac (PPC) G3 (Blue & White)
400Mhz
384 Mb RAM
9GB HD
Mac OS 9.0.4 (before I blasted it, so that's gone too)
Ubuntu 8.0.4 Hardy, PPC version

Now when I installed I saw the notes about changing the HorizSync and VertRefresh but when I looked at xorg.conf I couldn't find these parameters... so I ignored it. That was probably a mistake, but I can't go back in time, so what do I do now? I've searched the forums for a clue but haven't been able to find one. Can anyone help?

---

### Post by tiresia on 2009-01-02
When you restart, do you get the yaboot prompt?
Have you tried to give there video=ofonly?

---

### Post by xosia on 2009-01-02
Nope, I wasn't getting anything at all, nada, zilch, zip. I tried booting again this morning after being off for 8 hours and - tada - it magically works again. I changed the xorg.conf file to add "Module" HorizSync and VertRefresh parameters, and to disable "glx" and "dri", and though I get a slightly scary message from my monitor after the boot process begins (after the second stage of the boot) along the lines of "cannot display this video mode", this doesn't affect the boot process, and I can hit control-alt-F1 and see the boot messages as it progresses. I don't see the splash screen. Ultimately the login screen appears after a short while, accompanied by the beep I heard yesterday. 

I can hit TAB at the second stage of the boot and enter "Linux video=ofonly nosplash and I DO get a splash screen (curiouser and curiouser), followed by a couple of lines of messages ending with  "*Running local book scripts (/etc/rc.local)" followed by a blinking cursor, but it does not proceed from there, the cursor just blinks indefinitely. I can get to a command line by pressing control-alt-F1 but I can't get the desktop to load from there. (I could do stuff like edit .conf files if I knew what to edit.)

It looks like the initial weirdness might be caused by a hardware problem, that's the best I can guess. The computer is 9 years old now with the original HD, and the monitor is 10. I can't explain why I wasn't able to boot from CD, except that the CD-ROM is on its last leg - it sounds like a sick cow when it spins. That is only worrisome in that I can't boot from USB or firewire from this computer - it isn't supported - so if that goes I'll have to replace it. That I was able to get the machine to boot from CD the very first time but not subsequently is a mystery, although by that point the computer had been on (and working) for several hours. The far does work, but maybe not well...?

As for the video issues I'm seeing now, I would have thought running "Linux video=ofonly nosplash" would have help the situation, but it only seems to make it worse. I'm afraid to edit yaboot.conf in the event that it prevents me from logging on at all subsequently. Clearly there is some issue with the video (hence the "cannot display this video mode" message from my monitor) but I'm not sure how to proceed.

Any thoughts?

(At least I have gotten the OS working though - and this makes me so happy.:D)

Thank you!

---

### Post by stream303 on 2009-01-02
You're almost there!  Since you know how to edit your /etc/X11/xorg.conf, have you tried these known parameters for the G3 iMacs:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

Especially important is

[b]HorizSync  58-62
VertRefresh 75-117[/b]

Once you get your display stable, you can add those kernel parameters you used at first to your /etc/yaboot.conf lines that have "append=" in it.

For example, you can add
```
nosplash video=ofonly
```

to the append= line, and then make the system aware of your change with

```
sudo ybin -v
```

Now when you reboot, you won't have to type in those kernel parameters anymore.

---

### Post by xosia on 2009-01-02
Yup! I added the HorizSync and VertRefresh parameters already, but the weird thing is that if I set nosplash video=ofonly I get *worse* results than not. If I *don't* set this parameter my video display gets knocked out until the login screen displays - not a crisis, but weird. If I *do* set it the best I can achieve is a terminal - the desktop doesn't seem to load. It's no big deal since everything ultimately loads, but it is weird and a bit disconcerting to get the flashing monitor and "cannot display this video mode" messages. But it would be great not to have that happen! But since I've no idea what *other* parameters might be affecting it I'll take it as it is. :)

Thanks!

---

### Post by pxwpxw on 2009-01-02
> **xosia said:**
> Yup! I added the HorizSync and VertRefresh parameters already, but the weird thing is that if I set nosplash video=ofonly I get *worse* results than not. If I *don't* set this parameter my video display gets knocked out until the login screen displays - not a crisis, but weird. If I *do* set it the best I can achieve is a terminal - the desktop doesn't seem to load. It's no big deal since everything ultimately loads, but it is weird and a bit disconcerting to get the flashing monitor and "cannot display this video mode" messages. But it would be great not to have that happen! But since I've no idea what *other* parameters might be affecting it I'll take it as it is. :)

Thanks!

Did you try just the 'nosplash'?

---

### Post by xosia on 2009-01-03
Nope.

I just tried it and the monitor went blank again. But I could still hear the HD working, and after a minute or so I got the system beep. And at this very point I remembered that this particular monitor used to have an issue where, if you left it too long and it went into powersave mode, it would not come back up when you tried to wake it up. You had to press and hold the power button in for several seconds, let it shut off, and then turn it on again. So... I did that and what do you know, up pops the login screen.

So it was a hardware problem all along (most of it, anyway). But setting just "nosplash" (**not** "nosplash video=ofonly") was helpful as well, since it still boots and as I much prefer to see what is going on than seeing "cannot display this video mode" and wondering if startup is going ok or not. :)

Thanks everyone!

---

### Post by stream303 on 2009-01-03
First off - my apologies - I thought you were running a G3 imac and not the B&W that you mentioned earlier.

[http://www.everymac.com/systems/apple/powermac_g3/stats/powermac_g3_400_bl.html](http://www.everymac.com/systems/apple/powermac_g3/stats/powermac_g3_400_bl.html)

One thing that will help will be to determine what video monitor are you using?  You'll need to know what the proper horizontal and vertical frequencies are for that monitor.  CHANGE them from what was listed earlier, as that was specific to the G3 iMac.  If it is an lcd monitor, what is the native resolution?

You may have to manually add this data to the existing /etc/X11/xorg.conf to get it to work properly.

Sorry about that - I don't know why I missed you mentioning the B&W with an external monitor....

---

### Post by xosia on 2009-01-03
Yup, it's a B&W. As for the monitor... well, it's an old Dell. A *very* old Dell. (Because the Mac didn't come with a monitor, because it was a rescue.) It (the Dell) is 10 years old, and I can't for the life of me find anything on it resembling a model number. The native res is 1024x768 (at least, that's what the menu tells me - the on-board menu, accessible from a little menu button on the front). Then again, it might just be what it's currently displaying at. Looks ok though. Honestly I don't know how to find out the model short of someone else recognizing a monitor that flashes "AGING..." when it goes into screen powersave mode... :) (Really, it's one of the oddest monitors I've ever seen.)

---

### Post by stream303 on 2009-01-03
Hmmm..  Ok, here's what I'd do.  Even if you don't plan to run Dapper, but something newer, I'd try to install Dapper ppc 6.06x first.  Why?  Without knowing the right video freqs, it is going to be a lot easier to experiment with the command that is supported in older releases like dapper to find something useful:  (THIS DOES NOT WORK IN RECENT RELEASES)

```
sudo dpkg-reconfigure xserver-xorg
or
sudo dpkg-reconfigure -phigh xserver-xorg
```

You'll be stepped through a sequence of questions, and will be able to choose your 1024x768 resolutions and even offer some very generic frequencies that *may not* hurt your monitor.  Note that the monitor may already be shot.

Once you get a working configuration on Dapper, you can use that data from /etc/X11/xorg.conf and possibly /etc/yaboot.conf for a manual configuration with 8.04.

Failing this, you may just want to get hold of an inexpensive lcd monitor with known values.  It will take a bit more punishment than the old crt Dell has. :)

So maybe installing Dapper purely as a diagnostic / test bed might be in order - although any testing on a crt based monitor that old usually hurts it - but if you have nothing to lose....

---

### Post by xosia on 2009-01-03
Update: I got smart! Went on Dell's website, where they conveniently have the manuals available for apparently all of their monitors they ever made.* Gosh Dell, thanks! I was prepared to wade through the specs for approximately 50 15" monitors, but only had to go as far as #5! Here are the specs for it:

Dell 1501FP
Resolution:
Horizontal scan range  	30 kHz to 61 kHz (automatic)
Vertical scan range 	56 Hz to 75 Hz (automatic)
Optimal preset resolution 	1024 x 768 at 60 Hz
Highest preset resolution 	1024 x 768 at 75 Hz
Highest addressable resolution 	1024 x 768 at 75 Hz

Folks, we have a winner. Now, what do I do with this info? :) 

Presumably HorizSync = 30-61 and VertRefresh = 56-75? Maybe? I have the entire user's manual here, so if I need to know more, I can probably get it.

:)

 *or packaged with any of their computers I guess, because they aren't all branded "Dell"

---

### Post by xosia on 2009-01-03
Ok, I mucked around a bit more and found [THIS]("http://ubuntuforums.org/showthread.php?t=83973") oldie but goodie on how to change your settings in xorg.conf. :) I made the following changes:

```
Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync      30-61
    VertRefresh    56-75
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth   16
    SubSection "Display"
        Depth       16
        Modes       "1024x768"
    EndSubSection
EndSection
```

(Depth of 16 because I read somewhere it is more efficient for older comps and you probably won't see a difference when running a more minimalist desktop than setting it to 32.) Then I restarted X. I noticed (even before) that the screen was slightly off center in the horizontal, so I ran xvidtune and adjusted the position slightly and applied the changes. Went back to xorg.conf and added this to "Monitor":

```
Modeline "1280x1024"   78.75   1024 1048 1144 1312   768 769 772 800 +hsync +vsync
```

and restarted X. Everything looks peachy now!

One thing I am wondering about is that xvidtune reports the following:
```
Pixel Clock 78.75
HorizSync 60.02 kHz
VertSync 75.03 Hz
```

The VertSync is just outsize the range of the specs for my monitor. Should I be worried? I'm also unsure if I should explicity define the refresh rate (by which I mean my monitor can display 1024x768 @60 or 75 Hz, but 60 is supposedly optimal (and will extend the life of the unit rather than using 75?)).

@stream303: I thought about getting a new inexpensive monitor, especially since this thing is such a [beast]("http://support.dell.com/support/edocs/monitors/5320u/en/front/front.htm"), particularly the [base]("http://support.dell.com/support/edocs/monitors/5320u/en/side/side.htm"). I use it for my old PC as well (which I keep only because I need it for a few more months yet, at which point I will probably jettison it or convert it to a Linux box as well :)). The table it sits on is rather small. But, I figure why get rid of a perfectly functional monitor? Aside from the weird sleep mode action it works just fine. I am becoming a repository for obsolete equipment. :)

For anyone who happens to be searching for the specs on Dell monitor they are all [here]("http://support.dell.com/support/systemsinfo/documentation.aspx?c=us&cs=19&l=en&s=dhs&~subcat=50&~cat=3"). Nearly all except the very oldest have graphics (pictures) of the monitors, in the event you don't know the model number (like me), and they list them by size, so it cuts down the searching a fair bit. Most have complete user manuals as well. **Great** resource. ***But not as good as this forum. :)***

---

