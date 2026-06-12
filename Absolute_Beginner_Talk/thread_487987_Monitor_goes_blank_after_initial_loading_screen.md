---
title: "Monitor goes blank after initial loading screen"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by footwo on 2007-06-29
OK so I'm new to Linux but not new to computer hardware. I recently built a new machine and got an LG L226WTQ 22" Widescreen LCD Monitor to go with it.

I downloaded Ubuntu 7.04 and burnt it off. Booted from the CD rom and I get the menu offering to install / run in safe graphics mode.

I choose install and i get an Ubuntu logo and a loading bar that fills up. Then as soon as the bar is filled my monitor goes into power saving mode and turns off. I can hear music so i assume that the install program runs successfully but I can't see anything :(

Can anyone offer me advice on how to fix this?

(It boots into Ubuntu from the disc if I choose safe graphics mode but I want to install it!)

---

### Post by loserboy on 2007-06-29
if it works in safe graphics mode just do it that way, you can still install in safe mode, in fact it looks the exact same except you are using a generic video driver.

out of curiosity though, what video card do you have?

---

### Post by footwo on 2007-06-29
I dont get an option to install in safe mode only run Ubuntu in safe graphics mode.

It loads into the actual OS so I dont get a chance to install it.

Im on an nVidia 8800 GTS card

---

### Post by loserboy on 2007-06-29
there's probably some workarounds for getting the 8800s to work, I would just search around for that.

but what do you mean it just loads the actual OS? if you are able to boot into the livecd and see the desktop then theres an icon on the left that says "install"

---

### Post by footwo on 2007-06-29
Yes indeed! I just found it and installed :) I'm on it right now.

Even managed to get my wireless USB adaptor working with my router.

Thanks for pointing that out to me :)

Now is there anyway to use the proper resolution for my monitor (1680x1050)?

I'm currently stuck at 1024x768 on widescreen.

---

### Post by logos34 on 2007-06-29
Did you install the nvidia-glx graphics driver?

---

### Post by footwo on 2007-06-29
no i dont know how to do that

---

### Post by logos34 on 2007-06-29
Try method 1 on this link:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

---

### Post by footwo on 2007-06-29
ok i get to the step where i do this:

ross@zim:~$ sudo apt-get install nvidia-glx-new

and i get this message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-new has no installation candidate

---

### Post by logos34 on 2007-06-29
then try 'nvidia-glx'. That should work fine. If you must have bleeding edge, then go to nvidia website and get the latest 'NVIDIA-Linux-XXXX.run' driver.

---

### Post by footwo on 2007-06-29
I get the same message using nvidia-glx.

I've downloaded the .run file from nvidias website, how do I use it?

---

### Post by logos34 on 2007-06-29
method 2 (on the same link).

Basically your going to drop to the console, turn off gnome display manager, cd over the dir where you downloaded the .run file, and 'sudo sh NVDIA-Linux-x86-xxxxx.run'.  It starts an interactive installer.  But you need to read method 2 to make sure you have the required depencies (gcc, build-essential, linux-restricted-<uname-r>, etc, etc)

---

### Post by footwo on 2007-06-29
When I press CTRL-ALT-F1 to goto the command line my monitor switches off again, just like it did originally when I was trying to install :(

---

### Post by logos34 on 2007-06-29
Did you enable all the repositories in Synaptic and download all the updates?  What kernel are running?

---

### Post by footwo on 2007-06-29
OK I just downloaded around 72 updates from ubuntu's autoupdate and I used Envy to install the nvidia drivers. They installed and I can access a control panel that allows me to switch to the 1680x1050 resolution.

When I do this it changes to the correct resolution but sets its self uncentered on the horizontal axis about 3 inches from the left of the screen. When I press the autoset button on my monitor it jiggles the display around and lines it up (correctly) for a few seconds but then switches right back to being off centre.

Its infuriating I keep getting things so far then hitting another problem!

---

### Post by logos34 on 2007-06-29
Did you run

sudo nvidia-glx-config enable

?

Try reboot.

No experience with widescreen, so I'm not sure what to suggest other than get the documentation for you monitor specs and run the interactive X server config.  But you'll have to do it from the console.  If you have the same problem as before then restart in recovery mode.  

**sudo dpkg-reconfigure xserver-xorg**

The only thing I could find was this (but its oriented towards intel--see bottom):

[https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28widescreen%29](https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28widescreen%29)

good luck

---

### Post by footwo on 2007-06-30
Thanks again for your replies :)

I've tried to reconfigure the X server manually as per your instructions and by following that link. Now I have a new problem.

I boot the machine, Ubuntu loads up, I get the graphical logon prompt, so I log in and my desktop shows up.

But.... I cant click anything now. The mouse is there and I can move around but I cant click ANYTHING, not icons on the desktop, not the Applications/System menu, nothing. The only thing I can do is right click on the desktop and that brings up a menu. I'm going to try reconfiguring again I may have done something wrong...

Or have you any idea why its doing that?

---

### Post by sirius11 on 2007-07-01
so basically  we can't run the 8800 video card on ubuntu at 1920x1200 ?  there are no gurus with a widescreen 24 " and a 8800 card here in this forum ?

it would also be nice if someone would post the link to the infos on how to install ubuntu with a 8800 video card, I can't seem to find the informations. except this LONG page about installing a driver : 
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

