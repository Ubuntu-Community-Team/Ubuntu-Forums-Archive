---
title: "Is there a way to expand screen resolution?..."
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-05-29
Hi,
I'm on Ubuntu Feisty and I have an ATI Radeon X-1650 graphics card. I've stopped trying to install the accelerated graphics driver for it, since it makes me reboot to a blank screen every time. 

So the accelerated graphics driver sits in the Restricted Drivers manager disabled.   My screen resolution default only goes up to 1024 X 768 and I know my monitor is capable of resolutions up to 
1680 x 1050. 

Is there a way to get the higher resolutions without installing the accelerated graphics driver? The other day a fellow suggested code for a similar (but not the same) card, and my system went screwy as a result.  

I appreciate any help on this, since it would enhance my experience with Ubuntu on my desktop. Ironically, Ubuntu graphics were set just fine on my laptop. 

Many Thanks, Frank

---

### Post by alan34 on 2007-05-29
Try editing your xorg.conf file.

Code

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

sudo gedit /etc/X11/xorg.conf

look for the screen section

then add new resolution to each section

heres mine

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by Brightbelt on 2007-05-29
Thanks, I wish I had seen your answer first. Now my system has crashed !! Refer to thread above titled "Help! Low Screen Resolution"

I came in late in that thread and tried the reconfiguration suggested there. Now My system crashed upon reboot and I get a message saying X Server has failed to load and it shows an error "Microcode bcm43xx"

I'll give my system stats again here: HP Media PC, with AMD Athlon X2 64 2.71 Ghz 4600+ Processor, 2 GB of ram, ATI X1650 radeon video card w/512 mb of ram. My C:\ drive is partitioned for a dual boot with Vista.

I need HELP!!! I need to know what to type to get to a command prompt after my system crashes and what to do from there. Thanks, Frank

---

### Post by DougieFresh4U on 2007-05-29
When you boot up can you get to grub menu? On boot up press ESC key and that should get grub. When grub comes up,read what it says to get command line. i think you press c, not sure but it will specify in grub menu
Good luck:p

---

### Post by alan34 on 2007-05-29
Still down?

Try

ctl alt F1

This should get you a terminal window

then login

sudo /etc/init.d/gdm start                          (kde instead of gdm if kubuntu)




Are you using edgy or feisty?

I used the Envy script to install my video card drivers search on the forums.
You can run it from a terminal created as above.

Best of luck

---

### Post by hashimoto on 2007-05-29
> **Brightbelt said:**
> I need HELP!!! I need to know what to type to get to a command prompt after my system crashes and what to do from there. Thanks, Frank

Frank, do this:

First find out your display's manual and look for the technical details. find out the supported resolutions and the refresh rates (horizontal and vertical). You'll need that data.

Next, boot your computer and when it loads grub, hit esc, then select the alternative which gives you root access (failsafe or something like, I canät recall the exact text). This will boot you to root account in text mode., Don't be afraid of that.

When the PC has booted give the following commands:

```
cd /etc/X11
dpkg-reconfigure xserver-xorg
```

