---
title: "Black Screen on installation"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by cajungenes on 2006-11-08
:confused: 
I have been unsuccessful so far in running Linux from the LiveCD.  When I try, the CD starts up and goes through the load up sequence and then has 'ok' next to each line.  When it finishes loading from the LiveCd the monitor goes black.  I can hear music like the CD is still running, but I can't see anything, and that's that.

I have tried running the CD in safe mode with a lower resolution, but I get the same results.  

I called CompUSA, where I bought my Norwood Micro Monitor, and ATI X1300 Radeon Video Card in March, and they told me I needed a special linux driver and I should get it at the ATI website.

I went to the ATI website and they had a notice that they didn't support Linux, specifically, but that I could probably find drivers through the linux community.

I am VERY new to Linux, in that I have never used it, and have never been successful in getting it installed. I read on here somewhere that there is some type of alternate CD for problems like this. I didn't get one with the LiveCD 6.06 LTS,  I received from Ubuntu.  

Should I have received an second alternate CD with the original? 

I'm open to ANY suggestions or tips that you may have. This has been a very long and frustrating ordeal.

thanks,

cajungenes

---

### Post by Ecthelion on 2006-11-08
> Should I have received an second alternate CD with the original? 

No. You can download an alternate cd [here]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download").
Click on "Other installation options" from a mirror that's close to your location.

Then scroll down to "Alternate install CD" and download.
Burn it as slow as you can.

You can use this cd to install xubuntu and then you might have to install your drivers.
The alternate cd isn't a "live cd".

To learn more about Xubuntu, click [here]("http://www.xubuntu.org/")

---

### Post by cajungenes on 2006-11-10
Have burned alternate CD and am in process of installing. Have a 250 gb hard drive and have made the first parition for 30. In setting up the second partition, it is asking for a mounting point such as "/boot" -- which should I select or should I choose "do not mount" option?

Also I plan to set up three more partitions and need to know how to establish their mount points. Will the mount point determine how the partition can be used or will I be able to use each as I want, regardless of the mount point?

I also have a second 80 gig drive that I plan to use as for the swapfile partition. How should I set the mount point for that and will the process wipe the drive completely?

I await your response as I will not continue the set up until I hear from you. Better safe than sorry!

---

### Post by petri on 2006-11-10
Here is an illustrated installation howto for Alternate CD [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

You may need 1 GB swap. More than that nowadays is not necessary. Usual recommendation for swap is 1,5-2 times your RAM. 80 GB swap is kind of... :rolleyes:  ;) 

You really should get as few partitions as possible. One for root, one for /home and one to swap. Maybe one for /boot but then you need to be a little bit more experienced in Linux. In the beginning you will install Ubuntu a couple of times believe me. As you learn Ubuntu, you will play with it and something will go just wrong 8)  That's why a separate /home is good from the beginning.

Check the link, Herman will show you how to do it! :mrgreen:


EDIT: One more thing. You may get blank screen after installation but then you can reboot with recovery mode and change the driver "ati" to "radeon" (or was it vice versa?) by writing in root prompt: **nano /etc/X11/xorg.conf** There is only one line with "ati" or "radeon" so you can't miss it.
One even more thing: you can install the fglrx drivers with [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) for Dapper and for Edgy [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) they work everytime ;)

EDIT 2 : Welcome to Ubuntu! :mrgreen:

---

### Post by cajungenes on 2006-11-10
Thanks for the info! Am well into the process outlined on the link you furnished and things are looking good! Will give an update on success when finished and, since this is further than I've ever gotten before, I'm delighted!

---

### Post by cajungenes on 2006-11-10
You were right about the blank screen. I tried typing the nano/etc/X11/xorg.conf  and got a file doesn't exist message. Tried   recovery mode and attempted your other suggestion.  I can't figure it out, or it's not installed right because it's behaving exactly the way the LiveCD did, it loads completely and then the blank screen.  I didn't really understand how to install the driver by switching from ATI to Radeon. I couldn't find the line you mentioned.

---

