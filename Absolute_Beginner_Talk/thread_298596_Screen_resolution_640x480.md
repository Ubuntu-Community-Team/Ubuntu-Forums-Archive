---
title: "Screen resolution 640x480"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by DapperMe17 on 2006-11-13
After a fresh installation of Dapper 6.06, I notice only one screen resolution listed in the preference control panel. I would like to add 1024, or at least 800x600. 

Would I need to update the driver? 

HP CRT monitor with AGP Nvidia Riva TNT Vanta soundcard. 

Thanks

---

### Post by confused57 on 2006-11-13
You might want to read how to reconfigure the xserver:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

Basically, what you'd do is open a terminal(Applications---Accessories---Terminal), enter:
```
sudo dpkg-reconfigure xserver-xorg
```

You might want to select "No" at the first screen for automatically detecting your monitor, then select the defaults for everything else, except select the "nv" or "vesa" video driver...and place an (*) by the resolutions that you want to use.  The link above explains all of this.

---

### Post by DapperMe17 on 2006-11-16
Thanks for the reply.

When I boot, my screen is off-center to the right as well. Is this something that can be fixed as you have described, or could it be a faulty video card/monitor?

Thanks for your patience.

---

### Post by ciscosurfer on 2006-11-16
Some monitors have an "Auto/Select" button or something to that effect that will automatically adjust the screen to fit perfectly and will get rid of the off-center effect that's occuring for you.

---

### Post by DapperMe17 on 2006-11-16
Monitor is a...HP Pavilion Monitor -  M70, 17-Inch (D5259A) Display/Monitor(VGA/CRT) circa 1998-99.

Video card....AGP, 8 MB Nvidia Riva TNT Vanta

Wonder if the video card is supported or faulty?

The monitor does have an monitor control panel on the front of the monitor, although I haven't found an "auto" adjust in sight, outside of the manual tweaks, where ironically I can adjust the whole screen horizontally & vertically, move vertically, but cannot move the screen horizontally left or right, or squeeze the middle. It does have an "auto-deguesser," which flickers the screen, but does not auto-correct the picture to the monitor size.

---

### Post by Bachstelze on 2006-11-16
If I were you, I'd have a try at the nvidia-legacy drivers, search the Wiki for it :)

---

### Post by morglum82 on 2006-11-16
Hey all,

 I have the same issue than DapperMe17.  Only 640*480 is listed under the preferences.  I am using a 15" Viewsonic VG150 LCD with an old Geforce MX200.  

I tried the following:

```
sudo dpkg-reconfigure xserver-xorg
```

And the computer is already supposed to accept 1024*xxx.  I rebooted but to no avail.  Then I tried to modify

```
sudo nano /etc/X11/xorg.conf
```

And I can see that, at my default depth, my resolution has 3 modes, including '1024*xxx'.

I also tried installing the nvidia drivers.  However, it tell me that I appear to be running a X server and that I must quit it.  How do I do that?

Thanks!

---

### Post by LLRNR on 2006-11-16
To those who have problems with screen resolutions and owe old nVidia graphic cards:
-----------------------------------------------------------------------------

This is sort of my case too, I have a nVidia card of 64 MB (GeForce MX 4000 AGP 8x). So, let's try it the "classic" way (it just worked out for me) :

**STEP 1**
```
sudo apt-get install resapplet
``` and then type ```
resapplet &
``` in the terminal / konsole, and you'll se on your panel / taskbar a little square, we'll that's the resolution switcher applet. Try and see if it's of any use.

**STEP 2**
I think the resolution switcher applet will be rather useless at this point. So it's time to grab the standard nVidia drivers:
```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable
```

**STEP 3**
This is also rather pointless, but who knows, you might get lucky: restart X server by pressing Ctrl+Alt+Backspace

**STEP 4**
Check out for visible improvements. If this isn't the case, you should be able to see "Resolution Switcher" in Applications -> Accessories -> Resolution Switcher (in Gnome) or in K Menu -> Utilities -> Resolution Switcher (in KDE). This is the "resapplet" you just installed. Anyway, if you can't locate it, run "resapplet &" again in the terminal and try to switch resolutions... If, after you restarted X, you didn't get BEFORE the login screen the nVidia logo, then proceed to

**STEP 5**
Time to manually edit xorg.conf file. First, let's do a backup:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
If, by chance, after a while you won't be able to login... ahem... in a graphical way, then don't panic, at the "login:" prompt type in your username, at the "Password:" prompt type in your password and then 
```
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
``` and restart the computer.

Ok. So let's edit the file:
```
sudo nano /etc/X11/xorg.conf
``` (Well I just happen to like nano... if you want, you can try vim :lol:)

This basically opens the file in R/W mode. You'll see a lot of sections called in certain ways:

Section "SectionName"
  ..................
  ..................
EndSection

You have to scroll down until you find **Section "Device"**. Good. In this section you'll see a few lines, including a certain one, that should look like this:
```
Driver     "nv"
```
You have to change this line to make it look like the following:
```
Driver     "nvidia"
```
Then save the file, exit and restart X (Ctrl+Alt+Backspace). (If you're using nano, then Ctrl+O, Enter, Ctrl+X)

That's it, after you login you should be able to switch to the desired resolution and refresh rate. 

I hope this was useful for you too, anyway it worked for me.

Cheers, 

LLRNR

PS - Worst case scenario: You'll have to try
```
sudo dpkg-reconfigure xserver-xorg
``` :D

---

### Post by DapperMe17 on 2006-11-17
So...it appears I'm in luck?!?!

Thanks so much for your info, i'll have to try that process.

ps...sweet munk'ish picture fellow metalist (Ronnie J Dio/Viv Campbell era) fan myself.

---

### Post by Bachstelze on 2006-11-17
He'll need *nvidia-glx-legacy* instead of *nvidia-glx*.

---

### Post by LLRNR on 2006-11-17
@HymnToLife: Whoops! You're right, forgot to mention that: nvidia-glx-legacy instead of nvidia-glx, of course, you're perfectly right.

@DapperMe17: Good luck with your problem... fellow metallist ! :D \m/

---

### Post by Bachstelze on 2006-11-17
My avatar is more metal than yours :D

---

### Post by DapperMe17 on 2006-11-19
Just me, back to my PC after a couple of days.

I haven't had time to try your fix, but I will tomorrow. Thank you for your assistance!

I did take note that, in Kubuntu/Xubuntu 6.10, I've noticed that the HP startup screen is a bit off center, but then the Kubuntu/Zubuntu start splash screen appears absolutely correctly at 1024x. But, when the desktop loads, it's back to being off center and way to big for the monitor.

---

### Post by DapperMe17 on 2006-12-01
...an update

I've successfully installed the nvidia-legacy-glx driver & have successfully updated xserver from "nv" to "nvidia".

I now have an extensive list of settings in my display settings & I get the Nvidia splash screen.

Unfortunately, & still troublesome, no matter what display setting I select, the desktop image is still way too large for my monitor screen:neutral: 



Could this be that the line & raster frequencies are still not optimized??? Or could it be something else?



My HP D5259a Pavilion M70 Monitor manual shows line freq at 30-70khz & raster freq at 50-120hz, with dot rate of 110mhz. The max viewable area is 12.8 inches (H) x 9.6 inches (V).


Previous to running Xubuntu Edgy, Windows 98SE was run on this system, with  perfectly fit desktop-to-monitor.

Any ideas??? 

I hope to get this picture figured out. 

Thanks again!

---

### Post by LLRNR on 2006-12-01
> **DapperMe17 said:**
> I've successfully installed the nvidia-legacy-glx driver & have successfully updated xserver from "nv" to "nvidia".

I now have an extensive list of settings in my display settings & I get the Nvidia splash screen.

Unfortunately, & still troublesome, no matter what display setting I select, the desktop image is still way too large for my monitor screen:neutral: 


..."the desktop image is still way too large for my monitor screen" ? :shock:
You mean the wallpaper ? It's strange. Still you can try 3 things:

**1)** Make sure that in your display settings you chose the wallpaper to be *stretched* to fill the whole screen;

**2)** Try to find a wallpaper that matches exactly your current resolution: for instance, if you're using 1280x1024, go to gnome-look.org or kde-look.org and download a wallpaper of exactly 1280x1024 and see if it fits better;

