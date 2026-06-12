---
title: "Booting 8.04 (or anything) on a G4 PowerPC"
date: 2008-05-27
forum: Apple Hardware Users
---

### Post by rocketssss on 2008-05-27
Hello,

I've recently received a donation of an old Mac G4 with ~800 MB RAM and ~800 Mhz processor for my development tasks. All I need is it to boot into some linux environment, and Xubuntu came to mind. However, if I just hit enter at the boot prompt it goes to a black screen, which I let sit for about 30 minutes before pulling the plug. Using "install" with the recommended video option produced a "kernal panic" and it told me it would reboot in 180 seconds.

I don't mind if it's the latest version - I'd just love to get A version of Xubuntu/Ubuntu (preferably Xubuntu) up & running so I can update them.

Thanks in advance for your help! :)


EDIT: and yes, I did try several google/forum searches, to no avail. Apologies if this is already covered :(

---

### Post by stream303 on 2008-05-28
First thing I might do is gather up all your specs:

[http://www.everymac.com](http://www.everymac.com)

Which version did you try to install?  For your requirements, perhaps Feisty 7.04 might be in order.  I recommend the "alternate" install unless you absolutely need to be running a live-cd:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

To save some time and bandwidth, perhaps try one of the mini-iso's that install from the net:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Although xubuntu is good, for a first-try effort, I recommend Ubuntu and then doing a "sudo apt-get install xubuntu-desktop" and switching to it at the next logon.  Maybe later try a dedicated xubuntu iso if you want...

---

### Post by rocketssss on 2008-05-28
Alrighty, looks like I have a [G4 867](http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_867_qs.html) on my hands.

I will have to wait for tomorrow for my bandwidth to roll over ><, but I will ask again if your tips don't solve it :)

EDIT - oh yea, actually, I was running an 8.04 Xubuntu alternate install CD, which is what triggered the errors above.
EDIT2 - if I installed Ubuntu first and then "downgraded" to Xubuntu by switching over on login, is there an easy way to remove the old packages or whatnot I no longer need?

---

### Post by stream303 on 2008-05-28
No problem.  There is a nice way to do that here if you load Feisty:
[http://psychocats.net/ubuntu/purexfcefeisty](http://psychocats.net/ubuntu/purexfcefeisty)

The author also covers doing this in other versions as well.  Pretty nifty.

---

### Post by rocketssss on 2008-05-28
> **stream303 said:**
> No problem.  There is a nice way to do that here if you load Feisty:
[http://psychocats.net/ubuntu/purexfcefeisty](http://psychocats.net/ubuntu/purexfcefeisty)

Er, dumb question - wouldn't that remove some packages used by Xubuntu as well, or does Xubuntu have all it's own stuff? TBH I don't mind if stuff ends up sitting on the HDD, it has an 80GB hard drive and I need perhaps half that.

Over the course of the day I will be using DownThemAll to get Xubuntu & Ubuntu 7.04 PowerPC alternate install ISO's. I'll also be using the MD5 checksum feature & verify the disks after they burn, I'll post my success/failure tonight.

---

### Post by stream303 on 2008-05-28
No, it removes the Ubuntu stuff that is not normally used in Xubuntu, and at the end makes sure that the metapackage for xubuntu-desktop is reinstalled.  For instance, you'll lose the Ubuntu Nautilus file manager, and instead end up with Thunar, which is much lighter and faster, among other things.

You can see exactly what is getting removed by perusing that very long command line.  Be sure to use the right version of that command depending on if you use Feisty, Gutsy, or Hardy - there are differing versions.

If you really like a program in Ubuntu, you could then reinstall it, but it will pull in all the packages and dependencies for it and you'll end up with a custom mix of both Ubuntu and Xubuntu - the choice is yours.

---

### Post by rocketssss on 2008-05-28
I've tried the Xubuntu 7.10 alternative install, hitting enter, "install-powerpc" & "install video=ofonly" all yeild various kernal panics and hang >< I will be trying the Ubuntu 7.10 alternate next.

I contacted the donator and they mentioned that there may be 3rd-party upgraded RAM installed, would that affect anything?

EDIT - The Ubuntu disks flash a white screen then go to black, and nothing happens after that :(

---

### Post by rocketssss on 2008-05-29
Hmmm.. I've tried all the available options that make sense to me at the boot menu, and none of them seem to work. Am I going about this the wrong way?

---

### Post by stream303 on 2008-05-29
> **rocketssss said:**
> I've tried the Xubuntu 7.10 alternative install, hitting enter, "install-powerpc" & "install video=ofonly" all yeild various kernal panics and hang >< I will be trying the Ubuntu 7.10 alternate next.

Have you tried the nosplash parameter in addition to some of the others.  Fortunately with an Nvidia card, you should be able to have a little less trouble:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Those show the live cd options, but with the alternates you could also use the nosplash parameter as well.  You'll have to play with those parameters to get your system past the black screen.

Note that after my first reboot, I stayed in black until the gdm login screen appeared, so I had to use *nosplash* in my yaboot.conf to make it permanent.

> I contacted the donator and they mentioned that there may be 3rd-party upgraded RAM installed, would that affect anything?

As long as the ram meets apple specs you should be ok.  Hopefully it was working when you bought it, and wasn't the reason for selling. :)  I'd keep it in, but perhaps remove the third party ram as a last resort or if nothing but kernel panics show up.

Btw, what is the make/manufacturer of your monitor?  Lcd, crt, size, etc?

---

### Post by rocketssss on 2008-05-29
> **stream303 said:**
> Have you tried the nosplash parameter in addition to some of the others...
Hopefully it was working when you bought it, and wasn't the reason for selling...
Btw, what is the make/manufacturer of your monitor?  Lcd, crt, size, etc?

Yea, it boots into OSX just fine, and has a classic OS partition which probably works as well. (I plan to blow away both partitions when I get an install to work.)

I'll add "-nosplash-" to my parameters. The monitor looks like it came with the machine, it has no power cord, only a DVI-looking thing, and it's an LCD encased in clear plastic, with two USB ports on the back. 

I'll post again when I get home.

---

### Post by rocketssss on 2008-05-29
Using the ubuntu live 8.04 disc and "live-nosplash-powerpc" it does NOT give a kernal panic (hooray!) but seems to hang at "loading, please wait" or give the exception
```
[ 161.9477272] ide-pmac lost interupt, dma status: 8990
```
I'm letting it sit for now, in case it gets anywhere. Some other discs I've tried (8.04 Xubuntu desktop) don't let me use the nosplash option, tells me it can't find the kernel.

I have a feeling I'm getting closer....

---

### Post by stream303 on 2008-05-30
I'll throw a few things out - are you installing the latest "release" of 8.04 Hardy and not a beta?  Early betas had a problem with ide controllers.

Are you burning your iso's on CD-R and NOT CD-RW, preferably at a very low speed?

This might also be a good time to open it up, blow out the dust-bunnies (NO ac connection of course), reseat the hard drive cable connectors, and take a look at the ram to make sure they are securely snug into the holders.  It would be interesting to see if that is a replacement hard drive, and if so, are the jumpers set to Cable-Select (CS) or master?

That box looks to have multiple hard drive controllers / slots that have sometimes proven finicky with Ubuntu installs - but I'd try the previous suggestions first.

If you can boot into OSX, can you get some info from "About this Mac" under the apple icon to see if the memory that is said to be included in the machine is actually detected?  It would also be interesting if you ran a "repair disk" under OSX disk-utility to see if a large amount of errors show up or get corrected.

Speaking of which, did the machine come with OSX install disks?  Just want to be safe in case nothing gets resolved, or if power-management issues force you back to OSX if that becomes a problem.  I hardly ever use OSX any more, but it is still very good to have.

Anyway, thought I'd throw out some of these suggestions before going bananas over the ide / dma issue...

---

### Post by rocketssss on 2008-05-31
I burned Ubuntu 8.04 Desktop live for PowerPC and Ubuntu 8.04 Server for PowerPC just now from the releases/ports section, using the DownThemAll! plugin for firefox to download & check the MD5 sums, then I burned them both to Verbatim CD-R media at 8x speed, and verified the burns with ImgBurn (the CD-Rs are rated at 52x).

I followed the instructions [on the apple website](http://docs.info.apple.com/article.html?artnum=42687) to open the G4, and took a look around (grounded of course). The insides are nice and clean, looks like someone knew what they were doing. A Seagate Barracuda 7200 80 GB hard drive is installed, and there isn't a jumper on the pins at all, which seems odd to me. It has an apple logo on the label farther down, so it might be the HDD that came with the computer? It's hooked up to the second spot on the motherboard cable (AKA farther from the mobo). I pulled the info & power cables out by their tabs and reseated them as you advised.

The ram is clearly & cleanly inserted into the three slots, but I took each one out to get a clear look at them & dust them off a bit. There was one labeled "512 MB SDR DIMM,H 64WHS PO 116709.6", one labeled 256MB "EDGE PC-133 PC133-322-620 PC-100 Compatible" and one labeled "PC133U-333-542 HYM76V16635HGT8-H E AA 128MB Sync 133Mhz CL3". To be honest, none of that means much to me except the MB amounts, so I put each one back in the order they were in, pushing carefully until the tabs snapped back into place.

There was a purple 3.6V battery seated on the motherboard, so I took it's voltage with a multimeter and it reads 4V across the metal contacts. I decided not to remove the battery because I figured that'd reset the CMOS or whatever.

Since the screen I'm currently using has that weird DVI-looking cable that carries both info and current, I'm presuming the graphics card is the apple-branded default that came with it. Everything looked peachy inside so I closed it up.

It booted back up to OSX with no problems, hooked it up to the internet, and ran software update - the only update available was a security update, which I installed & rebooted. In "about this mac" it shows 896 MB SDRAM, which is correct. For processor it shows "867 Mhz PowerPC G4 2MB L3 cache" and a Boot ROM version of "4.3.3f2".

I'm thinking maybe I should delete the 10GB partition that has MAC OS 9 installed on it and have OSX take up the entire hard drive to make things simpler. I'm not sure how to do that on macs though, and I doubt that is what's causing my failure to boot.


After all this fiddling, I tried Ubuntu Desktop with "live-nosplash-powerpc" which sat at the "Loading, pleas wait...." message. I turned it off after a bit over 45 minutes (should I wait longer?) and tried again adding the "video=ofonly" option, which gave the same result, after waiting about an hour I turned it off again. I will be trying Ubuntu Server next.

---

### Post by stream303 on 2008-06-01
In a similar case, a fellow Quicksilver owner (733) mhz had no problems and used the "alternate" installer:
[http://ubuntuforums.org/showthread.php?t=769826](http://ubuntuforums.org/showthread.php?t=769826)

At some point, you'd have to make room for Linux, so that would mean repartitioning your drive.  Yes, you could tell the Ubuntu guided partitioner to "use the whole disk", but of course that would wipe out your working OSX setup.

And there's no guarantee you aren't facing some other sort of problem that is specific to the 867 mhz model.

Do you have the OSX install disks?  If so, you could use those to reinstall OSX to say half of the drive, and install ubuntu to the "free space" left over.  I'd just hate to see you lose OSX experimenting or not being comfortable with OSX repartitioning, and not have any way to reinstall it, and have a big Ubuntu installation issue and end up with nothing in the end.

I'd evaluate your comfort/experience level with the amount of risk involved.

---

### Post by rocketssss on 2008-06-01
Interesting, I will try the alternate install discs using the same md5 & burn at 8x method and let you know what happens.

When I installed xubuntu on an old laptop with windows XP installed on the entire drive, I was able to use the guided :manual" mode to shrink the XP partition and install Ubuntu on the free space provided, since XP wasn't taking up much space. Can I do that with OSX? It takes up barely any space at all.

---

