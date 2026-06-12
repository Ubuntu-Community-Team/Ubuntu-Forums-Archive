---
title: "[SOLVED] Help booting X on iMAC G3 from live CD"
date: 2008-06-06
forum: Apple Hardware Users
---

### Post by snaglpus on 2008-06-06
Good day everyone, I need you help.  I have an iMAC G3 Indigo 500mhz 1G RAM and internal CD ROM.  I got this iMAC really cheap and being familiar with LINUX, my plan was to install LINUX on it.  So, after receiving my machine and playing around with OS X, I ordered a LIVE PPC Xubuntu CD version 6.06.  It came, I popped in my CD, rebooted, held down "C" till I got the boot prompt, hit return, it loaded all the necassary drivers and such, I pressed Ctrl, Option, F1 which dropped down to command line.  I went into my xorg file and changed my video settings, save the file, started up X and boom, all worked great!  Up popped the gui and I am just loving it!  However at that time I did not install Xubuntu to my hard drive as planned.  I just tried out the software.

Well, that was a year ago.  SInce then, I've placed my machine on the shelf and it sat there till now.  Today when I try the exact same disk and try the exact same process to boot up Xubuntu, I can never get X to load.  I keep getting fatal error, "*you must remove X0-init.d to run X server*".  Even if I remove this file, it still does not work!

Guys, I have no idea why I am getting this error today when last year every thing worked fine.  Any ideas on what I am doing wrong here?  BTW, I have 3 of these machines that I plan to install Xubuntu on, if I can get X working properly.  Please help.  Thank you for listening.

Snaglpus
:confused:

---

### Post by snaglpus on 2008-06-06
Guys here is more information on my problem.  This is what I get after typing startx.


[I][B]xauth:  creating new authority file /home/ubuntu/.serverauth.5775

fatal server error:
server already active for display 0
if this server is no longer running, remove /tmp/.X0-lock and start again.[/B][/I]

Any idea what is happening?  How do I get X running?

Snag

---

### Post by avtolle on 2008-06-06
Since it sat a year, maybe you should reset the PRAM and give it a go again.

---

### Post by stream303 on 2008-06-06
That is strange!  Just a reminder that unless you need Dapper 6.06x, you can get more up to date community-supported versions here:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Just burn at a very slow speed for your aging cdrom drives at something like 2x or 4x as an iso image, onto CD-R and not cd-rw.

I am intrigued as to why you'd get that error especially off of a live-cd.....

---

### Post by snaglpus on 2008-06-06
Guys, I'm not sure why this is happening.  I am not sure how to reset the PRAM on the iMAC.  I'll google it and see what I get.  Say I tried that CD ROm on all 3 of my iMACs.  I get the same results.  I'll also try to download and burn a CD and see what I get.  One of my iMACs had OS 9.2.  I installed OS X on it and tried the same Live CD and got the exact same results.  One machine has a DVD ROm and the others are just plain CD Roms.  It very well could be my CD.  I'll burn another and see what I get.

Snag

---

### Post by stream303 on 2008-06-07
I believe that an holding down CMD-Option-P-R while powering up and listening for a few chimes should do the nvram/pram deal. (CMD = cloverleaf)

As a side note, on some of the G3's I believe the pmu/smu reset button is to the southwest corner of the lower ram chip - and ONLY push once if you actually need this to be done.

As a reminder about some of the early G3 machines - they sometimes have 8gb or 128gb partitioning limitations, which can throw you off if there are any newer drives installed, requiring custom partitioning.

---

### Post by snaglpus on 2008-06-08
Well, I did as requested and still no results!  Setting my PRAM was not a good idea.  I had to end up reinstalling OS X which took about 4 hours!  Anyway I am back to not able to install Xubuntu!  I get the exact same error trying to install it as my first post.  I downloaded and burned a newer version but that got me nowhere giving me a complete lockup and leaving me a white screen.  So, I trashed the Cd and went back to my orginal CD.  Hey, you guys are the experts!  Help me out, please. 

snag

---

