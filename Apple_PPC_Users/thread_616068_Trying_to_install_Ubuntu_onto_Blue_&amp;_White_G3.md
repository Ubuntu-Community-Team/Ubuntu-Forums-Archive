---
title: "Trying to install Ubuntu onto Blue &amp; White G3"
date: 2007-11-17
forum: Apple PPC Users
---

### Post by snow-templar on 2007-11-17
Here is my situation. My dorm floor was selling these used Blue & White Mac G3's for $20 each, so I bought one. I wanted to install Ubuntu into it so I could SSH into in from home during breaks and be able to access my school's internal network, which I need to do to access certain resources for some school assignments. I know it is possible for this machine to run Ubuntu, because that was what was previously installed on here. But the following are my problems:

1) I tried installing the desktop version and when I did a check it returned a checksum 1 error.
2) I tried the live command. It successfully goes to the loading screen, where afterwards it goes to a black screen with a single underscore in the upper-left hand corner as if I am supposed to type something there but it won't let me type and the computer never moves on from that screen.
3) The guy who was in charge of them before mentioned that these machines are underpowered enough that the highest version they can take is 6.10.
4) Due to the fact that these computers had sensitive floor networking information, all the G3's had the hard drive wiped before being given to the person who was buying it.
5) I am used to PC's with BIOS, and apparently Mac's don't have that, so I barely have any idea what I am doing.
6) Only desktop version could load yaboot and kernal.  Sever edition could only load yaboot and alternative could not do either.

And I am trying desktop version now because that seems to be the one version that can load the kernal. I tried the sever edition first, but although yaboot would load, the kernal would not load. I would rather have sever edition than desktop edition, but I can do with either.

Any help would be great, and thanks in advance.

---

### Post by Auria on 2007-11-17
Doesn't checksum errors mean corrupted download? In any case check the intergrity o your download and make sure it's okay. also burn the CD slowly (4X)

From reading your post, i am confused what worked and what did not. First it freezes during install, then it freezes before booting, then desktop edition work, etc. :confused:

---

### Post by snow-templar on 2007-11-17
> **Auria said:**
> Doesn't checksum errors mean corrupted download? In any case check the intergrity o your download and make sure it's okay. also burn the CD slowly (4X)

From reading your post, i am confused what worked and what did not. First it freezes during install, then it freezes before booting, then desktop edition work, etc. :confused:

Okay, let me see if I can explain what exactly happened batter.

First I tried installing the sever edition.  I downloaded the ISO for powerpc and burned the image to a CD+RW I have.  I did it at x4 because that is sadly the fastest speed I can burn at.  Anyways, I put that into the CD drive of my G3.  I turned it off, turned it back on and it automatically booted from the CD, so everything seemed alright.  The yaboot program loaded fine.  It then basically told me I had several options of what to do, but the default was to insert the install command.  So I did.  The response was "Please wait, loading kernel..." and then "Read failed".  I tried the other options available and the same result occurred.  Next I tried the alternative install.  This CD the G3 could not even detect on boot up.  I tried holding down the C key like I've seen written elsewhere and still no go.  Then I tried the desktop version.  This one loaded the yaboot program and then when I entered the live command, it appeard to of loaded the kernal correctly, and then go to the screen with the ubuntu logo and orange loading screen undernieth.  Then it goes to the black screen with the blinking underscore mark in the upper left hand corner.  This looks to me like I am supposed to type something but it won't let me type and the screen never progresses from there.  I then tried some of the other options.  The live-nosplash option eventually just took me to a completely black screen.  The check command returned a failed checksum 1 error.

Those are all the details I think I have.  I am just wondering if the fact the the dude wiped my hard drive before he gave me this G3 has anything to do with the problems.

---

### Post by rockstarwill on 2007-11-18
I had no success with any of the  distros on a b&w g3 until  i used the alternate ppc 7.04 Feisty  which is xubuntu ../xfce  which seems to be running like a champ.

[http://cdimage.ubuntu.com/ports/releases/feisty/release/ubuntu-7.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/feisty/release/ubuntu-7.04-alternate-powerpc.iso)

Is running like a champ .. 

I literally had no problems whatsoever.   

I wish you well.. Its amazing how well a b&w can hold its own.. 20 bucks is a steal.

---

### Post by the_darkside_986 on 2008-03-09
I got a free Blue and White G3 but have had no luck with any distro due to the horrid piece of junk metal known as an "ATI Rage Pro" graphics card it has. And i'll invest in a PS3 before I waste a dime on getting an ATI Radeon 7000 PCI for this thing. So what I am asking, can someone post their xorg.conf if they have a working X server on their B&W G3? I can't figure out any decent settings for getting the "ati" driver to work.

---

### Post by stream303 on 2008-03-10
These boxes may be facing the 8gb or 128gb limitation.

I'll bet that these G3's had upgraded drives and the former owner may have done some manual partitioning on them.  If those drives are not original, and are using larger drives, you may have to do manual partitioning as well instead of letting Ubuntu use free space, or use the whole drive.

When you install, have you tried manually partitioning the drive to use less than 8gb, ie something safe like 7.25 gb or less than 128 gb?

You can get fancy with partitioning to reclaim the additional space, but for now, can you just try to use something like 7gb or or 120 gb and have it running?

---

### Post by stream303 on 2008-03-10
> **the_darkside_986 said:**
> So what I am asking, can someone post their xorg.conf if they have a working X server on their B&W G3? I can't figure out any decent settings for getting the "ati" driver to work.

I don't have a G3 (I'm still waiting), but does the following help - it will take you right to the G3 and ATI settings:

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

