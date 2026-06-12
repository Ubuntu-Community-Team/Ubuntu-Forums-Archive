---
title: "flash and java"
date: 2011-10-14
forum: Apple Hardware Users
---

### Post by wxl on 2011-10-14
thought i'd update this whole notion for 2011, soon to be 2012, especially in the dawn of ocelot, which is running nicely on my powerbook. technically, it's lubuntu but that's neither here nor there (unless you want to know how to do it-- write up coming soon).

so i'm looking for flash and java. i have gnash and openjdk/icedtea, respectively right now. 

as far as the former is concerned, youtube and soundcloud were the first two places i checked and no go. i had a go at lightspark and swfdec and neither seemed better but maybe i'm missing something. solution: download the files?

i find the latter to work ok for everything except really complex applets, e.g. logmein. unfortunately, i'd really like to use logmein. so would be nice to find something else. i tried to make sense out of some totally outdated information as it relates to installing ibm java but didn't have any luck. i couldn't convert the rpm and no luck unpacking the tgz. so... ?

thx
w

---

### Post by majortom67 on 2011-10-14
This is how I got them working. From terminal:

-sudo add-apt-repository ppa:ferramroberto/java

then:

-sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

For flash, add the following repository:

- sudo apt-get install gsfonts gsfonts-X11 flashplugin-nonfree

---

### Post by pauljwells on 2011-10-14
@wxl - how did you install ocelot? I can't get either the alternate or the live CD to boot properly on my G5

---

### Post by wxl on 2011-10-16
> **majortom67 said:**
> 
-sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts


i didn't think there was sun java for ppc. you sure you don't have an intel machine?

> 
- sudo apt-get install gsfonts gsfonts-X11 flashplugin-nonfree
why are the gsfonts necessary? and again, i thought adobe flash was ppc only.

> **pauljwells said:**
> 
@wxl - how did you install ocelot? I can't get either the alternate or the live CD to boot properly on my G5     

hate to say it, but that's a topic for another thread. i'd suggest making one if you haven't already. i had some problems originally only to find it was a bad cd. i messed with open firmware and tried all sorts of other things before burning another and having it work. still stuck? make a new thread.

---

### Post by rsavage on 2011-10-17
@pauljwells Hi Paul, other people seem to be struggling with oneiric too.  An update from natty is an easy fix [http://ubuntuforums.org/showthread.php?t=1861871](http://ubuntuforums.org/showthread.php?t=1861871).  The live cd seems to have progressed from a busybox error [http://ubuntuforums.org/showthread.php?t=1858036](http://ubuntuforums.org/showthread.php?t=1858036) to possibly yaboot having no boot options after installation [http://ubuntuforums.org/showthread.php?t=1740629](http://ubuntuforums.org/showthread.php?t=1740629) (am awaiting feedback on what the actual error is).

---

### Post by Pjotr123 on 2011-10-17
Manually installing Oracle (Sun) Java JRE in 11.10 is preferable to using a PPA. Because you know exactly what you are installing. And it's not hard: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by rsavage on 2011-10-17
To stop wxl going mental at all this intel stuff, I'll provide the powerpc info [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) .  Is that the out of date stuff you were referring to?

---

### Post by wxl on 2011-10-17
> **rsavage said:**
> To stop wxl going mental at all this intel stuff, I'll provide the powerpc info [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) .  Is that the out of date stuff you were referring to?

that and [this]("https://wiki.ubuntu.com/PowerPCFAQ#Java").

---

### Post by sammiev on 2011-10-17
> **Pjotr123 said:**
> Manually installing Oracle (Sun) Java JRE in 11.10 is preferable to using a PPA. Because you know exactly what you are installing. And it's not hard: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

+1 I use this method all the time than adding another PPA. :)

---

### Post by rsavage on 2011-10-18
> **wxl said:**
> that and [this]("https://wiki.ubuntu.com/PowerPCFAQ#Java").

Hi, since you are one of the first to try oneiric can you tell me what is not up to date on the post I linked?  I will gladly update the post with your feedback.

I've downloaded and installed ibm java before.  Not sure why you are having problems?  My computer broke before I could fully test so I've not tried the web plugin.