This will start a text based configuration program to set up your graphics card, display, mouse etc. Select the proper alternatives (e.g. for NVidia cards the driver shoudl be nv, for ATI, I don't unfortunately know); the descriptions are relatively self expalnatory. When given possibility, select advanced screen setup. In that part select all the supported resolutions (de- & select with space-bar) and fill in the correct reresh rates when asked. After everything is done do 
```
reboot
``` and you should be done.

---

### Post by Brightbelt on 2007-05-29
Thanks Hashimoto,
I hope that works -- it was doing that monitor reconfiguration that got me in this mess to begin with !!

I do need to look into the manual. Great idea,...Frank

---

### Post by Brightbelt on 2007-05-29
Hashimoto,
I did those command and on the last one, it comes back and says "xserver-org not installed"

Am I screwed here or what???

I've tried every command line in this post and none have worked!!

HELP! I'm open to new ideas... Many Thanks, Frank

---

### Post by alan34 on 2007-05-29
Hi, frank

Have a look at this link. I installed my nvidia driver using this in edgy.
Worked great although for some reason I had to run it twice. If you
look through the forums the script is widely praised. It also supports
ATI cards.


[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Good Luck 
Alan

---

### Post by hashimoto on 2007-05-29
> **Brightbelt said:**
> Hashimoto,
I did those command and on the last one, it comes back and says "xserver-org not installed"


Quite strange. Try installing ubuntu-desktop by doing:
```
apt-get install ubuntu-desktop
```
That should install ubuntu's gnome with all dependencies and if xserver is missing it should be installed at the same time as well.

---

### Post by Brightbelt on 2007-05-29
Hashimoto,
Here's what I got from running 'sudo apt-get install ubuntu-desktop':

Firmware_helper [5277]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/000.03:08.0' with driver '(unknown)'

It said 'done' at some points (it could have been just the dependency tree)  but it also said the latest version of Ubuntu desktop was already installed. 

I'll give this one more round and I'll have to reinstall I guess, so I'm open to maybe one more idea or effort. 
I do appreciate your help a lot.

Many Thanks, Frank

---

### Post by george29 on 2007-05-29
> **Brightbelt said:**
> Hashimoto,
Here's what I got from running 'sudo apt-get install ubuntu-desktop':

Firmware_helper [5277]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/000.03:08.0' with driver '(unknown)'

It said 'done' at some points (it could have been just the dependency tree)  but it also said the latest version of Ubuntu desktop was already installed. 

I'll give this one more round and I'll have to reinstall I guess, so I'm open to maybe one more idea or effort. 
I do appreciate your help a lot.

Many Thanks, Frank

that error is something to do with a broadcom wireless card..

---

### Post by hashimoto on 2007-05-30
> **Brightbelt said:**
> 
Firmware_helper [5277]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/000.03:08.0' with driver '(unknown)'

Sorry for delay, it's been night here so I was asleep...

As george29 says that message has to do with your wireless.

I'm stumbled: your ubuntu-desktop is installed but claims that xserver isn't. Yet, desktop depends on xserver. My guess is that there is an error in your apt-get (actually I don't know if that is possible.., see sig). You could try reinstalling the server. I think this should do it:
```
apt-get --reinstall install xorg
``` 
Then, if needed do the reconfiguration and select vesa driver. That should be safe and functional at least.

If this doesn't help, you will need help from someone more knowledgeable. My skills end here (and guessing has already started).

---

### Post by Brightbelt on 2007-05-30
Hi Hashimoto,
Thanks for your response and follow-up. Glad to say that through your help and several other links & suggestions from another fellow here as well, I got back up early this afternoon (well,....now yesterday afternoon).

This is what I did & it worked. I rebooted and went into recovery mode, then I entered, 'dpkg-reconfigure xserver-xorg'

The text-based graphics reconfiguration wizard came up. And you are right, choosing the 'Vesa' driver was the key. (kind of anti-intuitive since I have an ati card and ati was on the list, but...whatever) Another fellow suggested the Vesa Driver as well and until I chose that driver, the reconfiguation wizard was not going to work. 

Also it was suggested that I look up my monitor's horizontal freq. rate and vertical refresh rate in my monitor's manual, so I could enter them directly into the wizard. And I also went into my dual boot XP and wrote down all the screen resolutions so I could enter them correctly into the wizard as well.

And Finally! It worked; it was very satisfying to learn all of this today. One slight downer was that I didn't get the absolute highest resolution (1600 x 1040), but the next highest (1280 x 1024). This is still a lot better than 1024 x 768, so I'm sticking with it. 

There is a program called Envy, which a fellow suggested would install the accelerated driver for my Ati X1650. And I tried that, and it gave me the highest resolution, but it only worked on my 15 kernel (not on 16) so that kind of weirded me out, so I actually had to do the xserver reconfiguration again !! So it worked twice for me.


Thanks for following up. I really appreciate it,...Frank Bright

---

### Post by hashimoto on 2007-05-30
> **Brightbelt said:**
> ...choosing the 'Vesa' driver was the key. (kind of anti-intuitive since I have an ati card and ati was on the list, but...whatever) 

Frank,

Glad you got it sorted out finally. I was already feeling a bit uneasy and frustrated.

It seems that there are issues with the proprietary drivers & 7.04, both ATI and NVidia. I have a NVidia card and if I try to use the nvidia proprietary driver my xserver also fails. On 6.10. everything was fine and dandy.

---

### Post by Brightbelt on 2007-05-30
FYI, Hashimoto, and in case this interests anyone else, there was a notable exception to all this on my HP dv9030us Pavilion laptop. I was able to go into the Restricted Drivers Manager and enable the advanced Nvidia driver there. I rebooted successfully and it fixed all my resolutions and everything.

I just thought it might be worth sharing a hardware success story after all this! Thanks again, Frank

---