My monitor also become black when trying to install ubuntu.
yes I am trying to search for informations.

Thinking about it,  if someone need to read such a long page just to be able to install the latest driver for his video card,   he is either bored to death or have a lot of time to loose.

---

### Post by footwo on 2007-07-02
> **sirius11 said:**
> so basically  we can't run the 8800 video card on ubuntu at 1920x1200 ?  there are no gurus with a widescreen 24 " and a 8800 card here in this forum ?

it would also be nice if someone would post the link to the infos on how to install ubuntu with a 8800 video card, I can't seem to find the informations. except this LONG page about installing a driver : 
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

My monitor also become black when trying to install ubuntu.
yes I am trying to search for informations.

Thinking about it,  if someone need to read such a long page just to be able to install the latest driver for his video card,   he is either bored to death or have a lot of time to loose.


I fixed it.

Heres what I did to get Ubuntu working on a 8800 GTS with a 22" LG Flatron widescreen monitor. I am a total linux noob:

[LIST]
[*] boot from the Ubuntu Live Disc.
[*] Dont select Install straight up because more often than not your screen will just got blank after the initial loading screen.
[*] Select to run ubuntu in safe graphics mode - THIS SHOULD BOOT UBUNTU FROM THE CD AND YOU SHOULD BE ABLE TO SEE THINGS! If it doesn't then you can stop reading here because I have no advice for you.
[*] Once Ubuntu is up and running choose to Install it from the Install icon on the desktop
[*] You might want to setup your partitions in windows using partition magic or whatever, it can be a bit confusing doing it in linux
[*] Once Ubuntu is installed you should now be able to boot it and see the desktop in 1024x768 res. Your main priority now is getting your network card working so you can get on the net, get updates and download other stuff that you need. For me this was the tricky bit since I use a Zyxel USB Wireless adapter to connect to my router and support for USB adapters is rather dodgy at the moment. If you need help setting up internet access on a USB wireless adapter then let me know.
[*] OK once you're online download and install every single possible update for ubuntu, make sure all package respositories are turned on. Once the update is done (there were 72 for me) reboot.
[*] After the reboot you will be fully updated, now its time to get [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"). Choose the version that corresponds to your version of Ubuntu (I'm on Feisty). Download and run that script, it should create a link to Envy in your *Applications >> System tools* menu. Run it from the link and it will get the nvidia drivers, install them and configure them for you. However there will probably be some tweaking to do.
[*] You should now have the correct nVidia drivers installed and a way to access the control panel, again in *Applications >> System tools* there will be a link to nvidia settings, so open it.
[*] Here you can change the resolution, refresh rate, the normal stuff you can do with videocards. However the problem I was having was that I couldn't save the changes to make ubuntu always use these settings. The settings for your X windows server is stored in /etc/X11/xorg.conf and this is what the nvidia settings window will write to. It contains all the settings your GFX card and monitor uses. The nvidia settings can detect these and try to write to the file but because you are not logged on as root you cannot make changes to the file.

[*] So we sudo to get access to the file ```
sudo gedit /etc/X11/xorg.conf 
``` this will open the editor with the xorg.conf as root file and allow you to make changes. What you are looking for is the section called 'Monitor'

```
Section "Monitor"
     Identifier         "FLATRON 995F"
     Option             "DPMS"
     HorizSync          30-96
     VertRefresh        50-160
EndSection
```

this needs to be changed to reflect your personal settings. Most people will have Generic Monitor for the identifier, so all you need to change is the HorizSync and VertRefresh variables. These can be found in your monitor manual. You will also see a section entitled 'Display':

```
SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
```

you can just add a mode in there, for example my monitors native resolution is 1680*1050 so I added that mode in:

```
Modes           "1680x1050" "1024x768" "800x600" "640x480"
```

[/list]

There are most likely huge gaps in this guide so if you have any other questions let me know but currently I am running Ubuntu with the latest kernel on an nVidia 8800 GTS at 1680x1050 res. It looks lovely and I even tried playing WoW on it (tip, if you play WoW stick to windows, framerate is noticably worse even on a powerful machine ^^)

---

### Post by sirius11 on 2007-07-04
Thanks a lot,  GREAT guide. 
 I was missing was the : Install from the desktop trick.
And your explanation about how to configure the video card is very clear.. 
Much better than those confusing 2 pages threads.
I will certainly have more questions, but at least I can start learning.
:KS:popcorn:

I have a 1920x1200 res   24"monitor   , I'll see if I can get it up to that resolution...  I am not expecting to play some games with Ubuntu , I'll have enough just to learn those sudo and command things for a while,  this will be a type of a game by itself   :)  I still have Vista to play the latest games,  that is about all Vista can do well = gaming..

---

### Post by sirius11 on 2007-07-11
that did not work, when i finish installing ubuntu, the screen goes to black upon first boot, I've tried many things with command prompts  but nothing seem to work...   I do not know how to install a driver from  a dvd at a command prompt . So basically,  no ubuntu for me I guess.

the problem seem to be the screen size...  but very strange that I can install ubuntu in 1900x1200 and not boot with the same resolution.

is there a way to boot in a way that the image will show on the monitor  even at any resolution so that I can update everything ?

---

