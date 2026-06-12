---
title: "Live Ubuntu for a Powerbook G4 1.33GHz 12&quot;"
date: 2012-11-24
forum: Apple Hardware Users
---

### Post by peezee13 on 2012-11-24
Hi all,

 the question pretty much in the topic title.

I have a 2004 Powerbook Alu with 1.33GHz PowerPC G4 processor and 768MB of RAM (the model in left column here :[ http://support.apple.com/kb/SP83]("http://support.apple.com/kb/SP83") ), whose hard drive is in the process of dying (gives SMART errors). Instead of trying to replace it with a new drive (not for the faint of heart on this model ^^) I'd like to use a Live CD/USB Linux distro, iow one that boots from CD/USB and uses the RAM as a "disk" to operate from (ideally it would use the usb thumbdrive to even save data e.g. config file during a session, but I'm not there yet).

Initially I had to burn CD's to boot from, slow and painful (CD/DVD drive issue I think), but now I'm able to "burn" (on my desktop PC) a thumbdrive with any ISO image containing a Linux distro and boot from it on my Powerbook ( usb drive even recognized as bootable with ALT/OPTION key at boot time, don't have to fiddle with O/F, nice ! )

 (for those interested, I'm using this command in a Win7 terminal to do it : >[COLOR=Blue]dd if=Ubuntu_distro.iso of=\\.\j: bs=1M[/COLOR] )

With that I can boot my PB with Ubuntu and Lubuntu distro's, however never able to get thru to a normal GUI situation : 

 - Ubuntu 12.04 -> boot freezes, I have to add "[COLOR=Blue]nouveau.modeset=0[/COLOR]" to the boot command to get thru to the GUI, however colours are totally messed up it's a psychedelic pixel soup, just unusable

 - Lubuntu 12.10 -> I get the Lubuntu splash screen, but at some point boot freezes; went to single user, added "[COLOR=Blue]single snd-powermac.blacklist=yes  nouveau.modeset=0[/COLOR]" as suggested in the PowerPC FAQ/KnownIssues, this gets me a little further in the boot process but still not up to the GUI, I'm getting an error message with "[COLOR=DarkRed]b43-open/ucode5.fw not found[/COLOR]" in it...

Any suggestion on how to get thru a complete Live install of whatever version or flavour of Linux on my Powerbook would be more than  welcome.

TIA. ;)

---

### Post by 2F4U on 2012-11-24
The firmware for your wireless hardware is missing:

[http://ubuntuforums.org/showthread.php?t=2055717](http://ubuntuforums.org/showthread.php?t=2055717)

---

### Post by peezee13 on 2012-11-24
Thanxx, I looked into the link you provided and added b43.blacklist=yes to the boot command line, but still freezing on the splash screen, so got to reboot in single user mode and see what the next problem is.

Looks like patience and perseverance is going to be key here.

Esp. because I don't have a US EN kbd and it's quite a pain in the neck to enter command lines with special characters...

EDIT : so rebooted in single user mode, but not going anywhere... got a bunch of cryptic error messages, like Exception 300 at tumbler_detect headphone etc... at some point got "Instruction dump:" followed by a couple of lines of hex numbers, last line being : "Fixing recursive fault but reboot is needed!". Yeah, whatever... it's stuck there, don't listen to kbd so can't type reboot so have to reboot manually which will get me back to the same freeze.

Isn't there a simple way to boot Lubuntu with ZERO h/w detection/firmware install (no audio, no bluetooth, no wifi, no firewire, no ...) so as to has at least one chance to get thru all this...?

---

### Post by peezee13 on 2012-11-24
I switched to [COLOR=Blue]Ubuntu 12.04 LTS[/COLOR] (Precise Pangolin), booted from CD, used following  command line at boot prompt :

boot:  [COLOR=Blue]live-powerpc single snd-powermac.blacklist=yes b43.blacklist=yes[/COLOR]

howeverI got for both sound and b43 the same error message : [COLOR=DarkRed]Unknown parameter 'blacklist'[/COLOR]

it then stopped at the b43 error message and from there I couldn't do anything other than shut down the Powerbook.

I'm lost here, these blacklist instructions are the ones provided in the 12.04 known issues section ( [https://wiki.ubuntu.com/PowerPCKnownIssues#A12.04_Precise_Pangolin](https://wiki.ubuntu.com/PowerPCKnownIssues#A12.04_Precise_Pangolin) ), so what's wrong here...?:confused:

Aside from this, I rebooted without providing any specific instruction at boot, and well the thing does boot and gets into the GUI, except that most of the screen is blank/white, with just the top menu bar visible  (with time, settings icon, bluetooth icon, ...) and a purple vertical stripe maybe 50 pixels wide on the left. Tried to Shutdown from the menu there but just go the CD spinning continuously which at some point trigerred the fan to spin like crazy, at some point I had to shut it down manually, looked like entered in an endless loop...

---

### Post by abtabt on 2012-11-25
try this

[http://ubuntuforums.org/showthread.php?p=12372178#post12372178](http://ubuntuforums.org/showthread.php?p=12372178#post12372178)

post #6

---

### Post by peezee13 on 2012-11-26
Thanxx **abtabt**, I will try this, see how good I am at typing "blind" with a non US-EN keyboard... :biggrin:

Actually I just found out the CD I have is for Ubuntu 12.04, not Lubuntu. The Lubuntu distro does not fit on the CD, I also have a DVD+RW I could use except the PowerBook drive is unable to read those.

Also, for some reason I can't boot from the usb flash drive anymore dunno why, what I mean is that the flash drive does appear as a bootable device after rebooting the Powerbook (and holding down the Option key), however when I select it it seems to start booting but stops after a few seconds, the mouse pointer turns into a bizarre round black thing (I can still move it with the trackpad), and essentially it's back to the boot selection screen (which in fact it doesn't leave anyway). So right now I can't boot from Lubuntu 12.04 anymore, stuck to Ubuntu 12.04... Oh well... :-/

---

### Post by peezee13 on 2012-11-26
Ok, so I have scrupulously followed the instructions there, and it did get me further, I can see the Ubuntu desktop now with all GUI elements.

There's still on slight problem though, I guess a picture is worth a thousand words :

[IMG]http://om.zone.free.fr/IMAGES/Powerbook_ubuntu.jpg[/IMG]

So next step : get the colour bitmap right. :)

After that I'll obviously have to resolve the wifi and audio driver/firmware issues, but one step at a time. :)

---

### Post by peezee13 on 2012-11-26
Forgot to mention but my Powerbook has an [COLOR=Blue]**NVidia**[/COLOR] graphics  chipset. And btw just realized both the network AND the audio do work,  since I can listen to a web radio, that's cool. Also, I can access a 8GB usb flash drive I just plugged, wayyyyy nicer than being in single mode, not to mention Open Firmware. :biggrin:

Also, I changed the  desktop background to a fixed colour, I chose green which obviously  shows... a perfect black ^^, but at least now I'm not bothered by the  psychedelic background :biggrin:

I've tried browsing the internal hard drive, which like I said is about to fail terminally, want to recoup a bunch of files, but I'm having problems accessing certain folders, get a message saying I don't have the "permissions necessary to view the contents of" the folder, eg my Desktop folder... any idea why that is ?

---

### Post by peezee13 on 2012-11-27
Ok, well I'm beginning to realize that, despite my setup starting to operate - somehow, my initial objective won't be attainable.

The objective is (was ?) to be able to continue to use my 2004 G4 Alu Powerbook - despite the internal hard drive being almost dead - by installing a "[COLOR=Blue]**Live CD/USB**[/COLOR]" distro of Linux/*Ubuntu, which (in my dreams I'm afraid) would then allow me to browse the web (via tethered or Wifi connection), listen to music, and view movies or youtube type stuff (therefore also requiring flash player/plugin).

It's obvious now after the research I've done, that unless I find a way to have data persisting from one boot to next, I would have to reinstall at each boot specific drivers/firmware (eg wifi, graphics ?, ...) and things like Flash plugin for Firefox, etc...

I need to find a way to boot from a USB flash drive AND have the Live distro write to it in order to save config data, driver updates and stuff, iow I would use internal RAM and usb drive as a replacement for the (dying) HDD.

Or maybe if I can tweak the distro and add to it all the required software such that once booted the Powerbook is fully ready to be used... (no idea if it's possible and how to do this)

I have found distro that can fully boot and operate from usb stick (or even 100% from RAM after booting from usb) - however they are all targeted at **Intel/AMD** processors, not the PowerPC processor running my Powerbook. ( [http://lifehacker.com/5069054/battle-of-the-thumb-drive-linux-systems](http://lifehacker.com/5069054/battle-of-the-thumb-drive-linux-systems) )


So, instead of continuing to spend hours on trying to have this work, I would like to ask the experts here : [COLOR=Blue]**is this a reasonable goal, or should I rather give up ?**[/COLOR]

Thanxx a lot in advance for your help trying to decide.

---

### Post by abtabt on 2012-11-27
> **peezee13 said:**
> Ok, so I have scrupulously followed the instructions there, and it did get me further, I can see the Ubuntu desktop now with all GUI elements.

There's still on slight problem though, I guess a picture is worth a thousand words :

[IMG]http://om.zone.free.fr/IMAGES/Powerbook_ubuntu.jpg[/IMG]

So next step : get the colour bitmap right. :)

After that I'll obviously have to resolve the wifi and audio driver/firmware issues, but one step at a time. :)

yes you need too try this to bitmap 
 

modprobe nvidiafb mode_option=1024x768-16

if we lucky then is looking good (maybe -24 can be ok )

---

### Post by abtabt on 2012-11-27
> **peezee13 said:**
> Forgot to mention but my Powerbook has an [COLOR=Blue]**NVidia**[/COLOR] graphics  chipset. And btw just realized both the network AND the audio do work,  since I can listen to a web radio, that's cool. Also, I can access a 8GB usb flash drive I just plugged, wayyyyy nicer than being in single mode, not to mention Open Firmware. :biggrin:

Also, I changed the  desktop background to a fixed colour, I chose green which obviously  shows... a perfect black ^^, but at least now I'm not bothered by the  psychedelic background :biggrin:

I've tried browsing the internal hard drive, which like I said is about to fail terminally, want to recoup a bunch of files, but I'm having problems accessing certain folders, get a message saying I don't have the "permissions necessary to view the contents of" the folder, eg my Desktop folder... any idea why that is ?

maybe you must be root (sudo )

but if you use live cd do you get this too ??

---

### Post by peezee13 on 2012-11-27
Hey **[abtabt]("http://ubuntuforums.org/member.php?u=161416")**, thanxx a bunch for bearing with me and my questions here... :)

I'll give the Nvidia bitmap thing a try (maybe I'll also want to try with 32-bit depth, which is the chipset capability) and let you know how it goes.

As for the file recoup' issue, I did get the problem while using the Live CD (like I've explained it's the **only** way I can use Ubuntu on this Mac due to HD almost dead), but I've solved it... via the network, not the usb drive (gets me crazy when s'thing really basic doesn't work). From Ubuntu I was able to easily connect to my PC desktop, so I ended up xferring the files from the Mac to the PC this way, so the Powerbook HDD may now die without me worrying (except for my wallet, of course ^^).

Right now I'm searching for a Linux distro that can be booted and fully operated from usb flash drive, incl. the capability to save updated configuration files or added drivers/firmware/plugins/sw application/... to the usb stick. I've already found several of these, however unfortunately **NONE that supports PowerPC processors**. :-/

All in all I'll eventually be forced to upgrade the internal HDD (or to buy another laptop, which I'd obviously rather avoid to), but if there's a cheaper and more fun way to get around this I'll try hard to find it.


P.S. Just for the heck of it, here are the instructions to follow to remove the internal HDD from a Powerbook. See why I'm trying to avoid this ? :-/

[http://www.ifixit.com/Guide/PowerBook+G4+Aluminum+12-Inch+1-1.5+GHz+Hard+Drive+Replacement/548/1?singlePage](http://www.ifixit.com/Guide/PowerBook+G4+Aluminum+12-Inch+1-1.5+GHz+Hard+Drive+Replacement/548/1?singlePage)

---

### Post by rsavage on 2012-11-28
> **peezee13 said:**
> 
Right now I'm searching for a Linux distro that can be booted and fully operated from usb flash drive, incl. the capability to save updated configuration files or added drivers/firmware/plugins/sw application/... to the usb stick. I've already found several of these, however unfortunately **NONE that supports PowerPC processors**. 

You can do this in Ubuntu.  The PowerPC FAQ has instructions - see the persistent USB section.  This works with nomal Ubuntu, but maybe not Lubuntu (I think they skip the test for this....tut....tut).  

A live ISO can be loaded entirely into ram with the 'toram' parameter, but this doesn't work with persistence as far as I am aware.

You can also install a normal system onto a USB drive.  So you could installl Xubuntu this way for example.  You just need to read the FAQ, although it probably sounds complicated.

I don't normally reply anymore to messages which are covered by the FAQ, but I read your first post on the forum and the obnoxious reply you received.  The individual who replied does not represent the forum or PowerPC users.   He knows little about linux and posts incorrect information.  He has been banned/driven out of other general mac forums and has created a bad atmosphere with LowEndMac and linux/bsd users.

---

### Post by peezee13 on 2012-11-28
rsavage, thanx a lot for your help, you're right that one is supposed to read the FAQ before asking here but in fact being a total noob with Linux and even the concept of Live CD (let alone "Persistent Live USB") I didn't really know what/where to look for and indeed what I was up against, coming from a world of having  everything ready and working without a glitch right off the bat with zero shell level instructions to execute to get there.
(Ok, that and tbh got to admit to being quite *scared *by the FAQ lengthiness - not to mention the Known Issues page... :redface:).

Following the discussion here and a few trials I could finally understand and explicit what I was really looking for, it's much clearer now. And now that I know the "what", I *just* need to understand the "how". ^^

Ok so I'll have a more serious look into the FAQ and see if I'm able to pull s'thing out of the reading. And as for the guy in the other topic, I already forgot about him, not a warm welcome I received for a new comer... oh well, thanx for the support here as well anyway. ;)

P.S. English ain't my native language, hope it's just about good enough to make myself understood.

---

### Post by rsavage on 2012-11-29
The first thing to sort out is your screen.  Have you tried nouveau.noaccel=1 as a boot parameter?  You probably just need to swap to unity-2d (see known issues). 
 
Once you have that figured out you can sort out the persistence or installing to usb.  It reads much more compilcated than it is.  If you need help then give us a shout.
 
P.S.  your English is fine!  You spell things correctly (like colo**u**r), unlike people in the USA!

---

### Post by peezee13 on 2012-11-29
[COLOR=Blue]**nouveau.noaccel=1**[/COLOR] => success ! :)

Now that the colours are right, the Ubuntu's GUI doesn't look bad after all... ^^

Guess I'm ready to move to the next step now, I'll eventually come back to resolve the graphics issue after I have the following working :

 -> wifi (b43 error messg)
 -> flash plugin for FF/flash player
 -> switch kbd to FR (easy I guess)
-> work from RAM only ("toram" ?)
 -> boot from USB (hopefully w/o having t resort to O/F)
 -> Persistent Live
-> suspend

and that should be it really, apart maybe from installing few addtional apps.

P.S.  the Mac just went crazy after I opened Firefox, I can hear the CD drive going all over the place for 3-4 mns nows (plus the fan at full speed), is there any way to stop this other than what I'm going to do because I don't know any better: shutdown the Mac, while the drive is spinning ? (ouch!)

---

### Post by peezee13 on 2012-12-01
Oki, so [FONT=Arial]reading [/FONT]the FAQ, Persistent Live USB section, at some point it says :

> 
1- sudo mac-fdisk /dev/sdb
2- sudo mkfs.ext4 /dev/sdb3 -L UbuntuUSB
3- sudo mkfs.ext3 /dev/sdb4 -L casper-rwEDIT : Ok I finally found out about mac-fdisk. (stuff below is an update to this post)

I entered command 1 above in xterm, but this just gets me in the mac-fdisk utility, which prompts for an fdisk type command (to partition, delete a partition, ...). So what am I supposed to do here ?

Then entered command 2, but system complained that /dev/sdb3 was mounted, so had to unmount it, then command executed (Ok, apparently)

Then entered command 3, but got an error message : "*No enough space to build proposed filesystem etc...*"

Am I not supposed to format the drive first to clear out its contents ? How should I do this, using mac-fdisk...?

---

### Post by peezee13 on 2012-12-02
Just a quick note, I have been able to create a bootable Ubuntu 12.04 usb stick, and then boot (Live desktop) from it (via OpenFirmware, as explained in the FAQ), still using the nouveau.noaccel=1 at boot prompt. Way faster than operating from the CD drive, needless to say.

That's good, and promising in terms of being able to switch to Live Persistent USB mode, as soon as I find/understand the missing parts in that section of the FAQ (see post above).

Still need to try the *toram *thing, although with only 768M of DDR I'm not sure it will work.

---

### Post by rsavage on 2012-12-03
Yeah, mac-fdisk is not very user friendly if you are a beginner.  You need to use it (or the GUI Gparted if you are using, for example, a non-PowerPC computer) to partition the drive.  Once you've done that you can format the partitions.  Once you've done that you can write data to the drive.
 
A good example of how to use mac-fdisk can be found here [http://ubuntuforums.org/showthread.php?t=780320](http://ubuntuforums.org/showthread.php?t=780320) .  There are also basic instructions in the "alternate text-installer method" section of the FAQ.

---

### Post by peezee13 on 2012-12-04
Thanxx **[rsavage]("http://ubuntuforums.org/member.php?u=1220329")**, actually I saw that thread last week but at that time had no idea it would be useful to me... ^^

Since last post I tried "TORAM=yes" in the yaboot command line but didn't work (not surprisingly), at some point right before entering the desktop GUI it barfed a dozen of text lines which lasted for approx. 450µs so just had time to see it had to do with RAM usage - after which it resumed normally but no performance improvement and clearly usb flash drive operating full time (i/o RAM as I had hoped).

Also tried to play a mp4 movie, but no H264/AAC codec support in Ubuntu, so converted it to MPEG2/MP3 but no MPEG2 system muxer, so converted to MPEG1 (1990's style) but even that wouldn't work, no system muxer either.

This is perplexing. Is that right that Linux base distros do not include support for even the oldest, simplest, most basic video format ? Or more probably, am I missing s'thing ? :confused:

(Ok the frustration also comes from the couple of freezes (with high CPU util and fan at full speed) I've experienced while trying to install Gnash - and then Synaptic, in order to be able to install Gnash - via the Software Center, each time I launch it it seems to need full CPU power and often gets stuck there... :-/

---

### Post by peezee13 on 2012-12-05
Ok, so following rsavage suggestion and going thru the many steps as explained in the FAQ, I've been able to create a Persistent Live USB Ubuntu 12.04 thing. :D

TBH it's probably at least as much luck as it is work (and some reminiscence from my good ole days working in a Unix environment), esp. the section around mkofboot, I've tried to get the most out of reading 20 times the 6-line explanation ^^, gave it a shot à la "oh what the heck let's just try this !", and voilà, now booting directly from USB flash drive, no need to get thru O/F or anything. Nice !

Next step : RTFM about what "persistence" consists of here, iow what settings can I save - or not save, how it works, etc... and then try it out. Once I have this mastered (lol), I can move on to looking into installing missing drivers, missing plugins, missing applications, missing... ok, enough already ! :oops:

Too bad this thread and the PPC forum in general doesn't generate more activity, more responsiveness, oh well... (and thanxx a great deal to those who do participate here)

---

### Post by peezee13 on 2012-12-05
Oops - doublon.

---

### Post by peezee13 on 2012-12-05
Persistence working fine on my Powerbook, all settings and added  packages have been properly saved everything was still there after  reboot as expected (in fact this is my first post here from that  computer, and first since I could not boot MacOS X from the hard drive  anymore).

Had to add automatic mounting of the separate partition on the USB stick  (casper-rw) in the fstab file, otherwise had to do it manually each  time. Btw after reboot, in the folder view I do have "casper-rw" listed  in the devices section top left pane of the window ( underneath the hard  drive - which as I already said is almost dead and unused) with an  eject button next to it, however if I click on it I get an error messg  "Could not find /cow"...

Now, after successfully installing the required ubuntu-restricted-extras  package, I'm trying to play some MPEG video with MPlayer (Totem)  however it doesn't work, when I double click an MPG file it does launch  MPlayer however it crashes immediately.

If I launch Totem from a terminal, I have the following error msg in terminal :

[COLOR=DarkRed](totem:4830): GLib-GObject-CRITICAL **:  Read/writable property 'object' on class 'ZeitgeistDpPlugin' has type  'TotemObject' which is not exactly equal to the type 'GObject' of the  property on the interface 'PeasActivatable'[/COLOR]

and after loading a movie I immediately get an MPlayer crash and segmentation fault (core dumped) in the terminal.

Have no idea what this means. Could it be due to the fact that I have to  use nouveau.noaccel=1 at yaboot time ? (otherwise display all messed  up)

---

### Post by peezee13 on 2012-12-06
This is becoming a journal of some sort I guess...

Anyway, I've found (by coincidence) the existence of a "gnome-mplayer", ran it on my PC in Lubuntu 12.10 via VBox and worked Ok, so installed it on my Powerbook and... works Ok too. So that's good, starting to approach my initial goal...

Except for the fact that I can't resize the video nor go fullscreen, but for this I highly suspect that the absence of specific NVidia driver in my install (or maybe the nouveau.noaccel=1 switch) is the root cause of this problem, so I'm going to investigate in that direction - which I knew I had to anyway, I want to get rid of the yaboot switch and have full graphics support. Dream on... :-}

Other issue right now is that the casper-rw partition still refuses to automount at reboot, I have to do it manually in disk utility. I have edited the /etc/fstab but after reboot I see that my edits are gone. Need to fix this as well.

On a general note, Ubuntu 12.04 has the CPU running high quite often (and its fan gets crazy noisy), from what I've read (and experienced on the PC via VBox) Lubuntu is not as resource heavy, I also find its GUI a bit more intuitive upfront for someone essentially adept at Win7 (and MacOS but far behind ^^). So I might decide to switch to Lubuntu pretty soon.

Like I needed just that, restart from zero lol... :-]

---

### Post by abtabt on 2012-12-07
> **peezee13 said:**
> This is becoming a journal of some sort I guess...

Anyway, I've found (by coincidence) the existence of a "gnome-mplayer", ran it on my PC in Lubuntu 12.10 via VBox and worked Ok, so installed it on my Powerbook and... works Ok too. So that's good, starting to approach my initial goal...

Except for the fact that I can't resize the video nor go fullscreen, but for this I highly suspect that the absence of specific NVidia driver in my install (or maybe the nouveau.noaccel=1 switch) is the root cause of this problem, so I'm going to investigate in that direction - which I knew I had to anyway, I want to get rid of the yaboot switch and have full graphics support. Dream on... :-}

Other issue right now is that the casper-rw partition still refuses to automount at reboot, I have to do it manually in disk utility. I have edited the /etc/fstab but after reboot I see that my edits are gone. Need to fix this as well.

On a general note, Ubuntu 12.04 has the CPU running high quite often (and its fan gets crazy noisy), from what I've read (and experienced on the PC via VBox) Lubuntu is not as resource heavy, I also find its GUI a bit more intuitive upfront for someone essentially adept at Win7 (and MacOS but far behind ^^). So I might decide to switch to Lubuntu pretty soon.

Like I needed just that, restart from zero lol... :-]

Lubuntu is snappier than Ubuntu and the design is lighter some 
CPU havy  stuff is removed (software handler )

1. you wrote TORAM=yes in my world i use toram its works for 1.5 GB RAM
but you can use it with lower RAM if you use swap  (i tried 768 MB with swap its more snappier with firefox etc

2.you can change swappiness to 1 - 10    (default is 60 )

3.gnome-mplayer if you use nv/aty128fb  driver in your other mac does it work then 

4.you can resize the iso be smaller too (less size on USB )

5.how do you feel the performance

6.how long is boot time from power on to desktop 

when you ready
write a how to i think more people can try this solution

god Thread

---

### Post by peezee13 on 2012-12-07
Hallå abtabt, (nice country Sweden, loved it in Stockholm - except for the beer price ^^)

concerning the "toram" thing, I'm reading this article : [https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM) and now realize I had a rather naive approach to the problem (thinking that simply adding a "toram" switch in the boot command line would make Ubuntu operate from RAM, simple as that - NOT ! ^^).

So I obviously need to do some more thinking here; I'll take some of your advices like creating a "light" version of Ubuntu, eg I do not need OpenOffice in the install, and I can probably strip off other unnecessary stuff from the Distro to make it as lean as possible. In terms of distro, if I have to go thru that level of customization then it make full sense to switch to the lighter Lubuntu right away instead of spending more time on Ubuntu.

How do you change the "swapiness" ?

In terms of boot time we're talking several minutes on my Powerbook, this is quite long. which is also why I need to have "suspend" mode fully working at some point. Unfortunately I'm afraid this is just a pipe dream, considering the problems I'm having with the graphics driver (not to mention Wifi, I haven't even started to work on this issue). But we'll see, one step at a time... ;)

---

### Post by abtabt on 2012-12-07
> **peezee13 said:**
> Hallå abtabt, (nice country Sweden, loved it in Stockholm - except for the beer price ^^)

concerning the "toram" thing, I'm reading this article : [https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM) and now realize I had a rather naive approach to the problem (thinking that simply adding a "toram" switch in the boot command line would make Ubuntu operate from RAM, simple as that - NOT ! ^^).

So I obviously need to do some more thinking here; I'll take some of your advices like creating a "light" version of Ubuntu, eg I do not need OpenOffice in the install, and I can probably strip off other unnecessary stuff from the Distro to make it as lean as possible. In terms of distro, if I have to go thru that level of customization then it make full sense to switch to the lighter Lubuntu right away instead of spending more time on Ubuntu.

How do you change the "swapiness" ?

In terms of boot time we're talking several minutes on my Powerbook, this is quite long. which is also why I need to have "suspend" mode fully working at some point. Unfortunately I'm afraid this is just a pipe dream, considering the problems I'm having with the graphics driver (not to mention Wifi, I haven't even started to work on this issue). But we'll see, one step at a time... ;)

yes the beer is too expensive (but people go to Danmark or Deutchland )to buy sheep beer and buse but not me i dont like 
old beer i like fresh beer for pleasure and old fashion LP 
with god music 
 

didn't this thread work (suspend)
[http://ubuntuforums.org/showthread.php?t=2090462](http://ubuntuforums.org/showthread.php?t=2090462)

i put info in the thread about swap

i hope you dont give up about USB
 
(i use USB/SD card in pc world with good performance with out any harddrive )

):P

---

### Post by peezee13 on 2012-12-07
Thanxx, I'll have a look at that thread.

I need to keep in mind that once booted to RAM any change made in the configuration, any new software installed will be lost at next reboot. At least that's what I understand from reading the BootToRAM page. IOW, Persistent and ToRam are kind of mutually exclusive.

I guess then that I'll need to have a fully operating Live Ubuntu (built over time, booting in Persistent mode to save changes) before wanting to switch to a ToRam boot, which only make sense if you don't want/have to modify your install.

I wonder though whether or not it would be possible to add a symbolic link in /usr/bin pointing to a folder in the USB "user partition" (created when building the Persistent Live USB install), such that even when booting to RAM it would be possible to add programs/software... =P~

Also, from what I see, although Ubuntu is said to be more resource consuming than Lubuntu, the latter's distro is 715M (12.04) and no Open Office to strip off, while the Ubuntu distro is 652M and does include Open Office that I could then remove from it...

So, what is there in Lubuntu that I could remove to make the distro smaller, such that it could fit in my 768MB RAM Powerbook (including swap)...?

---

### Post by peezee13 on 2012-12-07
Ok, let's forget about the toram for now, not a showstopper, more like a potential enhancement once everything's running as it should.

Because of the limitations I have in playing video media (eg impossible to play *full screen* video), I'm now concentrating on the NVidia graphics chipset issue. Well, I _*believe*_ the [COLOR="DarkRed"]nouveau.noaccel=1[/COLOR] switch is the cause of these limitations, but I'm not sure, no one yet has come here to confirm this - but let's assume for now it to be the case.


EDITH : I just played around with gnome-mplayer preferences, and found out there is one mode called "vdpau" which does play the video in full screen, however it's so CPU intensive that it's more like a slide show than a movie, like 4 sec per frame lol. Resizing does work as well. However if I enable video hardware support, the movie doesn't play at all.

Not sure how to interpret this... I wish an "expert" will land here and be kind enough to provide his/her help to get around this (which is a killer issue for me).

---

### Post by peezee13 on 2012-12-07
So have tried various yaboot switches to see if things would improve, most notably this: [http://ubuntuforums.org/showpost.php?p=12336938&postcount=5]("http://ubuntuforums.org/showpost.php?p=12336938&postcount=5"), which brought me back to the "psychedelic" colours I had last week, pretty ugly but still allowed me to try mplayer, and in the end no change, still impossible to go fullscreen with gnome mplayer (actually a little worse, not even vdpau is able to go FS in that video mode).

So... doesn't look like the noaccel=1 switch (which remember allows me to actually use Ubuntu, pretty mandatory at this point) is what's causing the full screen/resize issue. Well, at least that's my conclusion, but no guarantee.

Well, on to doing more research I'm afraid...


Yet another Edith (Piaf) : finally, found a solution for this, MPlayer needs to be told that it's Ok to resize or go full screen (!?!), by adding "zoom=yes" to its config file (in the .mplayer dir under home folder). So now resize and FS work in normal video mode, however when in FS due to CPU at 100% the video goes to a sort of slow motion, sound continues to play but not in sync as you can imagine.

Looks like I'm not going to get what I was looking for with Live Ubuntu on my jig... :-/

---

### Post by peezee13 on 2012-12-08
I'll allow myself one more silly question ^^ :

is there any chance than another Linux distro for PowerPC might have a different, more efficient Xorg s/w, such that playing video would not take such a high toll on the CPU as it does within Ubuntu (much higher than it does in MacOS X with the proper NVidia driver)...?

Thanxx.

---

### Post by abtabt on 2012-12-09
> **peezee13 said:**
> So have tried various yaboot switches to see if things would improve, most notably this: [http://ubuntuforums.org/showpost.php?p=12336938&postcount=5]("http://ubuntuforums.org/showpost.php?p=12336938&postcount=5"), which brought me back to the "psychedelic" colours I had last week, pretty ugly but still allowed me to try mplayer. :-/

did you tried  modprobe nvidiafb mode_option=1024x768-16

and you get "psychedelic" colors too

---

### Post by abtabt on 2012-12-09
> **peezee13 said:**
> I'll allow myself one more silly question ^^ :

is there any chance than another Linux distro for PowerPC might have a different, more efficient Xorg s/w, such that playing video would not take such a high toll on the CPU as it does within Ubuntu (much higher than it does in MacOS X with the proper NVidia driver)...?

Thanxx.

maybe 10.04 work better older X.org

---

### Post by peezee13 on 2012-12-09
Hey abtabt, thanxx again. I tried the modprobe exactly as you mention, and first of all it does get me in the normal desktop environment with no funny colours, so that's good to begin with (so far only the noaccel=1 was able to do just that).

In addition it looks like things improve a bit on the video front, although with all the combinations of video players and codecs and preferences I've tried I'm not sure anymore which one is best, anyway I've been able to play movies full screen with some chopping and lag here and there but globally this is the best I've been able to achieve so far. Note that despite of this, if I try to enable video acceleration it still refuses to play (too bad because that would certainly lower CPU util a great deal, oh well...)

So I'll continue to explore this path, and if it proves Ok I'll try to automate the boot procedure, though I'm not sure it's possible to automate the "blind writing" part...

Now I still have a few issues bugging me :

 1- still refuse to automount the user partition, I have to do a manual mount in Disk Utility after reboot. I have edited the /etc/fstab file but the edits get lost at next reboot. Pain in the neck.

 2- after reboot the audio is muted and volume set to zero, again here this requires manual intervention. I've found a solution for that (with alsactl store/restore) but doesn't work either.

I feel like most solutions I read about are for installed Ubuntu, not Live Ubuntu. I'd appreciate if anyone here could help on these annoying issues.

Thanx. :-)

---

### Post by peezee13 on 2012-12-10
Been wasting hours looking for a working solution to this partition not auto mounting at reboot problem.

Don't understand why nobody here can or want to help on this very basic issue. Pretty frustrating.

**[COLOR="#BF0000"]Looks like it's impossible to force a Ubuntu Live CD system to automatically mount a specific partition at reboot[/COLOR]** in addition to what it does by default, the partition being on the very same disk Ubuntu is installed on. Unless you have to entirely rebuild your install and have to go thru a "Live CD customization" phase ?

I just can't believe this should be so difficult, since Disk Utility properly mounts that partition when asked to (btw where does D.U. get the mount information for that partition ??)

Could Someone PLEASE help on thi - thank you.

---

### Post by abtabt on 2012-12-10
can this help you [http://www.systemateka.com/usbboot.html](http://www.systemateka.com/usbboot.html)

good to hear that modprobe nvidiafb mode_option=1024x768-16
work for you 

if you use 800x400 it can be faster 

btw lubuntu vs ubuntu lubuntu live 590 MB is a lot smaller in ram then ubuntu live 747 MB no swap used

---

### Post by peezee13 on 2012-12-11
Thanx for the link, but WOW! never going to have the time/patience/will to read thru all this.

TBH I've already spent way more time than reasonable on this. I'm now realizing I'd rather had spent the time buying a new drive and reinstalling OSX on it (even though swapping the drive on this model is a real pain in the ***), I thought Linux had made lots of progress towards "user friendliness", it certainly has but boy there's still a LONG way to go imho...

For instance things as basic as creating a symbolic link on the desktop to a folder somewhere in the file system... not so fast, you got to go thru command line to do just this. WHAT ?? In fact I've learnt that the people at GNOME have decided to remove that capability from the U/I, it used to be easy - but not anymore. Why do they do this, to "*improve the user experience*"...? 

Anyway, I'm going to leave it at that, see if it's bearable for me or not, and if not instead of spending more hours and hours searching for ways to do even the most basic things I'll buy a new drive, period.

With all this I feel like having to learn in detail how the car engine works before being able to take it for a trip. Ok it's free in terms of cash which is great, but then if you look at all the time spent, and that's not free...

Also because a little disappointed with the lack of participation here, probably due to the less-than-usual "Persistent Live Linux on PowerPC-based Apple hardware" objective I was aiming at ?


So thanxx again to the few who participated to this thread, but I don't have the patience nor the time frankly to go any further.

---