You don't say what is the matter with gnash and lightspark.  The results will depend on your processor speed and graphics card.  More detail would be useful.  swfdec not been developed for years.  You also give no mention of html5 for youtube etc.

If you think the PowerpcFAQ wiki is out of date (which it is) then how about updating it yourself?!  Powerpc is community supported etc...

---

### Post by wxl on 2011-10-19
> **rsavage said:**
> Hi, since you are one of the first to try oneiric can you tell me what is not up to date on the post I linked?  I will gladly update the post with your feedback.
If you think the PowerpcFAQ wiki is out of date (which it is) then how  about updating it yourself?!  Powerpc is community supported  etc...

you miss my point. it is not so much that it's necessarily full of outdated information but that it's old. i don't know what to trust. i do plan on adding my 2 cents when i get it all figured out, don't worry.

> 
I've downloaded and installed ibm java before.  Not sure why you are having problems?  My computer broke before I could fully test so I've not tried the web plugin.
i was never able to actually install it. downloaded it. wouldn't install. tried to install the rpm a la alien. nope. couldn't get make-jpkg to make the tgz a deb. so couldn't do anything with that. therefore stuck.

>  
You don't say what is the matter with gnash and lightspark.
same results: nothing but a blank video window in you tube, soundcloud players that don't do anything, and official.fm widgets that don't appear. the browser draws a space and adblock recognizes the media. i don't hear or see anything.

> 
The results will depend on your processor speed and graphics card.  More detail would be useful.
```
$ cat /proc/cpuinfo 
processor    : 0
cpu        : 7447A, altivec supported
clock        : 1499.999000MHz
revision    : 1.2 (pvr 8003 0102)
bogomips    : 73.72
timebase    : 18432000
platform    : PowerMac
model        : PowerBook6,8
machine        : PowerBook6,8
motherboard    : PowerBook6,8 MacRISC3 Power Macintosh 
detected as    : 287 (PowerBook G4 12")
pmac flags    : 0000001a
L2 cache    : 512K unified
pmac-generation    : NewWorld
Memory        : 1280 MB
``````
$ lspci | grep -i vga
0000:00:10.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)
``````
$ uname -a
Linux xxx 3.0.0-11-powerpc #18-Ubuntu Tue Sep 13 23:42:15 UTC 2011 ppc ppc ppc GNU/Linux
``````
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric
```not sure why that's not lubuntu because it is. installed from the ubuntu live cd no less.
anything else you want to know?

> 
You also give no mention of html5 for youtube etc.
works! but that don't fix soundcloud, official.fm, etc. etc. etc.

---

### Post by rsavage on 2011-10-19
IBM Java: I followed the 'install anywhere' instructions on the IBM website.  Download the bin file, run it and bobs your uncle.  At the end of the install it did give me a message that said there were some errors, but it didn't say what they were and it wasn't immediately obvious to me how to actually figure out what the errors were!  It had installed though.  That's as far as I got.  If you have any further problems with IBM Java then it may be worth posting on the IBM forum?  Try and find out if the firefox plugin works on the latest versions of firefox since that is what you need it for.

Lightspark/Gnash: You sound like you've got the same problem I had with Firefox 5.  Haven't tried them since on PowerPC.  I have no access to a ppc machine at the moment so can only test on my intel.  Both work in Natty and I updated them to the Oneiric versions and they work too.  So I'm thinking there is a problem with ppc Firefox v5 and beyond?

The problem I seemed to have if I remember correctly was that lightspark/gnash were not receiving the swf file.  The player loads in the appropriate part of the page, but there is like a null pointer as the play path.  Can you confirm?  You can see what lightspark does by running firefox from the terminal with "firefox -verbose".

If you downgrade firefox to 3.6 I bet they will work.  Also, maybe try midori?

You can test lightspark on its own.  At a terminal type:
```
wget http://www.adobe.com/content/dotcom/en/devnet/flash/samples/drawing_1/_jcr_content/articlecontentAdobe/generic/file.res/1_coordinates[1].swf
lightspark 1_coordinates[1].swf

```You should see a disk spinning that you can move around with your mouse.  When I tried this last on my ibook (radeon card) it gave me an error, but I have had it working in the past (with KMS on) at the dizzy speed of 1fps!  In your case make sure you are using the nouveau driver and not the nv driver.

---