### Post by abaddon1215 on 2006-11-10
Did you type this:  sudo nano /etc/X11/xorg.conf

---

### Post by cajungenes on 2006-11-10
no, I didn't realize I had to type sudo. I will try that.

---

### Post by cajungenes on 2006-11-10
I tried that and this is the response I got.
sudo: nano/etc/X11/xorg.conf: command not found

I also tried typing sudo: and enter and then the string nano/etc/X11/xorg.conf and received the same command not found

---

### Post by cajungenes on 2006-11-10
Tried typing command one more way -- sudo nano /etc/X11/xorg.conf -- and did get to the file "GNU nano 1.3.10 File: /etc/X11/xorg.conf. Found ATI mentioned in two lines: once under Section "Device" and once under Section "Screen." In both sections, the line reads "ATI Technologies, Inc. ATI Default Card" so am not sure which of these two should be changed or is it both of them? Under "Device," it has Driver "vesa" and, under "Screen," it just says "generic monitor."

Thanks for all your help on this!

---

### Post by meborc on 2006-11-10
there is a space after nano... :)

ant the best way to go about reconfiguring the xserver after new video card installation, or change in drivers (or just to get the right rezolution) is:

```
sudo dpkg-reconfigure xserver-xorg
```

in linux CAPS and SPACES are VERY important :mrgreen: so next time, try to copy/paste... or if you are not writing this in ubuntu try to write it down letter-by-letter..

welcome, and good luck

PS check the edgy guide in my signature... that will help you much ;)

---

### Post by cajungenes on 2006-11-10
I don't understand why I can't get this. I still have the black screen, after it loads. At least I finally have Linux installed, I just can't use it. 

I did figure out about the spaces, that's how I accessed the file, and I changed the ATI in the line to Radeon. I also went to the Ubuntu Users Guide in your signature, but I'm not sure what I should do now. It didn't seem very clear to me. This is all very new and unfamiliar.

When I restart my computer now, I do have the Grub with options to boot into Linux or Windows, but I still have the same problem with the black screen.

---

### Post by abaddon1215 on 2006-11-10
Sorry, dude, but I couldn't figure out how to specify that you leave spaces between sudo and nano.  All apologies there.

When you say it loads before the screen goes black, do you mean that you see the splash screen where lines appear with system messages like "mounting root filesystem" or the login screen where you have the username box?

And that vesa driver is no good.  I have an ATI x200 card(purchased this my system in May '06) that didn't react well to it.  It forced 800x600 resolution on me, so I replaced it with the fglrx driver.  Mind that I'm not saying that you have to do the same.

---

### Post by cajungenes on 2006-11-10
hey, don't apoligize, I'm the dummy here. :) but, eventually I will learn this. 

When I say it loads, I mean I get the ubuntu splash screen and it ticks off each item it is loading, then types ok on each line, and then on to the next line. When it has gone through all the things it is loading, the screen then goes black, and I can't get it back.  If I hit escape, I get a linux login screen, and when I login in, it signs off and shuts down. 

I sure do appreciate you hanging in there with me on this. :)

---

### Post by Velotix on 2006-11-10
Your problems are all contingent on one file: xorg.conf, which is the one you've been trying to edit. Specifically, your problem is that X is trying to  run the wrong driver for your card.

This will probably sound very, VERY annoying, but you may have to keep rebooting X and trying out each separate driver in turn until you find the right one.

The command:

```
sudo dpkg-reconfigure xserver-xorg
```

will, as you've been told already, open up the menu system for optimising your video card. It also gives you the option to change the driver you're using. Vesa is the general default driver for this, and obviously Vesa doesn't work on your system. Interestingly, X defaulted to the "nv" driver for me from the very first startup - for future reference, nVidia cards work much, MUCH better with Linux as nVidia actively develop drivers for it.

When you get to the first screen in the menu, CHANGE the driver (press the up or down arrows) until you find the "ati" driver. Press Enter and from there follow the instructions to try and get your display sorted out.