### Post by snaglpus on 2008-06-08
Ok, ok, I got the live CD working on my G3 iMac.  Some of the instructions were here [https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)
But here is what I did step by step:
1.  Slip  in the CD, turn on Mac
2.  Hold down c until "boot" appears
3.  Hit return
4.  After the Xubuntu screen load all the drivers and screen goes black, wait 1 min and press CTRL, ALT, F1
5.  Keep doing that until you get a ubuntu promp
6.  type  sudo pico /etc/X11/xorg.conf
7.  scroll down and look for "dri", place a # at the begining of that line
8.  scroll down and look for "glx", place a # at the beginning of that line
9.  Scroll down and look for Identifier "Generic Monitor"
  Under this section, change the HorizSync to 58-62
10.  Scroll down and look for Identifier "Generic Monitor"
  Under this section, change the VeriRefresh to 75-117
11.  Type Control O, then press return
12.  Type Control x, this puts you back at the Ubuntu prompt
13.  type sudo killall -HUP gdm  and watch what happens!
Up pops the Xubuntu mouse on screen and then the gui and boom!  You are set.  So I solved this thread myself after constantly reading and trying out tips from friends.
thank you for all the support, my live CD works great now.  
Snag:)

---

### Post by stream303 on 2008-06-09
> **snaglpus said:**
> 4.  After the Xubuntu screen load all the drivers and screen goes black, wait 1 min and press CTRL, ALT, F1
5.  Keep doing that until you get a ubuntu promp

Thanks for the nice report and congrats on the live-cd!

I am really interested in the amount of time it took to get to a command line.  Even when you waited a minute, did you have to wait even more time with multiple attempts at CTRL-ALT-F1 to finally see some characters?

If so, this might be an interesting test for those who use other methods like the "alternate" installation and end up at a black screen.  If waiting for a few minutes or more and THEN trying to get to a virtual terminal works, it might be an alternative to passing kernel parameters at the second-stage of yaboot.

---

### Post by snaglpus on 2008-06-09
For me, it was more like 2 minutes.  Right after Xubuntu finished loading the drivers, my screen did black out with a blinkin cursor, but my CD ROM was still loading driver data so I waited one minute and it was still loading.  So, I hit CTRL, ALT, F1 while my cursor was blinking,  after a few seconds, I hit it again, and the cursor stopped blinking.  So, every 5 or 6 seconds, I slowly kept hitting CTRL, ALT, F1 and then up popped command line.  My machine has 1G of RAM.  Those with less will take more time to load in memory.  All the apps work once X is running.  However, the installer on my desktop does not.  It crashes after it tries to particition and format my hard drive.  I think it is because I chose the "Automatically setup option.  It tells me to copy the error files listed in my /tmp/var/log directory to the online bug report, but there are no files.  So, I learned to just shutdown the machine and reboot all over and when I am ready to install Xubuntu, Use the installer but just choose the "Manually setup my particitions option".  The installer can't set up SWAP or BOOT and just gives up and takes me back to my desktop.  I think once I setup the partictions myself, it will install fine.  I'll test it out tonight and reply back with results.

Snag:guitar:

---

### Post by stream303 on 2008-06-09
I wonder if that hard drive is original, or perhaps a larger replacement?  Reason I ask is that very early G3 iMacs had an 8gb partitioning limitation (make it 7gb when actually doing it to be safe), or some have 128gb (make it 125g or less in reality) limitations.  There are several ways to partition, but the simplest is to just keep the entire install under these limits, and use the extra space as general purpose data partition.  (or custom partitions as long as root is below these values).

I would have thought that since you have OSX running, that means that the firmware has been upgraded already - but perhaps that upgrade doesn't address the HD partition limitations?  I'd have to check.

