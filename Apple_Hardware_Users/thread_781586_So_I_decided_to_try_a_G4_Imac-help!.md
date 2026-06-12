---
title: "So I decided to try a G4 Imac-help!"
date: 2008-05-04
forum: Apple Hardware Users
---

### Post by fxrocket on 2008-05-04
OK, after using Ubuntu for about 6 months and lovin it,  my PC died (again) and I figured it is time for another way to go.  So, I purchase a $35 G4 Imac LCD and upon inspection the CD drive and HDD are gone, so I shove some others in there and try to get a live CD (6.06.2) to boot.   I keep getting this stupid flashing question mark folder! (No bootable drive sector sorta warning) Once I did push a few random keys and saw Tux and an arrow for the next section, but then I had other issues and locked up.

SO, I tried the text based CD, I still get the CD drive spiining Up and Down and Up and Down forever, but that folder is still flashing.

I set the HDD to slave and I think the CD/dvd drive is set to master.

I know the keyboard flashes the lights at boot, I hear the chime, then just the flashing question mark folder and the CD spins up-down etc..  I cant get into this  "Open Firmware" at all?  I know nothing about the Mac's but this cant be that hard to at least get it to show me the Ubuntu install info?  Any help at all would be of great use.

I wish I knew what key sequence I used to see tux last time.

:popcorn:

---

### Post by frog_pilot on 2008-05-04
First of all: never connect any drive in master/slave-mode to a macs controller. You have to use the cable select jumper setting. The device at the end of the bus cable (terminating) will be automatically detected as master. If you have 2 ATA-busses, take these two and connect the drives as terminating. Sometimes there are different ATA-Controllers. Make shure to connect the harddrive to the fastest one. E.g. my PM G4 has 3 busses: ATA33, ATA66 and ATA100. I connected the optical drives to ATA33, the system drive to the ATA100 and some backup storage devices to the ATA66.

For CD booting you have to hold the "c" key during startup. To access a graphical open firmware menu with the available boot devices hold "ALT" key during startup. You have to hold the keys until you have video output on the screen.

The flashing question mark means that the default startup volume isn't valid.

---

### Post by stream303 on 2008-05-04
When adding or changing components, it is sometimes advisable to zap the pram, and/or do a pmu/smu reset:

[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

And for the cd, was it burned to a CD-R (not cdrw), at a low speed as an iso image?

---

### Post by fxrocket on 2008-05-04
Thanks guys, I need to pull the drives then and put the DVD on the end of the chain?  

It is burned to a CDR not CDRW.

As far as zapping, I have the reset button on the bottom of the imac, but I cant access anything in the Mac with keyboard commands at all, this has me worried.

---

### Post by fxrocket on 2008-05-05
OK, I took it apart and sorted out the jumpers and the plug arrangement on the IDE chain, and after it sat and spun for a while with the flashing folder/question mark again for a while I fumbled through a few key combo's and got to a screen that shows a square with a CD with a small TUX in the lower corner, to the left of that is a button with a curved arrow (Back?) and to the right of the CD ICon is another arrow that I am guessing is a forward.  

I keep pushing the forward arrow and the CD spins up, but then it slows down again and I get to push it again...but no joy?  

What is going on here?  Possible junk HD not allowing either the text based or live CD to work?

(And what did I push to actually see these buttons anyway?)

---

### Post by stream303 on 2008-05-05
Did you click on the Tux CD icon itself, and then click on the forward button?

You probably got here by holding down the alt/option key when starting up.

Please forgive me, but I gotta' ask: :)
When you hold down the "C" key, do you hold it down long enough to where you can sort of detect it booting from the cdrom?

I mention it because when I first started out, i found that I wasn't holding down anything long enough...

---

### Post by fxrocket on 2008-05-06
I hold down the C key until I see that folder flashing a question mark..it does the same thing if I do nothing.  I cannot seem to get to the setup options no matter what I do.  I am using a windows keyboard, but I read up on the key differences and put a few labels on the different keys.I wonder if thats a problem?

I did click on the tux Icon, but it did nothing.

I was thriled to get a movable mouse pointer last night, but this is getting tiresome, I know Ubuntu prety well, but this mac is kicking my but.

---

### Post by stream303 on 2008-05-06
Hang in there!  I guess it is possible that the system doesn't like your new cdrom, and possibly the windows keyboard.

Some thing's I'd try - try another keyboard.

Can you get hold of a firewire cdrom?  I've successfully used a modern Memorex firewire 400 cdrom to boot and install from, I'm sure other brands do well.  If you decide to go this route, you can boot from it by getting into the openfirmware prompt and issuing:

```
**boot fw/node/sbp-2/disk:,\install\yaboot**
```

---

### Post by fxrocket on 2008-05-08
OK, I swapped out the CD drive for another and also found an older smaller Hard drive...  Now I actually get to the white screen with red text that gives me the option to select how I want to boot ( *live or live-powerpc etc..)  I try both the alt cd and the live cd and they both get stuck after the ramdisk is loaded...what should I check now?  I know these Imacs dont have much ram, is that a problem?

---

### Post by stream303 on 2008-05-09
Which version of Ubuntu are you trying to install?  If you are trying Gutsy, it has been known to get stuck at the busybox prompt:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

It seems that the least amount of memory I've seen in a G4 Imac is 128mb.  I personally recommend using the "alternate" install rather than using the live-cd, especially with lower-mem systems.  Which one are you running?
[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

With a new hard drive, I'd be tempted to zap the pram.  Also, you may be running into a 128gb partitioning limit on that machine, so it is important to find out which one you are using.  Later models didn't have this limitation.

For a first-time install, I'd probably suggest Feisty 7.04, or Hardy 8.04.  Gutsy had issues, but if you're gutsy enough (pardon the bad pun), you can overcome some of them. :)

---

### Post by fxrocket on 2008-05-09
Thanks, I will try to find the ppc version of 8.04 and see if that helps any.  As far as what model I have is a trick question.  Looking at your link I can tell you it is a G4/800 Flat panel 15", but they show two of them and All I know is that mine uses convection cooling on the processor but has a fun in the top of the case above the drives.  But they both show a fan in the description, I am confused because it points out that one of them cannot boot into os9.

Zapping the pram...well, I have not had much luck with keyboard shortcuts and getting into the open firmware Command, Option, P, and R does nothing at boot.  I guess I need to get a mac keyboard now.... Even ALT at boot gives no joy.

Stay tuned.

(Thanks for the help)

---

### Post by stream303 on 2008-05-09
Interesting - I see that one model has OSX preinstalled, and that one has a 32X combo drive, and the other a 24X superdrive.  In any case, I'd burn install images at maybe 4X or lower, even with your new cdrom.

---

### Post by fxrocket on 2008-05-11
Well, I tried the 7.04, same thing happens.  I try all of the options both on Live cd's and on the alt cd. 

 If I try to install I get "elf32 kernal loaded..." Loading ramdisk.....

Ramdisk loaded at 01900000, size 8409 kbytes
Then I get no response, it is locked up tight. The screen stays on the white screen and I cant type.

If I choose check or some options it just goes to a black screen like it is going to sleep.

---

### Post by fxrocket on 2008-05-15
Still nothing, it just hangs at the ramdisk.  I have tried serveral itterations of the OS in both live and alt Cd's.  The ones that do anything at all will all lock up at the ram disk when I try the installers, and if I chose check it goes to a black screen and stops spinning the drive (goes to sleep?)  Any opinion on what I should consider doing next outside of just throwing this imac away?

Could it be ram?

---

### Post by stream303 on 2008-05-15
It could be ram - how much is in your machine? If there seems to be some additional ram installed, is it up to Apple specs?  Perhaps try removing that ram using only the original.

---

### Post by avtolle on 2008-05-15
I'm with stream303 on this one; how much RAM? and if additional RAM was added, try removing back to the original (although if this takes you back to 128 MB, other problems may arise).

---

### Post by fxrocket on 2008-05-15
Well, That may be trouble... All that I have in the machine is the original 256.  I knew from the get go that I would need to use the ALT CD to get anywhere.  I guess I need to find more ram, but 256 should let me get further into the CD, at least it has on PC's.

---

### Post by avtolle on 2008-05-15
> **fxrocket said:**
> Well, That may be trouble... All that I have in the machine is the original 256.  I knew from the get go that I would need to use the ALT CD to get anywhere.  I guess I need to find more ram, but 256 should let me get further into the CD, at least it has on PC's.
The information on updating to 8.04 indicates one needs to have a minimum of 384 mb RAM to run under Gnome or KDE. While I've run prior versions with less, it looks like to me that with all the new "stuff" in 8.04, the 384 figure might be accurate. I obviously don't know, but that's the opinion I've formed. 
Xubuntu would seem to be an option, but there's no PPC release that I've found yet. As indicated on another thread, I did a server install of 8.04 then added xubuntu-desktop to it to "try it out", and things went relatively well, but I abandoned the project after fighting sound problems, among other things. Good luck; I'm (unfortunately) out of here, and won't be back for a day or so.

---

### Post by stream303 on 2008-05-16
At this stage, maybe we can cut down the variables by doing just a server install. (without any major server software running).  Afterwards, you can build it up and determine where to go from there.

Can you download the "server" install image of Hardy PPC, and get that running before tackling gui issues?

If that works, it is possible to do a "diy" installation:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Where you could sudo apt-get install xorg, xterm, xdm, and a window manager - for now just LWM would be fine.  Not that you'd probably want to keep it that way, but if we can't get this to work, then there are other issues...

---

### Post by fxrocket on 2008-05-16
Bahhh...Server puts it to sleep! ???  Screen goes black and I cant get it to wake up?  At least it made it past the ram drive/

---

### Post by stream303 on 2008-05-16
Was this during the install phase, or post-install?

It is possible that you might have to pass some kernel parameters at the second-stage boot: prompt such as:

nosplash
video=ofonly
quiet
break=top

or a combination to get your screen back.  Just hit -tab- at the second-stage to stop the countdown and allow you to type in the parameters.

As a diagnostic, you could also try another distro, such as Feisty 7.04 "alternate".  If that works, we can use some information from it, or just keep it.

Being secondhand, that ram could also be bad, or not the right spec even if it looks original.  That machine seems to have been "parted out" and perhaps someone just threw in some apple ram from another machine...

---

