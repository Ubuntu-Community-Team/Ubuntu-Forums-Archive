---
title: "revive iMac g3"
date: 2014-12-31
forum: Apple Hardware Users
---

### Post by zafod4422 on 2014-12-31
Hi guys, 
I think I'll need quite some help on this, so I'll be  grateful for any replies.
Recently I've installed Lubuntu on my iMac g3 slot loading 350mhz with 256 MB of RAM. All went well except that the crt display colours and geometry were acting weird. Every startup the colors changed and sometimes the monitor was completely black. This was because the computer had an old firmware and it needed to be updated for Lubuntu to run. But I didn't know that back then, so the first thing I did was that I zapped the pram. That made things go from bad to worse. At first the iMac didn't want to boot at all, shutting itself off after a few seconds but after I let it rest for a while, it now manages to boot to Lubuntu, but with a completely black screen.

I did some research on this and found that there are fixes, a detailed guide to revive your iMac is here:[http://www.gileskennedy.com/panthereatsimac/problemsolver/](http://www.gileskennedy.com/panthereatsimac/problemsolver/)
In part 2 you can read about the different states an iMac can be in after installing a new OS with an outdated firmware. My iMac is in s2, with an occasional s4. 
The two fixes are putting the iMac to sleep and then waking it or connecting an external monitor. However I cannot perform either of those as the sleep/wake method requires Mac OS (X) and my only installed OS is Lubuntu. The second method requires a Mac that is capable of connecting to an external monitor, which mine isn't.  
So my question is: Are there any other possible fixes?
Can I get my Mac to sleep after booting into the OSX install CD? 
If not, then I guess I'll need to somehow get OSX into the Mac. But how? I cannot go through the whole installation process with a dead monitor. Is there a way to install OSX onto the HDD perhaps from a different computer so that the iMac can then boot?
I'm really running out of ideas now, if any of you could help i would be super grateful.

---

### Post by este.el.paz on 2015-01-02
Possibly you just need the right xorg.conf file for your computer . . . can you get into a clean TTY?  There is a thread here "Old iMac-ubuntu capable" posted here recently also for a G3, some links provided and reference to "Testers wanted for 12.04 PPC" that should have plenty of data on getting the G3 set up going.  Probably have to use Google to search and then go to the Ubuntu forum results . . . .

e.e.p.

---

### Post by zafod4422 on 2015-01-03
I don't think that's the problem, as far as i know I should have the right xorg.conf file. Even though finding it was quite tricky as the mac.linux.be site seems to be hacked. 
This problem is that the firmware of the (bootloader?) does not support OS's newer than mac OS 9. I had the same problem when I had OS X Panther installed. I could just always bring the screen back by putting the computer to sleep and waking it up again. This does not work with Lubuntu, so im stuck with a mac with a black screen.

---

### Post by este.el.paz on 2015-01-03
> **zafod4422 said:**
> I don't think that's the problem, as far as i know I should have the right xorg.conf file. does not work with Lubuntu, so im stuck with a mac with a black screen.

Well, that doesn't mean the computer is not use-able . . . just not as use-able as it was . . . .  What version of Lubuntu are you using?  Sometimes the xorg.conf has to be tweaked a bit more to get the screen function going.  And, what does the output of "lsmod" show?  Does it list the correct video module for your computer?

What about my question about getting to a clean TTY?  If you can see that you might try "sudo start lightdm" and see if that does anything . . . or trying "sudo stop lightdm" (which may make the screen go black) and then wait a bit, and try to start it again, etc.

There are other, lighter versions of linux out there, possibly you are right on the edge of the specs, esp. if you are trying Lu 14 . . . try 12.04, or try "ToriOS" ??? (don't know if it's spec-ed for PPC). . . or some have mentioned "puppy linux" . . . keep trying OSs until something works . . . .

---

### Post by zafod4422 on 2015-01-03
> **este.el.paz said:**
> And, what does the output of "lsmod" show?

Haha, how am I supposed to know? As I said, the monitor is not working at all. Totally black, always. 
I might have posted this in the wrong forum, as it is only partially a Lubuntu problem. The problem is not in the xorg.conf file and is not stricly related to Lubuntu, before I reset the PRAM, i was getting a rather usable display, therefore the xorg file at least partially worked. The problem is that I had an outdated bootloader firmware, which barely works with any OS newer than Mac OS 9. I did not know that and so while troubleshooting the computer I decided to reset the PRAM, which made things even worse and rendered my screen rather useless. Now to get the monitor working again I need to update the Macs firmware, however I cannot do that with a black screen. There was a fix for this in OS X, where putting the computer to sleep and waking it up would somehow make the monitor work (a bit), allowing you to update the firmware. However it doesn't seem possible to put the computer to sleep in Lubuntu (at least i haven't managed to do it, its rather hard with a black screen). So that's how i'm stuck. What I will probably try to do now is to blind install OS X -that will be hard, get the monitor working, update the firmware, reinstall Lubuntu.

---

### Post by rsavage on 2015-01-04
> **zafod4422 said:**
> Haha, how am I supposed to know? As I said, the monitor is not working at all. Totally black, always. 

