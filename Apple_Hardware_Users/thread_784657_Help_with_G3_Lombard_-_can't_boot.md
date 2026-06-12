---
title: "Help with G3 Lombard - can't boot"
date: 2008-05-06
forum: Apple Hardware Users
---

### Post by egruber on 2008-05-06
I'm an Apple newbie and I tried to search for the answers, but I'm stuck. I have a Powerbook G3 Model M5343 333 mhz running OS9. I searched the model numbers and it should be the Lombard model which makes it New World and should work. Am I correct so far? If so, I cannot get the Mac to boot from the CD (it contains Hardy. I also tried Version 6). I tried booting while holding the 'c' key (letter c, right?). I tried again holding the apple, option, shift and delete together, and that did not work. Holding down other keys such at ctrl, apple, etc don't work either.

I saw another thread that said to go to Apple Preferences, Startup Disk and select the CD.  But I get a message saying the cd does not have the right files to be selected as as a boot disk.  I know 'old world' macs require disk partitioning and other fairly complicated looking steps.  But I believe this is a 'new world' and should boot from the CD.  Any ideas?

(PS. I apologize, but I also posted this in the Install Sticky, but did not get a response.  I thought I might get a little more visibility here)

Thanks!

---

### Post by avtolle on 2008-05-06
Some thoughts, random in nature:

1) How much RAM is in your system?
2) Did you check the md5sum of the iso before burning?
3) Did you burn the iso as an iso?
4) What speed did you burn (the slower the better, 4x or so seems to work best for me)?
5) Once burned, did you check the md5sum of the cd?
6) Did you use a CD-R for your burn? Older macs, such as yours and mine, don't like CD-RWs.
7) Were you using a "desktop" or "alternate" iso? Alternate works best, IMHO.

---

### Post by egruber on 2008-05-07
> **avtolle said:**
> Some thoughts, random in nature:

1) How much RAM is in your system? **512 cache 64MB**
2) Did you check the md5sum of the iso before burning?**Yes**
3) Did you burn the iso as an iso?**Yes**
4) What speed did you burn (the slower the better, 4x or so seems to work best for me)?**4X**
5) Once burned, did you check the md5sum of the cd?**I don't think you can do that. It checks it once it boots, but I didn't get that far.**
6) Did you use a CD-R for your burn? Older macs, such as yours and mine, don't like CD-RWs.**Yes**
7) Were you using a "desktop" or "alternate" iso? Alternate works best, IMHO.**desktop, but if I cannot boot, why would alternate work better?**

**See Above**

---

### Post by ubuntubrian on 2008-05-07
I have successfully installed Hardy on my old Lombard. I upped the RAM to 512mb though and 64mb is pretty small. In any case that shouldn't stop the box from at least trying to boot. 
When I booted Hardy from the live CD or even now with it installed I got a yaboot prompt that asked if I wanted to boot from CD or the hard drive. This happens now with no CD in the drive. If you insert the CD into the drive and reboot your box should recognize a bootable cd and yaboot should give you the prompt. If not then something is weird.
Shut down the box and wait a bit and then hit the ON button and then hold down the "c" key-it should boot if you have a powerpc desktop cd in the drive. It is a powerpc disk? there are some glitches with booting that may come up and you might get thrown into a busybox prompt but you should at least get that far.
Hardy runs sluggishly on my Lombard even with the extra RAM-be advised. There are smaller and leaner distros that may work better for you.
BTW, the alternate CD is for installation so if you want to just try out Hardy you need the desktop CD.

---

### Post by ubuntubrian on 2008-05-07
I think that I misunderstood and you do have 512MB RAM? In any case, just having the cd in the drive when you turn on the box should bring up the prompt or at least it did for me.

---

### Post by stream303 on 2008-05-08
I took a look at your specs for the lombard here:

[http://lowendmac.com/pb2/lombard-powerbook-g3.html](http://lowendmac.com/pb2/lombard-powerbook-g3.html)

and it appears to only have a 2X cdrom.  So maybe burn again at 2X or even 1X.

I'm also a bit confused too as to how much ram you have and how much cache since the specs are similar on the link, but it can be interpreted in reverse. :)

If you have 512mb actual ram, the note seems to state that installers won't work with 512mb and that you should remove one of the chips for install.  After install, you can put extra ram back in since it only "officially" supports 384mb.

If you only have 64mb available, there is a very minimal install you can try:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by stream303 on 2008-05-08
> **ubuntubrian said:**
> Hardy runs sluggishly on my Lombard even with the extra RAM-be advised.

I've seen some interesting Lombard mentions in this ATI Rage 128 thread:
[http://ubuntuforums.org/showthread.php?t=3723](http://ubuntuforums.org/showthread.php?t=3723)

Older info to be sure, but I thought the bit about dropping back from 24 bits default depth to 16 to get some nice video speed was interesting as long as it didn't lock up your video.  Not sure if that is still applicable in hardy though...

Have you run top or htop to see if anything specific is hogging the cpu?  Still a bunch of updates coming for Hardy, and I recently made the switch to Epiphany-browser as a very workable replacement to Firefox for me.  Anyway don't want to get to deep into a browser war. :)

---

### Post by egruber on 2008-05-08
I finally got it to boot (but not successfully). The problem was that I was holding the 'c' key down before I powered up the Mac.  Once I reversed the procedure it recognized the boot CD...so thanks for the tip!

Now, for the next problem.  I tried both Dapper and Hardy.  With Hardy, it begins to start up (I get the logo and moving bar) but after a while I start to get error messages such as h-disp too large, buffer exceeded, etc.  With Dapper, I get the logo and it starts checking off successful load items, but when it gets to 'Configuring X' it moves to a black screen with a blinking cursor and just stays there.

I assume the Mac has 64MB ram and a 512 cache because the label on the bottom says that.  How do I find out if it has been upgraded? Is there a command with MAC OS9 that I can check?

Also, I can try the Alternate image, but I'm not clear what I lose over the regular desktop version.

So....(deep breath), can I run Hardy or Dapper Desktop Versions?  How can I get one of them to load successfully?  And is it worth going to the Alternate version?

Thanks everyone!

---

### Post by avtolle on 2008-05-08
Ok, if there is just 64 MB Ram in your box, neither desktop version will run. IIRC, it takes 256 MB for Dapper (been a while since I used it), and 384 MB for Hardy.  The use of the alternate is for installation, as the text based installer will work where the Desktop won't, due to its need for fewer resources during the installation, but regardless of the "version", the system resources needed to run either Dapper or Hardy using the Gnome or KDE desktop are the same. To find out how much memory is installed, I believe (this is from memory, haven't run anything but Ubuntu for >2 years) under Mac Help, you can select "Memory" and find out.  There are some options if there is only 64 MB Ram installed, but I think you should find out what you have before any further discussion on this occurs.

---

### Post by egruber on 2008-05-08
Thanks for the info.  I'll check it tonight. It's amazing that the MAC can run it's GUI with only 64mb of ram.

---

### Post by avtolle on 2008-05-08
> **egruber said:**
> Thanks for the info.  I'll check it tonight. It's amazing that the MAC can run it's GUI with only 64mb of ram.
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) is something to look at should you find only 64 MB RAM in the box. While it is slanted to the "DOS" side, its suggestions and recommendations are valid across various platforms; until I upgraded the RAM in one of my Cubes from its initial 64 MB, I used Fluxbox on top of a minimal install; slow, but it worked.

Well, to be a bit snarky here, since the Apple GUI is proprietary, and at the time, Apple was shipping many boxes with just 64 MB RAM, it was definitely in their best interests to be sure the GUI would run on that memory; otherwise, not too many machines would be sold. 

Best of luck with whatever you decide to do once you determine your RAM. While additional RAM for our more "mature" machines is a bit higher in cost than RAM for the "latest and greatest", it is still less dear than a new machine.

---

### Post by stream303 on 2008-05-08
Avtolle and I both love that low-memory wiki!

With only 64mb on board, it looks like the only way to go for now.  You actually install the -server- version, (without installing the server-specific software when prompted) and later load up a little lightweight gui on top, ie xorg, xdm, xterm, and maybe icewm or some other window manager.

You may have to end up manually editing your /etc/apt/sources.list file to point to ports.ubuntu.com instead of the normal archives, and also may have to manually edit your /etc/X11/xorg.conf to tweak the video card.

Low-memory systems such as these are excellent projects to think light-weight, and get comfortable with the fastest desktop known: the commandline.  It's not too hard really once you wrap your head around it.

For example, to play an online ogg music stream, I just download vorbis-tools, and at the commandline:
```
ogg123 http://your.url.here:19800/music.ogg
```

You might end up working in an xterm a lot, and to make it look good I usually call up one from the first xterm:
```
xterm -fa mono -fs 14 &
```
(Change -fs XX to whatever font size is good for you)

What - need prettier fonts?
```
sudo dpkg-reconfigure fontconfig-config
```
and then make sure to tell the system NOT to use bitmapped fonts at the last utility prompt.

Now of course you can use lightweight gui browsers such as Dillo etc.

I'd even like to see an Ubuntu forum specifically for low-memory / lightweight installs based on that wiki!

---

### Post by stream303 on 2008-05-08
> **egruber said:**
> I finally got it to boot (but not successfully). The problem was that I was holding the 'c' key down before I powered up the Mac.  Once I reversed the procedure it recognized the boot CD...so thanks for the tip!

Actually thank you!  That may be the cause for many not being able to boot by strictly following the "hold down the "C" key" to boot instruction.  Perhaps we should be careful to modify that to:

"Quickly after power up, immediately hold down the "C" key until you hear/see the system boot from the CD".

Nice catch!

---

### Post by avtolle on 2008-05-08
"Avtolle and I both love that low-memory wiki!" Yes, Stream303, I noticed that previously. :-) 

