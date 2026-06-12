---
title: "Old Hardware - Any Tips?"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by hakre on 2006-08-29
Hi! I'm totally new to Ubuntu and I've got quite an old piece of hardware I'd like to run Ubuntu on. I choosed the Xubuntu 6.06.1 alternate version so far, because it was said it's optimized for lowend hardware. But I'm looking for more recommendations so far. Here are my specs:

Pentium S (166 MHz)
Memory:
Base: 640k
Extended: 31744k
Cache: 256k

@my first try, the installer warned me, that it needs at least 37mb RAM. Can I go around this limitation? Later on the installation stopped while it was displaying "e2fsprogs-udeb" at 25%. No Idea why. Maybe this is related having not enough RAM?

---

### Post by az on 2006-08-29
> **hakre said:**
> Hi! I'm totally new to Ubuntu and I've got quite an old piece of hardware I'd like to run Ubuntu on. I choosed the Xubuntu 6.06.1 alternate version so far, because it was said it's optimized for lowend hardware. But I'm looking for more recommendations so far. Here are my specs:

Pentium S (166 MHz)
Memory:
Base: 640k
Extended: 31744k
Cache: 256k

@my first try, the installer warned me, that it needs at least 37mb RAM. Can I go around this limitation? Later on the installation stopped while it was displaying "e2fsprogs-udeb" at 25%. No Idea why. Maybe this is related having not enough RAM?


You need more ram, no way about it.

You probably won't be happy without 128 megs, givem you are using a slow processor.

---

### Post by xyz on 2006-08-29
To get used to Ubuntu, you can just insert the regular Dapper 6.06 (LIVE CD) into your CD-ROM amd boot from it. That way you don't need RAM and it's a good learning experience which will probably prompt you to buy more RAM because you'll just love it too much!!!

Also you may want to try DSL...a distro more adapted to your box's capacities. 
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

...but I wouldn't drag you away from Ubuntu...that's for sure.

---

### Post by FuriousLettuce on 2006-08-29
The Live CD is a BAD idea on your computer. The Live CD loads the OS into the RAM - with that little RAM your computer might explode. If you don't want a graphical interface, install the 'server' edition - download the 'alternate' installer file. This might run. For a normal ubuntu install, however, (and again I recommend using the 'alternate install', which is text-only) I think you definitely need more RAM.

---

### Post by jimcooncat on 2006-08-29
> **azz said:**
> You need more ram, no way about it.

You probably won't be happy without 128 megs, givem you are using a slow processor.

Second that. Here's an old Compaq I set up for some friends with Xubuntu, first thing I did was order more RAM for it. It didn't cost much.

```
top - 11:34:31 up 14 days, 13:30,  1 user,  load average: 0.00, 0.00, 0.00
Tasks:  56 total,   1 running,  55 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7% us,  0.3% sy,  0.0% ni, 89.8% id,  0.0% wa,  0.0% hi,  9.2% si
Mem:    192028k total,   187500k used,     4528k free,    57304k buffers
Swap:   176672k total,    13876k used,   162796k free,    25892k cached

```

---

### Post by bullgr on 2006-08-29
the only you can do with this hardware is to install the basic (server) edition of ubuntu...
and after the installing you can install a light window manager... there is many lightfull window managers, (who fits even in a floppy) but i cannot remember now any.

but there is many howto's to help's you install one..

---

### Post by justin whitaker on 2006-08-29
Bull is right on this: start with a server install, then install a light WM via apt. This will force you to install xorg and a bunch of other stuff as well....but you will get it installed. 

The more RAM you get, the better off you will be, as noted, since your processor is slow.

---

### Post by az on 2006-08-29
> **justin whitaker said:**
> Bull is right on this: start with a server install, then install a light WM via apt. This will force you to install xorg and a bunch of other stuff as well....

Actually, no.  You need to install the X client and server yourself.

One would need to do a server install, enable the universe repository, update and then run

sudo apt-get install x-window-system-core xterm wdm icewm synaptic

and you end up with a really barebones GUI.

---

### Post by justin whitaker on 2006-08-29
> **azz said:**
> Actually, no.  You need to install the X client and server yourself.

One would need to do a server install, enable the universe repository, update and then run

