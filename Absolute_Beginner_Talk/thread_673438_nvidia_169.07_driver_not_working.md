---
title: "nvidia 169.07 driver not working"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by swp6499 on 2008-01-20
installed new nvidia 169.07 driver for my 8600gts card but it doesnt seem to be working...i was using the nvidia-glx-new driver before this and it worked fine but i am getting a new 8800gt fedex tomorrow and needed the 169.07 driver to run it so i figured i would install it now...but sometimes it boots and says its running in low res mode and i try to configure it but the screen just goes black....then it will load into x if i reboot but without compiz....and also when i open the nvidia xserver gui it says i do not appear to be running the nvidia driver please run nvidia-xconfigure to reconfigure xorg.conf but that doesnt help either....i have a samsung 19" widescreen monitor 1440x900 resolution its a model 940bw...if anyone can help i would really appreciate it......

---

### Post by b0rka7a on 2008-01-20
Install the drivers from Envy and see if they work: [http://albertomilone.com/](http://albertomilone.com/)
The drivers from Restricted Drivers Managed don't work for me, so I use Envy and everything is working nice. I have GF 7300GT

---

### Post by luke16 on 2008-01-21
> **b0rka7a said:**
> Install the drivers from Envy and see if they work: [http://albertomilone.com/](http://albertomilone.com/)
The drivers from Restricted Drivers Managed don't work for me, so I use Envy and everything is working nice. I have GF 7300GT

I was having the same problems with nvidia apparently not configuring my xorg.conf correctly, but envy seems to have fixed that for me. Thanks

---

### Post by AdiLit on 2008-01-21
I seem to have the same problem with my nvidia 7600GT the only thing which helped me was, as mentioned before, installing envy. After installing the drivers provided through envy everything works like a charm even compiz :).

---

### Post by LeAstrale on 2008-01-21
personally i would go for a reinstall of the driver, and do make sure that you have build-essential installed before trying to install the Nvidia driver from their website

---

### Post by CamaroSSMan on 2008-01-21
I bought a NVIDIA 5200 CompUSA brand and put it in a PIII I have that I have installed Ubuntu on. I have set the BIOS for Primary display to be the PCI card (the following happens even when I have OnBoard set to display first.). I can see everything on screen until after the splash screen on boot. Even when starting up off of my latest copy of the Ubuntu DVD yet OnBoard display works fine (except no 3d). It is a Pavilion 7855 and the OnBoard display is an Intel 8210 chip. Any ideas would be appreciated. P.S. Envy didn't fix the issue either even though it installed with success.

Thanks

---

### Post by bobdebouwer on 2008-01-21
I too had the problems described here. I ended up in low res mode for some reason after installing envy. Once I reinstalled the drivers from envy though everything has worked like a charm.

I have a 7600gt pcix card

---

### Post by MadDogX on 2008-01-21
Hi guys!


**_EDIT:_ NEVER MIND. PROBLEM SOLVED BY ENVY!**


I've been having a very similar problem. Been trying to figure it out all day, Searching on Google etc. but no use. Nobody seems to have a definitive answer.

I too installed the new 169.07 drivers and they worked fine at first... until the next day when I booted into Ubuntu and it told me my graphics card could not be detected correctly, forced to run in low-graphics mode etc.

Once logged in I tried to open the NVIDIA settings panel but it said the NVIDIA drivers aren't running and that I should run "nvidia-xconfig" and then restart the X server. Tried this but it didn't work.

Then I reinstalled the NVIDIA drivers and noticed a warning message about /usr/lib/xorg/modules/extensions/libglx.so not being a relevant pointer or something similar (I only wrote down the file name  :mad: ). The drivers still installed OK though and I was able to play. But... after rebooting I got the detection/low-graphics problem again.

Has anyone found a definitive way to solve this? I'm assuming that the drivers themselves are ok and it's either the xorg.conf or some other file that's been written incorrectly, but I'm not sure what or how. Here are my comp details:

[I]Ubuntu Gutsy (7.10) x86
ASUS P5N-E SLi
NVIDIA GeForce 7950GX2 with 169.07 drivers
Intel Core2 Q6600
4x1GB Geil DDR2 800Mhz RAM[/I]

Here's the relevant stuff from xorg.conf:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7950 GX2"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```


I guess I'll have a look at Envy next but I have no idea what that is. :(

I'm quite tech-savvy when it comes to Windows (I work as a programmer and part time web-designer), but I wanted to get into Linux aswell. This is what you get for being "bi-curious" (:)) I guess...


**_Update:_**

Well, Envy turned out to be a godsend. Quick, easy and painless. Shoud have tried it before making this huge post. Sorry.

---

### Post by luke16 on 2008-01-21
It looks like envy is the solve all app of video driver issues. It would be nice if it became a default app for the next ubuntu release.

---

### Post by CamaroSSMan on 2008-01-21
Unfortenetly Envy's program did nothing for me. I still boot up to a blank screen after the splash screen. It is driving me nuts. I can only see what I am doing if I boot with the Onboard as primary and have the monitor cable connected to the onboard. Like MadDog X I am fairly new to Ubuntu but I am a tech for Windows pcs and I am pretty good on Macs as well. Any one else have this problem? Even after Envy? Like MadDog X I am fairly new to Ubuntu but I am a tech for Windows pcs and I am pretty good on Macs as well.

---

### Post by swp6499 on 2008-01-21
problem solved so far...followed a few on envys directions such as removing nvidia-glx-new and commenting out the NV driver....and then reinstalled the 169.07 driver and everything seems to work again....msi 8800gt 512 working like a charm finally....thanks everyone....couldnt have done it without ya

---

### Post by Artemis3 on 2008-01-21
Bootsplash, the image that appears after grub with the ubuntu logo and the filling bar doesn't work with 8800gt, makes the screen go black and/or out of sync. Ignore it and Just wait until X loads. Better if you edit /boot/grub/menu.lst and take out splash from the boot line.

Those of us using nvidia drivers from their web site; beware of ubuntu updates. Be ready to reinstall the drivers if at any point after updates you see glxgears (or any 3d app) crashing your x server.

And yes, 169.07 does work.

---

### Post by CamaroSSMan on 2008-01-22
The boot splash does work for me but no matter how long I leave the system running it just boots to a blank screen. I know its not the resolution set to high either because the monitor doesn't shut off it is just blank. I can press the power button for a second and the system then shuts down on its own without me having to hold the button though. So apparently the system is responding, just not displaying anything.:confused:

---

### Post by msemtd on 2008-01-22
> **CamaroSSMan said:**
> The boot splash does work for me but no matter how long I leave the system running it just boots to a blank screen. 
Is this something to do with having two graphics cards?

---

### Post by CamaroSSMan on 2008-01-23
> **msemtd said:**
> Is this something to do with having two graphics cards?
I don't know but thats what I am guessing. I don't know if it matters but under my display settings the NVIDIA PCI Card is disabled. I have to say, my first experience with Linux hasn't been so great. :(

---

### Post by qhimq on 2008-01-25
i've got a 6150go on a hp tx 1000 and this new driver isn't working for me at all.

i've ran the installation, but ubuntu will not run the 'nvidia' driver.


( NVIDIA-Linux-x86_64-169.07-pkg2.run )

---

### Post by seanreynoldscs on 2008-01-29
I have Nvidia 6600 with 512.

When Install the ubuntu Nvidia new restricted drivers, i have no luck.

When i go to Nvidia and get their updated driver, i get one screen working. 
When I use the Screen And Resolution in ubuntu, i get the Low Resolution error. 
I had alot of trouble getting Compiz and Dual Screens. This is what i did.


Process:
Get new ubuntu 7.10 with updates: DONT INSTALL RESTRICTED DRIVER. 
Go to Nvidia and get their driver and install it.
Install Nvidia Settings through Synaptic Manager. (STAY AWAY FROM [Screen and Resolutions] It breaks the xorg.conf file)
Go to the Nvidia Settings and set Seperate X Screens with xinerama. Reboot (make sure to save the xorg.conf file each time) ( I had to cut and paste it because the Nvidia settings did not elevate when trying to save the xorg.conf file)
Go back to Nvidia Settings and set TwinView and merge the settings.(make sure to save the xorg.conf file each time)

and its all better.

To make it work, i had to get: ```
sudo apt-get install nvidia-settings
```
which uninstalled the restricted nvidia new drivers (if you had them installed).

Using Nvidia settings I was able to get both monitors with good resolution and Compiz using seperate x screens or Using TwinView. BUT I did not want either of those settings. Seperate X Screens wouldnt let me drag a window from one screen to another, and twin view gave me one big cube and when i maximized a window it went to both monitors full screen!

So i found out that if you go to Seperate X Screens and tick xinerama and restart, it sets that flag in your xorg.conf file but disables 3D! Then if you switch settings to Twinview once xinerama was already ticked, you get the 3d with the ability to drag windows from one screen to another, Two separate cubes, and Maximize to one screen only. Exactly what i wanted. 

Im sure there is a better way to do this, Im quite new to linux: but i got it to work, and that was how.

---