**3)** You might want to try to synchronize the HorizSync and the VertRefresh rates. For this, enter:
```
sudo ddcprobe | grep monitorrange
```
You will get an output similar to *monitorrange: 30-70, 50-120* for instance (well this is MY output, don't use it !), where the first pair of numbers represents the HorizSync value and the second pair stands for the VertRefresh value.

[ If, by chance, you get the message *sudo: ddcprobe: command not found*, then do
```
sudo aptitude install xresprobe
```first. ]

Now backup your xorg.conf file and then open it for editing:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```

and scroll down until you find the "**Monitor**" section, and modify it using the HorizSync and VertRefresh values provided by ddcprobe. Here's an **example** from my xorg.conf file:

```

Section "Monitor"
    Identifier     "MCM 171V"
    Option         "DPMS"
    HorizSync      30-70
    VertRefresh    50-120
EndSection

```

Then save the file (Ctrl+O, Enter), exit nano (Ctrl+X) and restart X server (Ctrl+Alt+Backspace).

LLRNR

---

### Post by DapperMe17 on 2006-12-01
Help please:o 

I edited the xorg file, adding vertical & horizontal rates, restarted. Unfortunately, that brought down my monitor. 

I'm running off a Kubuntu LiveCD at the moment, but when I run terminal to change the settings back, you must not be able to see those changes with a liveCD...?

I get a DOS-looking screen, and it says something to the effect of xorg, or xserverv error...server terminated or stopped. Not all I can see is a black DOS style window, which appears to be just like a terminal window.

Any help?
I'll try to write down the sudo xorg thingie, then try to fix.

---

### Post by DapperMe17 on 2006-12-01
I'm back up...no need to panic:p 

By "desktop", I mean that everything on my screen is way too big for the actual monitor, and center is off horizontally. 

All worked fine prior with Win98SE.

---

### Post by LLRNR on 2006-12-01
Have you tried editing your xorg.conf file (manually) and adding resolutions? It's a way of fixing things anyway... for me it worked, I put the resolution I needed in front of the others.

(I didn't understand your previous post: you mean you broke your X?)

LLRNR

---

### Post by DapperMe17 on 2006-12-01
Yes, broke the bugger...but I've since fixed it.

I now have the Nvidia Legacy GlX drivers installed, and have a wide variety of screen resolutions & refresh rates to choose from (compared to the stock driver).

I have many 1024x & 800x resolutions available, with different refresh rates...but none do the trick. 

I have a seperate thread with the nano (terminal) info & the manufacturer's specs.

I'm optimistic about Xubuntu, but...:-k

---

### Post by LLRNR on 2006-12-01
In your /etc/X11/xorg.conf file, right under **Section "Screen"** you should have a lot of things like this one:
```
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768"
    EndSubSection

```

What I meant was if you tried to manually modify the resolutions here, like I did (I also erased the "800x600" and "640x480" modes since I never use them).

Also, putting those HorizSync and VertRefresh values under your "Monitor" section should have helped, too.

LLRNR

---

### Post by DapperMe17 on 2006-12-01
Yes, I did add those rates like you mentioned, but the server crashed & I had no monitor, except for a black command screen. I had to restore the config file to get back my monitor.


Well, below is a copy of my terminal & the monitor specs. Can you make light of anything?


Thanks very much for your time!



Monitor manual specs...
My HP D5259a Pavilion M70 Monitor manual shows line freq at 30-70khz & raster freq at 50-120hz, with dot rate of 110mhz. The max viewable area is 12.8 inches (H) x 9.6 inches (V).



Terminal...
Section "Device"
Identifier "NVIDIA Corporation NV6 [Vanta/Vanta LT]"
Driver "nvidia"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "HWP"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV6 [Vanta/Vanta LT]"
Monitor "HWP"
DefaultDepth 24
SubSection "Display"
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection

---

### Post by LLRNR on 2006-12-01
> **DapperMe17 said:**
> 
Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV6 [Vanta/Vanta LT]"
Monitor "HWP"
DefaultDepth 24
[COLOR="Red"]SubSection "Display"[/COLOR]
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection

You're sure that's the exact output...?? If so, the red line seems a little off-topic to me, so to speak; try to erase it, save the file and Ctrl+Alt+Backspace.

LLRNR

---

### Post by DapperMe17 on 2006-12-01
I'm sorry, that was a duplicate...in other words, there is only one there, not two ( I copied & pasted to this thread with that erroneous duplicate). There is only one in the config file! Disregard the line you have in red.

---

### Post by LLRNR on 2006-12-01
Puzzled ; I can't think of anything else :( I ran out of ideas, I guess :D

However, I can't give you an exact "recipe", when I first got my x-res thing up I did a lot of experiments myself... still I can't advise others to do that, since it was my personal computer and I didn't have any important data on it, anyway.

Sorry I can't be of more help.

LLRNR

---

### Post by DapperMe17 on 2006-12-01
It's an older CRT 17inch monitor. 

I wonder if it could be that the video card and/or monitor are too old to be recognized correctly in Xubuntu? Maybe the video card is defective?

Have you heard of other Linux distros that are more user-friendly with this issue?

Because I've just fresh-installed this thing...I don't have anything important on the PC.


In my other thread named "Desktop image way too large for monitor", someone recommended another method, which is greek to me. Would you know about it?

Thanks

---

### Post by DapperMe17 on 2006-12-02
Do you think adding a modeline to the config file might work. If so, could I get some help with it, based on my spec info listed above?

When i added the vertical & horizontal refresh rates, that is what caused x to crash. Maybe I entered the info incorrectly...? Do I need to stop x prior to the changes? If so, what is that command?

If someone could review my specs listed above & offer me a modeline & the correct lines to add to x under monitor, it would be appreciated:mrgreen: 

Thanks

---