(WARNING - generally do NOT try to install OSX on a G3 that hasn't had a firmware upgrade done to it first from a Mac-os on the hd)

I'm not sure, but wonder if that is happening here....

---

### Post by snaglpus on 2008-06-10
Ok, before I make any changes, help me out.  How should I partition my hard drive?  Here are my current setting:
Partition  Filesystem	Size	  Used	  Unused    Flag
/dev/hda1  unknown	.03MB	  ---	   ---	    ---
/dev/hda2  unknown	.95MB	  ---	   ---	    boot
/dev/hda3  ext2		72.45GB	  1.16GB   72.29G   --- 	
/dev/hda4  linux+swap	2.89GB	  ---	   ---	    swap

What do you recommend?  Remember I have 1GB of Ram.

Snag
:guitar:

---

### Post by stream303 on 2008-06-10
It looks good as long as you've followed the guidelines especially for partitions 1 and 2.  I notice that you've chosen a non-journaled EXT2 filesystem, rather than the default journaled ext3.  Highly recommend ext3 for your root partition.  Swap could probably be a lot less, but for now, not too much of a worry.  I doubt you'll be hitting swap very often. :)

It looks very similar to what would happen if you let guided partitioning use the whole disk and make partitioning formats and layouts for you.  Although I'm not sure you have setup the filesystem types properly for 1 and 2.  I'm away from my Apple box at the moment (you caught me on my first boot of a Knoppix 5.3.1 dvd...)

The only snag *might* be that you would have to keep your root partition under 8gb, or at 7gb to be safe.  If you suspect this is a problem, you could just manually delete all these partitions, and use the "go-back" feature to install to free-space and keep the whole shooting match to 7gb, and use the rest as a general purpose data partition.

I'd have to look at your machine specs again to determine if that 80gb drive is a recent addition, or it came with the machine...


Even if it doesn't work, you could let Ubuntu try to partition the whole drive itself, and then take a look at the partitioning layout as a reference for doing it yourself.

---

### Post by stream303 on 2008-06-10
Here's the output of my own system that is dedicated to Ubuntu, and I have 1.5gb ram.  Note the unecessarily-huge amount of swap. :)  Someday I'll change that, but for what I do, I don't hit swap anyay.

       ```
 #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2         Apple_Bootstrap untitled                1954 @ 64        (977.0k)  NewWorld bootblock
/dev/sda3         Apple_UNIX_SVR2 untitled           303906251 @ 2018      (144.9G)  Linux native
/dev/sda4         Apple_UNIX_SVR2 swap                 8673539 @ 303908269 (  4.1G)  Linux swap

Block size=512, Number of Blocks=312581808
DeviceType=0x0, DeviceId=0x0
```

If your system has that 8gb limitation, just keep your ext3 root partition at 7gb or so.  Hopefully this is not the case.

---

### Post by snaglpus on 2008-06-11
Wow!  You do have a large amount of swap space!  The info I gave you on my system is "as-is", meaning this is how my hard drive looks before changing it.  As soon as I hit the "install Xubuntu manually" button, this is what's displayed on my screen.  I should have taken a screen shot and pasted it in. Anyway, your system shows your hard drive as sda.  Is your hard drive a Compact Flash card?  I'm not sure if my hard drive is original or not.  Probably not.  I want to wipe the entire drive for Xubuntu.  Heck I've got 2 other iMACs on the shelf waiting for Linux.  This is my first time trying to install Linux on an iMac.  I will take your recommendation and make root ext3.  I will make my Swap 2 gb.  I will make root 7gb as recommended also.  And the rest will be Xubuntu. Besides have 2 more iMACs (indigo and flower power) standing by.  I also have a Color Classic II with an upgrade board installed that works fine with OS 6.  My next project is to hopefully install Fluxbuntu or some other distro on it. Thanks for all you help.  it's a good thing I waited partitioning the drive.  I will tackle the install tonight and reply back with results.  Cheers!  Snag

---

### Post by stream303 on 2008-06-11
Typically swap is automatically calculated at anywhere from 1 - 2 - 2.5 times the amount of onboard ram.  When you get beyond about 512mb of memory, that calculation starts to get needlessly huge. :) Ideally, I'd go back in and make the swap smaller, but I never hit it in the first place as seen by top or other utilities, so I got lazy and just left it alone.  Making swap too big is just a waste when you have a lot of memory, but is vitally important when you have much less than 256mb ram.

The size and type of the special apple partitions #1 and #2 are very important - and that is why I usually choose to let the system figure those out for me.

If I start out from a drive with no partitions on it, and need to keep my root partition at either 7gb or maybe 124 gb (depending on model), I'll use the normal free-space install, but use the slider or other way of manually letting the system know to keep it under those limits.  (it's been awhile)

In other cases, I'll use a hybrid technique with the "go back" feature.  I'll start off with a fully automated "use entire disk", let it create the partitions, and when the root partition is too big because the partitioner doesn't know about the early Apple limitations, I'll "go back", switch to manual-partitioning, delete partitions 3 and 4, and repartition the ext3 root partition for a smaller size, and then finish up with a swap partition only 1 -2 times the ram.  THEN I allow it to continue on with the install.