### Post by wxl on 2011-10-20
> **rsavage said:**
> IBM Java: I followed the 'install anywhere' instructions on the IBM website.  Download the bin file, run it and bobs your uncle.  At the end of the install it did give me a message that said there were some errors, but it didn't say what they were and it wasn't immediately obvious to me how to actually figure out what the errors were!  It had installed though.

after setting up some symbolic links to libstdc++ and libc, i got the installer to run but it crashed soon after, regardless of which interface i use. got farther in console, but only as far as the language prompt.

> The problem I seemed to have if I remember correctly was that lightspark/gnash were not receiving the swf file.  The player loads in the appropriate part of the page, but there is like a null pointer as the play path.  Can you confirm?  You can see what lightspark does by running firefox from the terminal with "firefox -verbose".yeah it sort of seems to do nothing. by the way, i just clicked on the nearest video on the youtube page. don't give me crap about this:

```
Lightspark version 0.5.1 Copyright 2009-2011 Alessandro Pignotti and others
INFO: A plugin was found. Adding it to the list.
ERROR: findPluginInList: no plugin found in list
INFO: The plugin Pulse plugin output only was added with backend: pulseaudio
INFO: the selected backend is: pulseaudio
INFO: get_plugin: pulseaudio
INFO: RenderThread this=0x48282300
INFO: Creating input thread
INFO: X Window 260188e Width: 1 Height: 1
ERROR: Resize not supported
INFO: PLUGIN: NPScriptObjectGW returned to browser
ERROR: Resize not supported
INFO: ~RenderThread this=0x48282300
Lightspark version 0.5.1 Copyright 2009-2011 Alessandro Pignotti and others
INFO: A plugin was found. Adding it to the list.
ERROR: findPluginInList: no plugin found in list
INFO: The plugin Pulse plugin output only was added with backend: pulseaudio
INFO: the selected backend is: pulseaudio
INFO: get_plugin: pulseaudio
INFO: RenderThread this=0x48282300
INFO: Creating input thread
INFO: X Window 2601d20 Width: 640 Height: 390
ERROR: Resize not supported
INFO: PLUGIN: NPScriptObjectGW returned to browser
ERROR: Resize not supported
INFO: Newstream for https://s.ytimg.com/yt/swfbin/watch_as3-vflelJfZw.swf
INFO: NET: Downloading to memory
```> If you downgrade firefox to 3.6 I bet they will work.  Also, maybe try midori?meh i don't really want old firefox. no help from midori.

> You can test lightspark on its own. You should see a disk spinning that you can move around with your mouse.  When I tried this last on my ibook (radeon card) it gave me an error, but I have had it working in the past (with KMS on) at the dizzy speed of 1fps!works around 25fps. 

> In your case make sure you are using the nouveau driver and not the nv driver.i find both
kernel/drivers/video/nvidia/nvidiafb.ko
kernel/drivers/gpu/drm/nouveau/nouveau.ko
in modprobe. i'm thinking the former is just framebuffer, i.e. i'm using nouveau? i'm really curious about this, a bit off topic, because i can't suspend/hibernate properly.

---

### Post by rsavage on 2011-10-23
Hi, wondering if you have got any further with this?

I didn't setup any symbolic links for IBM Java.  I remember installing libstdc++5.

That swf file is just some generic file.  I don't see any reference to the Justin Bieber video that we all know you clicked on.  Was that the full extent of the output? You should have more.  What about another video?  Try [http://www.youtube.com/watch?v=qlYDtV-hIJg](http://www.youtube.com/watch?v=qlYDtV-hIJg) 'cos that works with lightspark on my Toshiba.

It would be useful if somebody could test Firefox 3.6.  What happened with midori?

25fps is not bad.  I got 30fps on my 3 year old laptop.

Have you tried suspend using powerprefs?  Last time I looked into this the kernel was not reporting that suspend was available I think.

I got JamVM working with the IcedTea java plugin on my Toshiba.  I've added a bit more about it on the lubuntu thread.   I had to set it as the default virtual machine.  Don't know if there is a better way.

Not having PowerPC makes it very limiting for me to help you on this.  Would be good to get the feedback from others too..... anyone?

---

### Post by wxl on 2011-10-28
Didn't get nowhere unfortunately. Same problems, including with Midori. Anywho, thanks for the help. We'll wait for someone else to show up.