sudo apt-get install x-window-system-core xterm wdm icewm synaptic

and you end up with a really barebones GUI.

I thought it did it automatically. You mean you can install a WM, and apt won't force you to install something to display it?:-k

---

### Post by hakre on 2006-08-29
Woa! Thanks a lot everybody for so many answers and tips. Since I want a Desktop version not a server and plan not to buy more RAM, both of these aren't an option right now.

for using the live or whatever bootcd, the hardware was so old I ran into problems booting from cd. anyway i found out how to handle with that BIOS limitation and posted an HOWTO in the forums ([HOWTO Create a Bootdisk for Ubuntu (on WinXP)](http://ubuntuforums.org/showthread.php?t=246486)) before I found a quite similar information within the documentation.

I myself found out that debian can be installed with 27 MB Ram minimum. I check that out now. Since ubuntu is based on debian (or sort of), I hope noone is offended if I write it down here (just kidding).


I'll keep this thread updated with my experiences.

---

### Post by AirRaven on 2006-08-29
That system's in serious need of additional RAM. You won't be able to get a GUI running on that all too well- IceWM's about as good as it gets on that hardware- if that. 

You'd be better off with just Windows 95/98 unless you're *extremely* fond of not being able to run a single program at a time very slowly.

---

### Post by Jerome36 on 2006-08-29
You might have better luck using something like DSL (Damn Small Linux), on a machine with those specs.  I know you want to use Xubuntu though, so like so many other people suggested, get more RAM.  It shouldn't be too expensive to get more.  I have a really old machine that I plan on throwing more RAM in.  It's like 30 bucks per 128mb module.

---

### Post by hakre on 2006-08-29
Okay, this old computer is really not worth to get that much attention but on the other hand I really like to know how this will work out.

I'm in the second run for the debian installtion because the first one did not work out. I tried to put the full desktop repository on a 400MB partition which smashed it I guess. Anyway within the second run I created a large 1.2GB partion which should handle it I hope.

Anyway, getting more RAM, let's say 128MB at least is really a good Idea. Maybe I consider this in the future.

That's all so far :rolleyes:

---

### Post by hakre on 2006-08-30
Okay, this is day two. First of all I got some help from a friend who really is working with linux a lot since years. He told me to choose the older 2.4.x kernel because it can do most things and it's smaller. That sounded logical to me as well so nothing to discuss long about and I am shure that I do not know it better then he.

The next tip there is: Old Computers are slow and you really need time to do a setup on them. This can be even great, because you can often sit back and relax while working. This reminds me that todays computers are pushing more and more the subject in front of them forward instead of simply helping us.

Nevertheless, If you plan to setup linux on an old computer as well, take your time! And ensure you can do other stuff in parallel.

And if you're within the base installation process, you can press anytime ALT+F2 to open a second console, login as root and do a *shutdown -h NOW* to shutdown the computer. The next day the base install will continue simply after rebooting.

---

### Post by SkyNet2029 on 2006-08-30
Ha ha.. Where to begin? The pentium 166 was/is not a slow processor as goes what was available in its day.on a computational level it usually smoked it competitors running at higher speeds due to its having been introduced as a 'higher-end cpu' destined for server setups. (Most people forget that back in the day we went home to our smoking fast 66Mhz PC's)...Unless you compare it on a 'numerical level' with today's processor speeds. Anyway, with a 256K cache, 32MbRam, Xubuntu will run fine on that machine. If pressed to the point of extinction whilst running a massive HSF combo, it is capable of running U/Edubuntu on it as well. As long as you have enough patience to 'relax' while you are working then you are set. 
I did a similar setup on a machine with a Pentium 166/256kcache/32MbRam but it took about 3 hours to run through the entire install process (for a breezy Badger 5.10 setup, not the server as I was very bored), the longest stalling out being at the 26% mark on the installer. At this point it does not actually lock-up, more than it is just , umm.. processing far more info than it should be tossed at any one time. 
You never mentioned the actual manufacturer of the machine, (older machine's with a 166/256k setup can run stable @ 200Mhz with one jumper reconfig to set it at 100Mhz fsb settings). 
More Ram can't hurt, but it's not as if you will blow things up by staying at the level you are at now. Just make sure you give the 'Services' menu a thourough (sp?) going over to disable anything you really don't need. Since you were running an OS on it prior to all of this (Win95 proly), you are already aware of the actual 'performance' of a 166Mhz cpu. it's about the same running Ubuntu as it is when running Win9x on these machines. 
If you can, a much cheaper ($about .50-$4.00US here) would be to just dump a 200Mhz cpu in the mobo, set the jumpers to 100Mhz on the fsb and be much more able to run the installer at a cpu speed of 233Mhz, since Ram is only useful if you are doing something with it, NOT as an substitute for a cpu.
Again, it takes a very long time for the installer to break past that 26% mark. To go make a sandwich and check on it every 30 minutes would be more realistic a solution than dumping about $50 into Ram on a machine that could be replaced for about $60.

---

### Post by jason.b.c on 2006-08-30
Why not just run [Puppy Linux]("http://puppyos.org/") on it and be done with it...?  <== Not to try to sound rude...:D

---

### Post by ciscosurfer on 2006-08-30
Try here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by anaconda on 2006-08-30
I recommend you to install the server version of ubuntu (as did someone else.) The "server" doesn't mean anything (really).. just that it doensn't install X or any windowmanager, which is a good start with a slow system. Then install fluxbox, which is one of the lightest (and best) windowmanagers (icewm is also very light) xfce isn't very light

I read from somewhere, that it is possible to enable swap in a very early stage of installation.. (just by pressing "Ctrl-Alt-f2" and then using the commands mkswap /dev/hda2 and swapon /dev/hda2 or something..can't remember exactly..)

If I was you I would look at DamnSmallLinux or Puppy-linux, and atleast install one of them to its own ~200MB partition, when you want more speed..

---

### Post by hakre on 2006-08-30
> **SkyNet2029 said:**
> Anyway, with a 256K cache, 32MbRam, Xubuntu will run fine on that machine. If pressed to the point of extinction whilst running a massive HSF combo, it is capable of running U/Edubuntu on it as well.

Maybe I should have had more patience before skipping the 26% percent "halt". If you say so, the actual version (6.06) does work on it, maybe I should try out later *gg*. Anyway what does the sooo coool sounding *running a massive HSF combo* mean?


> **SkyNet2029 said:**
> You never mentioned the actual manufacturer of the machine, (older machine's with a 166/256k setup can run stable @ 200Mhz with one jumper reconfig to set it at 100Mhz fsb settings).
Can't open the box right now, on the outside it's labeld SBC Buisness Computer (maybe the store) and Speedline 586.
The Bios is from Award Software Inc. and a Award Modular Bios v4.51PG #401A0-0105 (C) 1984-95. It was bought in Germany/Europe. Maybe I should open the Box later on and check the motherboard?

Additionally thanks for all your usefull tips. If it does not work out, I can freedos and doom the the machine. With a Pentium and 32 MB of RAM all my childhoods dreams might become true today. Have I mentioned that it got a 3com Ethernet Card? Ha Ha.

---

### Post by hakre on 2006-08-30
> **ciscosurfer said:**
> Try here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Thanks for pointing again back to the docs, I went through the list again and found some very promising links:
[LowEndSystemSupport](https://help.ubuntu.com/community/LowEndSystemSupport)
[LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[Ubuntu-miniRAM-HOWTO](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

Within the later one, it's suggested to start with the server install as well and to use fluxbox as the lightest version, so it's the same what anaconda said:

> **anaconda said:**
> Then install fluxbox, which is one of the lightest (and best) windowmanagers (icewm is also very light) xfce isn't very light

What I did was to install Blackbox on the current Debian Install. Is this in the same direction? All this is based on the cool X, right? I'll look for fluxbox within the package manager as well.

/edit:
I stumbled over [ubuntulite](http://www.ubuntulite.org/drupal/?q=node/1) anyone has checked that out? As describben on their page, it looks like that it is exactly what I'm doing in the end. A ubuntu distro especially for "High End they were" Computers. Why isn't this a Ubuntu community Project, or is it?

---

### Post by hakre on 2006-08-30
Well, install is now over and I could log in the first time "as intended", meaning after the installation closed.

But well, I did not made it *right*. A little *startx* brought to my attention that the device VGA could not have been located. Well, I thought I should have just pressed enter at the point VESA was suggested. But doing a *su* and then *dpkg-reconfigure* enables me to pass that part of the setup again. For ubuntu, as far as I know, you do not su, you just add a sudo in front: *sudo dpkg-reconfigure*.

Well this asks every (and more) questions again (for example about 5 to match my keyboard), but what the hack it took me one day to get this working, I won't care about spending 10 minutes more configuring the system ;). Well indeed it took me about 20 minutes maybe to answer all questions and finally, with VESA as primary display, it did not help! It's not found as VGA is not found.

What can I do now? How do I recognize my Graphics Card? Which driver to use? How do I configure my Graphicsadapter for X only, without answering 30+ Questions all unrelated to the Adapter? :confused: Need to check the docs for that, anyway If someone know the answer, a little tip would be great ;)

---

### Post by ciscosurfer on 2006-08-30
Maybe you should try UbuntuLite like you mentioned?

---

### Post by hakre on 2006-08-30
> **ciscosurfer said:**
> Maybe you should try UbuntuLite like you mentioned?

Before that, I would like to know how to freeze the actual system and create an image of it. I could transfer the image via Network to my WinXP box and then install ubuntulite (the torrent just finished and is seeding very well). [but i want a backup first, so I can restore this one day work afterwards (New Thread about this specific task: Creating an Image of the System)](http://ubuntuforums.org/showthread.php?t=247071) if ubuntulite is not fitting my needs.

---

### Post by SkyNet2029 on 2006-08-30
Glad to see it finally worked for you. Sort of worked. What I meant was an Heat Sink/Fan combo of larger than average size, to aid in you not melting your desk whilst using your machine. Heh. 
As for the 26% halt, it should list as 'SOFT_HALT CPU0' in your installer logs. More a 'hiccup-stop' than a 'full-halt' on the cpu's part. I think it is due to what is listed as an Pentium bug according to 
#cat /proc/cpuinfo
(listed as f00f bug, workarounds enabled). Will need to check on that to be sure though. Just a pentium thing.
On the xserver issue/VGA thinggus, have you tried to just reset the xserver to a base setting by running 
```
$sudo dpkg-reconfigure -phigh xserver-xorg
``` 
?
before doing that though (I am kind of backwards , I know) you might just try running the previous 
```
$dpkg-reconfigure xserver-xorg
```
and specify the amount of Ram available to your graphics card. (Should list at boot-time, prior to your actual bios boot screen, in KB, of course ;)  
and selecting all possible screen resolutions to let the xserver roll through all of them, at the least the output, if it were to crash and burn might prove useful in giving you a more concrete direction to head. 
Dunno bout the image, as I just redo the /home partition if I nuke it too bad, Plus I am extremely patient on reinstalls.

---

### Post by hakre on 2006-08-31
Today I was not able to continue practically. I'm in the mood of checking out the ubuntulite.iso. this means, that i'll kill the debian install. I was unable to install a partimage sucessfully and Mondo did crash debian while being preconfigured. I don't give up but maybe it needs a start from the ground.

Maybe I should optimize the kernel for that machine as well? Would this help?

---

### Post by hakre on 2006-10-28
Okay, some words left to my thread: Thanks for all the support. I finally decided to trash the computer because it took away too much space in my room. Afterwards I went to holiday, that's why I haven't posted for such a long time. I'm still sharing the ubuntulite.iso torrent for anyone who wants to check that out. I would recommend this to test on old computers instead of the "big" ubuntu release.

--hakre

---

### Post by esaym on 2006-10-28
Slackware 10.2 will install on pretty much everything and you can customize what the installer installs :twisted: Not sure what you are trying to do but that just might be an option for you...

---

### Post by esaym on 2006-10-28
> **hakre said:**
> Okay, some words left to my thread: Thanks for all the support. I finally decided to trash the computer because it took away too much space in my room. Afterwards I went to holiday, that's why I haven't posted for such a long time. I'm still sharing the ubuntulite.iso torrent for anyone who wants to check that out. I would recommend this to test on old computers instead of the "big" ubuntu release.

--hakre

oh sorry to hear that :???:

---