After the install, and everything works, I'll use gparted to just make the rest of the drive's free space into a general purpose ext3 data partition.

Whew, hard to describe - a screenshot tutorial would be nice, but once you've done it once or twice it becomes old-hat.

---

### Post by versemelk on 2008-06-14
ok i get about as far as booting the cd, hitting return  (at this point it says it's booting live, loading kernel) but then after a few seconds my entire screen goes white and it says: "can't allocate initial device-tree trunk"

i have an ancient g3 (blue-ish green-ish) with 256 mb ram

---

### Post by avtolle on 2008-06-14
> **versemelk said:**
> ok i get about as far as booting the cd, hitting return  (at this point it says it's booting live, loading kernel) but then after a few seconds my entire screen goes white and it says: "can't allocate initial device-tree trunk"

i have an ancient g3 (blue-ish green-ish) with 256 mb ram
As you have but 256 mb ram, you are going to need to use the "alternate" CD to install; to install from Live CD, 384 mb ram (for 8.04) is required (this is to handle the graphical installer from the Live CD, although once installed, Ubuntu will run with a Gnome Desktop with 256 mb ram, albeit slowly). If you are already using the alternate install CD, post back and we'll go from there. The alternate install refers to the text-based installer; once installed, you have the full system there.

With only 256 mb ram, have you considered using Xubuntu, which has a lighter DE?

---

### Post by versemelk on 2008-06-14
i'm trying to install 6.0.6 and have tried both the live and alternate cd, sorry for not mentioning that earlier (a)

i'm at the point where i think something might be broken, though os 9 works fine :S

i have considered xubuntu, but i thought i'd try this one first :)

---

### Post by snaglpus on 2008-06-17
Stream, I DID IT!  I got it Xubuntu installed on my g3 iMac.  If you scroll up and look again at my hard drive setup, I had 4 partitions.  Well, I dropped all of them execept #4, swap and clicked back and let Xubuntu install the software.  And it worked fine.  It setup the other 3 partitions the way it wanted.  I rebooted everything worked the way it was supposed to. I logged in and within seconds, there was my desktop!  I am so happy now.  Tomorrow I will install Xubuntu on my other 2 G3 iMACs.  Now that I know what to do, it won't be a problem.  You can call this thread --SOLVED!

Snaglpus
\\:D/

---

### Post by stream303 on 2008-06-17
Great! I'm so glad you got that to work.  What a feeling, huh?

---

### Post by cyberdork33 on 2008-06-17
Please mark the thread as solved from the "thread tools" menu at the top of the thread.

---

### Post by newbiedoobie on 2008-08-04
> **versemelk said:**
> ok i get about as far as booting the cd, hitting return  (at this point it says it's booting live, loading kernel) but then after a few seconds my entire screen goes white and it says: "can't allocate initial device-tree trunk"

i have an ancient g3 (blue-ish green-ish) with 256 mb ram

versemelk, i was having the same problems with the X 6.06 alternate disk...what has worked (so far, it's still loading) is what was described earlier in this thread...after following the older forum tutorial, I was stuck at a blue screen that told me that the xorg.conf file was wrong. This was fixed by the # in front of the gfx line. 

An added tip: if you get to the boot screen and hit enter...it will autoinstall...then when you see the blinking white dash (or underscore) then wait a little while till your CDrom quiets down...when it does, press the CTRL+ALT+F1 command and to know it was recognized, your monitor will make the magnetic sound that is typical of monitors turning on...then the disc will get loud again...and you will have to wait a little while until the screen shows up explaining some legaility stuff and giving you the command prompt. What I did here was just jump the gun and type in the command (the whole sudo pico...) and press enter , which it later recognized and retyped and enters for you. 

All should go well from here and in about 15 minutes give or take you should see the xubuntu logo with the mouse rolling around inside of the logo, then you will see some sky blue screens (before and after the logo screen) until the desktop shows up.

This is as far as I've gotten, because it's still loading but it has been the best effort of mine so far, and I'm working with the same ancient hardware (bought a G3 with factory specs off craiglist yesterday)

Good luck...hopefully (for me too) this works

---

