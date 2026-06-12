---
title: "Nvidia Driver Problem with Feisty Fawn"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by robert_manly on 2007-06-28
This is a newbie cry for help on a new installation of Feisty Fawn.   I have recently installed Ubuntu 7.04 Live Desktop 32 bit version on my old Dell XPS T450 P3 (1999 model) .  The system has 256 MB memory and 6 GB disk. It also has a 16MB Diamond Viper TNT AGP graphics card (Is this an Nvidia card?).

The system installed OK and worked fine except that the graphics were slow to paint the screen.  So I then went to the Restricted Drivers Manager where it suggested that I click the button to install the suggested NVidia driver (only one option suggested).  I installed the driver and rebooted. 

Thats where the problems start.  On reboot, the X server fails to start. So it seems I have the wrong driver (???).  The Xserver diagnostics identify the card as "nVidia Corporation NV4 [Riva TNT]" which sounds right to me - at least the TNT part does.  

I get a fatal server error from the X server which says "Caught Signal 4. Server Aborting". I also get a lot of progress information on the X server startup, which seems to get quite a way into it and then falls over. 

I have only a black screen which allows a command line interface if I log in by using Ctrl/Alt/F1.  So it looks like I have a booted system but no GUI.

Can anyone suggest:
1. Whether this system can be made to run Feisty Fawn, or is the graphics card and/or computer too old?
2. Whether there is a driver available for this graphics card that will work
3. If so, what do I do next to undo the install of the NVidia driver that appears to have caused the problem and install one that works?

Any helpful suggestions would be welcome.

---

### Post by sibot on 2007-06-28
I think you should install Xubuntu, since your config. seems to be not ubuntu capable. This could be causing problems, and even when you get everything work, its gonna be dead slow. Might as well do the best and switch to Xubuntu, its made for old systems. hope it works out!

---

### Post by catnappist on 2007-07-05
I wound up here because of basically the same thing.  I think.  Feisty Fawn has been working great, but I suddenly realized that I couldn't send my video to my TV and decided to install the nVidia driver(s).  I looked it up, clicked system-> administration-> restricted something, and it told me to put my Ubuntu disk in the drive.  I don't remember what it did next, but I suddenly had a clone of my screen on the TV and it told me to restart.  Next thing I get is the screen Robert described, with the X server thing and a nasty DOS-looking screen.  Now I can't boot into Ubuntu and I really don't want to start all over again.  I just got this thing the way I wanted it!

Can ya help a brother?

---

### Post by rohan21 on 2007-07-05
Hi,

I am new to linux and i am using ubuntu 7.04 and having difficulties enabling dekstop effects.

I have a nvidia geforce 2 mx integrated on my asus mbrd, and i have added all repositeries and as well enabled the restricted drivers, but when i restart the  system, it either gives me black screen or a screen filled with nvidia logo, so far i haven't been able to run the desktop effects at all.

If someone can help me, its highly appreciated.

Regards

Rohan:popcorn:

---

### Post by catnappist on 2007-07-05
I don't know what the problem is with nVidia.  The first time I installed Ubuntu 7.04, something popped up within an hour and offered me the option of installing it, which I did, and I never had any problems.  After trying Kubuntu and a couple of other things I didn't like, I came back to Feisty Fawn and don't remember ever getting that offer.  I tried it on my own last night and now I'm screwed (my backup turned out to be messed up so I have to start over...aaaaargh!).  As for the desktop effects, they're experimental, might be a little buggy, and I didn't bother with them on the second install.  Having bouncy windows isn't really worth any potential headaches, at least not to me.  Aaaaargh!

As a parting note, my video card and the nVidia software that came with it work fine in Windows.  It would be nice if I could use that software in Linux.

---

### Post by psyopper on 2007-07-05
The TNT (and anything else before the 6xx series of cards) require using the "nvidia-glx" restricted driver. The "nvidia-glx-new" will not work properly on these cards.

---

### Post by moredhel on 2007-07-05
Are you sure? I have 5200 FX and it's not on legacy.

---

### Post by catnappist on 2007-07-05
I've got a 5200 FX too.  How'd you install your software?

---

### Post by moredhel on 2007-07-05
if that is to me, then through envy. though the restricted drivers management works as well. But i remember when doing it manually it wasn't legacy.

---

### Post by catnappist on 2007-07-05
Sorry, yeah, that's to you, moredhel.  Envy means nVidia, right?  Gotta remember I'm kinda Linux ignorant.

---

### Post by orb9220 on 2007-07-05
> I've got a 5200 FX too. How'd you install your software?

On my fx5200 I used the Envy script which does it for me.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by catnappist on 2007-07-05
Oops, didn't see that we'd gone to a second page. Thanx for the link!

---

### Post by catnappist on 2007-07-05
While I'm here anyway, any idea what folder I screwed up through restricted drivers management?  I have a backup that's nine days old; it's a little screwed up, but I'd like to try everything before I start completely over and have to see that ugly brown screen.  I appreciate any help.

---

### Post by catnappist on 2007-07-05
Yeah, that would've been too easy. :D See everybody in a few hours...

---

### Post by rickycodie on 2007-07-05
you would be much happier with a distro for old computers, puppy linux, xubuntu, or damn small linux.

---

### Post by stchman on 2007-07-05
> **robert_manly said:**
> This is a newbie cry for help on a new installation of Feisty Fawn.   I have recently installed Ubuntu 7.04 Live Desktop 32 bit version on my old Dell XPS T450 P3 (1999 model) .  The system has 256 MB memory and 6 GB disk. It also has a 16MB Diamond Viper TNT AGP graphics card (Is this an Nvidia card?).

The system installed OK and worked fine except that the graphics were slow to paint the screen.  So I then went to the Restricted Drivers Manager where it suggested that I click the button to install the suggested NVidia driver (only one option suggested).  I installed the driver and rebooted. 

Thats where the problems start.  On reboot, the X server fails to start. So it seems I have the wrong driver (???).  The Xserver diagnostics identify the card as "nVidia Corporation NV4 [Riva TNT]" which sounds right to me - at least the TNT part does.  

I get a fatal server error from the X server which says "Caught Signal 4. Server Aborting". I also get a lot of progress information on the X server startup, which seems to get quite a way into it and then falls over. 

I have only a black screen which allows a command line interface if I log in by using Ctrl/Alt/F1.  So it looks like I have a booted system but no GUI.

Can anyone suggest:
1. Whether this system can be made to run Feisty Fawn, or is the graphics card and/or computer too old?
2. Whether there is a driver available for this graphics card that will work
3. If so, what do I do next to undo the install of the NVidia driver that appears to have caused the problem and install one that works?

Any helpful suggestions would be welcome.

256MB of RAM is a bare minimum for Ubuntu.  512MB would work way better.

That 6GB hdd is also too small.  I recommend getting a 20G model if you plan to run Ubuntu.  If you don't want to upgrade then you might try Puppy Linux as it is much smaller.

---