As I posted earlier, that let me launch into Ubuntu "way back" (for me) when I became the beneficiary of my first Cube from a client who was upgrading hardware. It came with its basic 64 MB Ram, and, at the prompting of my son-in-law, I decided to take the plunge into Linux. Figured out that I'd need to do a minimal (server) install, add a lightweight gui (although not allergic to the command line, as I "broke in on CP/M) just "cause", and off I went, never to look back.

Back to topic a bit; assuming egruber has only 64 MB, as it seems, he could, if he wants to try it straight out, install fluxbuntu ([www.fluxbuntu.org](www.fluxbuntu.org)) and give it a whirl, as they have a ppc version, and, IIRC, he could d/l a live cd to see how it might go.

---

### Post by stream303 on 2008-05-09
Fluxbuntu will be interesting to watch to see if the ppc port is succesful.

Oh man, brought back some memories with CP/M on my two-floppy Televideo.  Remember 
pip <target> <source>
and incompatible filesystems?
Editing with Wordstar?

(I was overjoyed when I started out with Slackware and Yggdrasil distros and discovered the JOE editor when placed into the wordstar mode..)

I always think it interesting to look into the crystal ball and wonder if IBM and dos hadn't come about.  If they didn't exist in the home market, and CP/M ruled the day instead, could you imagine today's systems such as Dell, HP, etc each having different and incompatible filesystems?  Users having to run utilities to just share a simple text file?  ...shudder.. :)

---

### Post by khelben1979 on 2008-05-09
> **egruber said:**
> Thanks for the info.  I'll check it tonight. It's amazing that the MAC can run it's GUI with only 64mb of ram.

I have been running Debian with the use of graphical desktop enviroments myself a couple of years ago(1999).

I wonder how much RAM one really need in order to use a desktop GUI with Linux..? It should be possible to run a GUI with less then 64MB of RAM, right? I don't know about Ubuntu, though. From what I have read here on the forum, Ubuntu seems like a fat and ineffective OS if it really wants as much RAM as been stated here in the thread, hmm.. I know that both Gnome and KDE applications seems to have been grown in filesize over the recent years, is this correct?

---

### Post by egruber on 2008-05-09
Well, I checked the Mac last night and it is only 64MB.  I'm a little disappointed because I thought one of the benefits of Ubuntu was that it would extend the life of older PCs with less resources.  But from reading all the posts it seems  that is not the case.  I may try some of the suggestions though, since we don't use the Mac for anything else.  

Note: I went to the Fluxbuntu site, but there is no build for the PPC yet. Too bad, since I wanted to try it.

BTW, if you want to clarify the boot instrucions, my suggestion is to 

1. Hit the Power button.
2. Wait for the startup tone (music, chord, whatever they call it).
3. Immediately press the 'c' key and hold until the CD boots up.

Thanks for all the tips!

---

### Post by avtolle on 2008-05-09
One only needs the larger amount of RAM if one uses either Gnome or KDE desktops; it is possible, as shown in the Wiki link, to run Ubuntu with a GUI with less than 64 MB RAM, using one of the light weights. 

@Stream303, your post brought back a lot of memories. pip indeed. :-) One of our first personal computers was an Epson QX-10, twin floppies, with what at the time seemed a revolutionary idea, VALDOCS. An early GUI, integrated suite using todays terms; slow by today's standards, but what a revolutionary idea "back then". I still recall working to figure out the bank switching so I could access the full 256 kb RAM (for those who don't recall, 64 kb was all CP/M could access), as VALDOCS did. Played around with Assembler routines, etc., to try to use it. Oh. well, enough of memory lane.

@egruber, sorry about the misinformation. I had thought the FLuxbuntu port to ppc was up and going; my bad. You can use the Lombard by loading the server edition, and adding a GUI as is set out in the Wiki, if you want to experiment. As I indicated earlier, that's the course I chose when I started.

---

### Post by stream303 on 2008-05-09
Funny - our trips down memory lane kind of point to something important if you want to put a 64mb PPC Mac to use.  Technology marches on so fast that the day you buy a computer, it is already obsolete.

64mb!  I remember the famous statement about "640k ought to be enough for anybody" - while sitting at my CP/M box smugly thinking I was max'ed out at 1/10th the ram at 64K!  And now, the typical requirement is that you need 1gb or larger for efficient operation. :)

That old mac might be worth pennies in today's market, but what you learn from it by installing a lightweight Linux environment is worth it's weight in gold.

I guess a weird analogy would be that if I had learned the VI editor for instance back in 1976, I'd be a guru with it today - having been through untold piles of hardware along the way.  But the learning experience about *nix in general is something that won't go obsolete.  With almost 40 years of support and development behind it, I think it's here to stay - even if our Macs end up in the shredder. :)

While desktop environments are nifty, who can guarantee that they will be around in 10 years?  What ever happened to Valdocs? :)  Anyone running the CDE desktop?  I guess the point is that if you are running a low-mem computer, if you learn the basics of the CLI by necessity, you are learning something that will last *much* longer than any of the desktops or hardware you are running now.

I guess I've gotten waaaay off the Lombard topic, so I'll reel myself in. :)

---