As an aside, it doesn't really help with this problem but I've seen some major improvements relative to Lubuntu, Ubuntu, and Debian installs with that frankendistro that is MintPPC. If you get another PPC, it comes recommended.

---

### Post by rsavage on 2011-10-28
Yes I had seen you had jumped ship.  It's a pity you didn't say what problems you were having with lubuntu as maybe somebody could of helped you?  The information could have been useful to other people with similar problems trying to find the solution.

No offence to those over at MintPPC, but I wouldn't touch it with a barge pole!  I maybe more interested in it if it was an official port of Linux Mint, but ripping off somebody else's work seems wrong to me.  We'll never know what actual changes have been made because MintPPC doesn't release source code!  Not very open source!  Also, history says ppc only distros don't last (yellowdog) even if MintPPC is practically just debian.

---

### Post by linuxopjemac on 2011-10-28
rsavage: MintPPC is pure Linux Mint, ported to PPC. That you fight a lonely battle to keep users in Lubuntu, that's your problem. Don't talk rubbish please and be honest.

---

### Post by rsavage on 2011-10-28
@linuxopjemac Yes I'm quite keen on ubuntu to carry on with PPC. Whether that is lubuntu, xubuntu, ubuntu, or kubuntu and the various variations provided by lucid, maverick, natty and oneric. The fact is ubuntu offers a vast choice to suit whatever machine you have. MintPPC doesn't and it would (in my opinion) be a complete waste of a machines resources to use say a G5 to run stock MintPPC.
 
I don't go on the MintPPC forum and slag off MintPPC like you have done here in the past with ubuntu. In fact, please point me to a post on this forum where I have been unfairly derogatory to MintPPC. I think you would struggle.
 
As for comments in the post above, well I really don't know what your problem is since I'm only going by what you have written on your own website. From [http://www.mintppc.org/about](http://www.mintppc.org/about) "MintPPC is not affiliated with Linux Mint but it uses the same underlying source code" and "Because of a conflict with the Linux Mint team, the name of the distribution was changed into MintPPC". So it is not an official port and by the sounds of it the Linux Mint team were not best pleased with you? Finally, since I don't use MintPPC I didn't know you didn't release the source code until you wrote it yourself in this thread [http://www.mintppc.org/forums/viewtopic.php?f=10&t=508](http://www.mintppc.org/forums/viewtopic.php?f=10&t=508) .

---

### Post by linuxopjemac on 2011-10-28
The source code is the same as Linux Mint. For MintPPC 11 it's published though.

---

### Post by B_Free on 2011-10-28
Guys, guys!
Not to change the subject but have you heard of Q Emulator or iEmulator? These are for the PPC. Q recognizes the cd of Ubuntu but just sits there. If you try these (Q Emulator is free) and if you could make it work, there would not be a problem with installing to the hard drive. Just another piece of software.

[http://www.macupdate.com/app/mac/20830/q-emulator](http://www.macupdate.com/app/mac/20830/q-emulator)

[http://www.kju-app.org/](http://www.kju-app.org/)

[http://www.iemulator.com/](http://www.iemulator.com/)

---

### Post by barbaGNU on 2011-10-29
i still prefer CRUX PPC and i've firefox+gnash working altought ff is 3.6.x
I asked for an update but it seems they are waiting for a firefox release  with ppc nanojit fixed.

---

### Post by wxl on 2011-10-31
holy thread hijack. ya'll need to chill out and play nice :D

anyways i never said i was jumping ship, but that i found an experience with mintppc i didn't find anywhere else. i'm still rather fond of lubuntu and hope that in using mintppc i can learn some things to help ppc users of both lubuntu AND debian (for that matter).

still, though, even with mintppc i have yet to see improvements on the flash/java front. i don't know what the deal is.

---

### Post by pauljwells on 2011-10-31
@rsavage and @linuxopjemac!!

As two of the most respected posters on the PPC linux forum PLEASE don't squabble. There aren't enough of us to form factions!

I sometimes think that there's only you two trying to nurse any kind of PPC linux along anymore. Lubuntu is great, MintPPC is great. Let's make sure whatever flavour we use can keep up with the x86 code or we might as well take all our machines out to the dumpster right now... :-(

---