What you say doesn't actually make any sense.  I've read this forum for years and nobody before has described a problem with old firmware.  If you've reset to factory settings, then you must be able to see openfirmware, and if you can see openfirmware then you can see yaboot, and if you can see yaboot you can configure the framebuffer, and if you can see the framebuffer you can configure an xorg.conf.

You haven't read the PowerPC FAQ, if you had you would of known not to use the xorg.conf files from mac.linux.be .

---

### Post by zafod4422 on 2015-01-04
Nope, resetting to factory settings doesnt help. I cannot see anything, no openfirmware no yaboot. I can boot into openfirmware though. Check the link above, it describes the problem quite well. Maybe also this one: [http://hints.macworld.com/article.php?story=20050218164736471](http://hints.macworld.com/article.php?story=20050218164736471) . It really has nothing to do with the xorg.conf file, i had the Mac working well after I installed it until I reset the PRAM.

---

### Post by rsavage on 2015-01-04
I haven't looked at those links in detail, nor am I going to, but they just look like a load of voodoo stuff.  Just because it appears on the internet, doesn't make it true.  If there is a real problem, then where is the Apple page on the issue?

As eep asked, what version of Lubuntu are you using?  Have you run an update?  Are you using the openfirmware framebuffer, or the one for you video card (e.g. aty128fb)?  What xorg.conf are you using exactly? Have you tried forcing a mode from the yaboot prompt (albeit blind)?

I don't have an imac, but on my ibook if I have a nvram setting wrong, then I get a blank screen until the xorg kicks in.  That sounds a bit like your problem.  So despite your reluctance, I still think it is fixable through a yaboot parameter/xorg.conf.

---

### Post by rsavage on 2015-01-04
These links hang a bit more info on the problem...

[http://lowendmac.com/2000/350-mhz-g3-imacs/](http://lowendmac.com/2000/350-mhz-g3-imacs/)

at the bottom of the page is [http://tidbits.com/article/6973](http://tidbits.com/article/6973)

---

### Post by rsavage on 2015-01-05
This describes the problem nicely and the kind of thing I was looking for [http://www.capecodgraphics.com/pages/macintosh.html](http://www.capecodgraphics.com/pages/macintosh.html) (linked from [https://discussions.apple.com/thread/1730596?start=0&tstart=0](https://discussions.apple.com/thread/1730596?start=0&tstart=0)).

So I don't see how Lubuntu caused this as is implied in the original post.... it was caused when you installed OS X Panther

---

### Post by rsavage on 2015-01-05
Want you really want is the PRAM setting that has been changed by the OS X installer.  Maybe then you can reset it using the nvsetenv command.  There used to be a command nvvideo ([http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/vivid/powerpc-utils/vivid/view/head:/nvvideo.sgml](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/vivid/powerpc-utils/vivid/view/head:/nvvideo.sgml) ) although this was removed (along with the command vmode) from the powerpc-utils package way back in the 1990s(!) with the comment that the command fbset is better.

---

### Post by zafod4422 on 2015-01-10
That looks good, but how do I use the nvsetenv command. 
OSX used to have a quick fix to this problem, but lubuntu doesn't have that.

---

### Post by rsavage on 2015-01-11
Please answer questions in post 8

---

### Post by zafod4422 on 2015-01-11
[FONT=microsoft sans serif]Im using Lubuntu 12.04. I have not run an update. I dont know which framebuffer im using. I have not tried forcing a mode from the yaboot prompt.
My xorg.conf: [/FONT]
Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
EndSection

Section "Device"
Identifier "Configured Video Device"
Option "ForcePCIMode" "true"
Option "NoInt10" "true"
Driver "r128"
Option "UseFBDev" "false"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Horizsync 30-65
Vertrefresh 50-75
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen 	"Default Screen"
EndSection

Section "Module"
Disable "glx"
Disable "dri"
EndSection
[FONT=microsoft sans serif]
Then again, this problem exists regardless of what OS is currently installed.[/FONT]

---

### Post by rsavage on 2015-01-12
> **zafod4422 said:**
> [FONT=microsoft sans serif]Im using Lubuntu 12.04. I have not run an update.[/FONT][FONT=microsoft sans serif]
then you are using the openfirmware framebuffer.  

Can you try running a 14.04 live iso as that will have a better framebuffer?  Pop the CD in and very soon after press the TAB key.  This will stop it auto-booting into an option.  Type

[/FONT]```
live single [COLOR=#333333][FONT=monospace]video=aty128fb:1024x768-32@75
[/FONT][/COLOR]
```[FONT=microsoft sans serif]

[/FONT]Other modes you can maybe try are 800x600-32@95 or 640x480-32@117 

Another way to do it is

```

live single video=aty128fb:vmode:17

```

For more info on that see [https://wiki.ubuntu.com/PowerPCFAQ#What_yaboot_parameters_should_I_use_for_graphics_problems.3F](https://wiki.ubuntu.com/PowerPCFAQ#What_yaboot_parameters_should_I_use_for_graphics_problems.3F)

Ideally you need another imac g3 user with the same machine to guide you better on what to try.

Btw, you won't get a working xorg with any of the above.

---