Once you actually get into Ubuntu, if your display still isn't how you want it, change the screen resolution either through Ubuntu or by doing it manually and editting xorg.conf (which I had to do myself today in fact!). Keep a backup of xorg handy just in case you screw up your settings and set them to something unusable.

Also, just in case you have the same problem I had: for some reason xorg.conf also stores the settings for which keyboard layout you use, so if you ever need to change them, you'll find them in there. When I manually rebooted X the first time it reset my keyboard layout, so I had the US map for a couple of days before finally sorting it out by accident.

Linux is funny sometimes. :D

---

### Post by abaddon1215 on 2006-11-10
-BEAT ME TO IT!-

On the login screen, make sure that the session type is a gnome session.  Other than that...I'm perplexed.

.....unless you've got an LCD monitor.  In that case, you may have to specify some settings in your xorg.conf that we talked about earlier.  I'm unclear about the settings because I use an old CRT monitor that doesn't require it.  I think these are Hsync and Vsync but I really don't know.

If you want to change video drivers to the fglrx driver and you have a working internet connection, type this on the command line:

sudo apt-get install xorg-driver-fglrx

After this is accomplished then type:

sudo nano /etc/X11/xorg.conf

On the line that says driver:vesa or driver="vesa", delete vesa and insert the word fglrx between the quote marks.  Then save it and restart the machine or log out.

Minus the LCD-specific stuff I mentioned above, that should get rid of the video driver issue.  Also make sure there are no strange screen resolutions listed, or weird refresh rates, and note whether your monitor is listed in the file.

---

### Post by cajungenes on 2006-11-11
I can't tell you all how much I appreciate the way you're hanging in with me on this! I do have an LCD monitor -- the Norwood Micro 17" Flat Panel TFT/LCD Widescreen -- so that could be a major part of my issues.

I'll be going through all the suggestions I've gotten and will update you on my success. Cross your fingers for me! :-?

---

### Post by cajungenes on 2006-11-11
OMG!! It worked..I'm now at the login in splash screen for ubuntu. 

I just have one small problem. It wants a login and password. I don't remember assigning these. I have no clue what they might be. I've tried numerous combinations. Can you believe this?  So what now? can I edit it out? Do I have to re-install? Can I get around the login and password. 

I still can't believe I actually managed to figure out getting it installed (with lots of help) and now I can't get into the program! ARG!!

Oh well, I am making progress. :)

---

### Post by Ecthelion on 2006-11-11
When you start working in command line, you usually are in your home dir
I get, for example, this:

**ecthelion**@ElvenHome:~$

My username is ecthelion, and my computername is ElvenHome.

So my login name is ecthelion too...

And your password...

That should be the password you have to fill in when using sudo...

So you probably do know both since you had to do, for example, this:
> sudo nano /etc/X11/xorg.conf
 

:-)

---

### Post by cajungenes on 2006-11-11
I give up. I have tried every possible combination of anything I might have used as a login or password. I didn't need a login to get into the linux or recovery startup section, it's listed with Windows as a choice when my computer loads.

I only need a login and password for getting into ubuntu and apparently at some point I gave it one, and now it wants me to type in the one I gave it. Only I don't remember what it was.

So I'm just going to delete it all and re-install it again.  At least I think I know how to do it this time.

Thanks for the help

---

### Post by cajungenes on 2006-11-11
Ok everybody, I'm typing this in Ubuntu! I just installed a second copy, not sure how to get rid of the first one that I can't get into.  I wrote the login and password down on this one.  

So now I'm going to start learning what the heck I've been doing with all of your help. :)  Hopefully I can get the hated "windoze" off my computer soon.

Thanks again to ALL of you....

No more Black screen!!:-D :-D :-D :-D :-D

---

### Post by abaddon1215 on 2006-11-11
Glad you got it going and welcome to Ubuntu!  

To get rid of the first copy of Ubuntu, just re-format it's partition to ext3 using the program GParted (Gnome Partition Editor).  Be careful on this because that data will be gone forever..  That should overwrite it.  If you want to use it for storage, check on either mounting that partition(best) or enlarging your current Ubuntu partion(which I definitely DO NOT recommend).

---