and

[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

I hate to see a G3 go to waste!

---

### Post by the_darkside_986 on 2008-03-10
Thanks for the links. I am using a 3rd party monitor which makes things very complicated. Right now, I have a somewhat working version of X via the "fbdev" driver but it only works at 8-bit color, which is pathetic because OS 9 could render the screen in millions of colors. 

But at least now I can read the rendered fonts; I never could find options in OS X to change the resolution and color, which was stuck at 256 colors as well, but the fonts and colors were unbearable and there seemed to be no way to disable the fancy rendering. If only Aqua were an Xserver, or just had some form of a text configuration file, I could have fixed it. I still don't know where OS X keeps its settings (text file, registry, ???) because no one on IRC could/would tell me. 

It is amazing how the G3 running at 300 Mhz runs *nix so amazingly well compared to the awful Intel Celeron 300 Mhz machine that I also have. Such a shame, the switch to Intel.  I wish I could purchase an affordable modern desktop system with a Cell CPU, or some other nice PowerPC cpu. (No, not a restricted PS3.) Then, I would even learn PowerPC assembly language.

---

### Post by stream303 on 2008-03-10
> **the_darkside_986 said:**
> Thanks for the links. I am using a 3rd party monitor which makes things very complicated.

What brand / size / lcd / crt monitor do you have?  Also what version of B+W G3?
[http://www.everymac.com/systems/apple/powermac_g3/index-powermac-g3.html](http://www.everymac.com/systems/apple/powermac_g3/index-powermac-g3.html)

Looks like the maximum resolution is 1600x1200 at up to 85 hz.

You might be able to tweak /etc/X11/xorg.conf manually, or run
```
dpkg-reconfigure xserver-xorg
```

I'm sure we can find something that works...

> But at least now I can read the rendered fonts; I never could find options in OS X to change the resolution and color, which was stuck at 256 colors as well, but the fonts and colors were unbearable and there seemed to be no way to disable the fancy rendering.

Was this in Aqua proper, or just in terminal?  Or was this in Apple's X11 environment provided one installed it..  I'll look into that.

> It is amazing how the G3 running at 300 Mhz runs *nix so amazingly well compared to the awful Intel Celeron 300 Mhz machine that I also have.

This may be urban-legend, but I thought the rule of thumb was that for rough comparisons, you can mentally double the speed of a PPC box to equal what you'd have with an intel cpu.  If that is true, then your 300 mhz ppc was running something equal to a 600 mhz intel. :)

---

### Post by the_darkside_986 on 2008-03-11
Not sure which one exactly, I just know it's the blue and white tower that is only a bulky tower with 128 MB of RAM (normally, but I added more) and a 300 Mhz G3 CPU, with ATI Rage Pro, I think.

The monitor is a Compaq Presario MV500 CRT. I still have fbdev working, but I couldn't get it to work in any color depth higher than 8-bit, the result would be a heavily distorted screen. I never could get X to show anything but blank screens when using the ati driver. The r128 driver simply made X complain about "no screen device found." The default xorg.conf made from auto-configuration never works until I do a manual configuration or editing of xorg.conf.

When the machine was running OS X, it was only running Aqua because I had no idea how to run only X11 or how to shut down Aqua. I know where the Unix terminal is though :). I personally prefer a Debian-based system over OS X any day, so it's all good. But I think it would be fun if I could run just Gnome or KDE in OS X instead of its default display manager. I mean, Aqua is just overkill. I can't imagine trying to play games with that much fancy desktop texture rendering going on.

---

### Post by stream303 on 2008-03-11
Ah, looks to be this bad boy right here:
[http://www.everymac.com/systems/apple/powermac_g3/stats/powermac_g3_300_bl.html](http://www.everymac.com/systems/apple/powermac_g3/stats/powermac_g3_300_bl.html)

And your monitor specs:
[http://en.wikipedia.org/wiki/Compaq_Presario_MV500](http://en.wikipedia.org/wiki/Compaq_Presario_MV500)

Any luck with the ppc faqs regarding ati / radeon etc?

What I've learned about the B & W's was that they have two disk drivers, and sometimes your /etc/fstab can end up pointing at the wrong one. :(  But it sounds like you can get it all installed ok, just your screen image is messed up.  Somewhere, there is just *one* line that will just make that thing pop into place. :)

---

### Post by stream303 on 2008-03-11
Forgot - have you tried the r128 driver, disabling glx or aiglx, and also disabling dri if necessary?

---

### Post by the_darkside_986 on 2008-03-11
Yeah, I've tried r128 and disabling glx and dri. Using ati results in a blank screen that does not cause X to quit. Using r128 causes X to quit with an error message saying "no screen device found" or something like that. oh well.

But at least the desktop is quite usable. My nephew uses it to check his myspace page. Seems to work just fine. None of that would have been doable on my ancient compaq presario with its 300 Mhz Intel Celeron.

---

### Post by stream303 on 2008-03-11
A fellow running OpenSuse 10.2 on his G3 seems to have found an answer by forcing pci mode.  Maybe this will help!

[http://suseforums.net/index.php?showtopic=32359](http://suseforums.net/index.php?showtopic=32359)

---

### Post by the_darkside_986 on 2008-03-12
I keep getting "(EE) No devices detected" after trying that. not sure what the problem is though.

---

