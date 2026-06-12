---
title: "Gusty Fglrx"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by kob0724 on 2007-10-27
Well guys, I was all excited the other day when I heard about the new FGLRX drivers supporting AIGLX and thought I'd fire up Ubuntu (I hadn't used it in a month) and try installing Compiz-Fusion. See, I have a Radeon X1600XT and it only works with the Fglrx drives. I went to make sure I was fully updated and decided before I got Compiz-Fusion all working I should probably upgrade to Gusty First. 

This was a mistake.

Before installing gusty I updated my Fglrx drives to the newest version. Then I clicked the upgrade to Gusty button and went through the whole Gusty setup process. When I rebooted everything stuff was a little off. So I tried rebooting again. This was the part where everything went bad.

When I rebooted the second time the Splash screen showed up and then went black. I never saw the log on screen.

I rebooted again and went into safe mode and did: 
sudo dpkg-reconfigure-xserver-xorg
and went through that whole thing and selected fglrx as my graphics driver.

When I started Ubuntu I got the "You're running in low-graphics mode" and I had to go through that whole setup. Even though I selected fglrx again, some how xorg.conf decided to use the ATI driver. This resulted in me never getting the log on screen (I have to log in via command line), and my computer running in a 800x600 res (my monitor supports 1400x900 res).
 
When ever I manually try to switch back to the fglrx driver I just get a black screen after the splash screen. When I try to install the new fglrx drivers (I thought maybe trying to install the new fglrx drivers again would help kick things into gear) I get a "VCDK is missing" error.

So, with that convoluted explanation, is there anyone out there who can help me? I really would like to see Compiz-Fusion work. Thanks in advanced.

---

### Post by kob0724 on 2007-10-28
Well, I did a fresh install of feisty and everything went back to normal. But I've learned something new. This time when I tried to use the restricted drivers (fglrx) everything went fine. This was using the 8.38 fglrx drivers. So I upgraded to the new Drivers. Then the same problem as before started happening. The problem must be with the new Drivers. They must just not play nicely with my graphics card. So right now I'm just using the vesa which is a bummer. 

If anybody else is having issues with getting the new 8.42.3 fglrx drivers to work on their X1600XT and has solved that problem I would greatly appreciate any help. Otherwise I think I'm just going to have to wait until ATI releases some more new drivers and see if those ones work.

---

### Post by smacattack on 2007-10-28
Sounds like the same thing that happened to me before... (I have a Radeon 9800 pro)

I havent tried the new drivers but I had the blackscreen/no login/low graphics problem. I just did a fresh install and it was fine. 

The thing I found triggered my problem was changing my monitor manually, from the 'Plug n Play' that was there by default to my Dell monitor. So maybe if you've changed your monitor setting that could be the reason... if not, sorry I haven't been of much help.

---

### Post by carlosjuero on 2007-10-28
I have an X1650 and experienced much of the same problem you had; What I had to do is completely uninstall the ATI drivers, then follow the[ instructions here]("http://ubuntuforums.org/showthread.php?t=575843&page=3") - after doing that I installed the ATI drivers again, but this time with the GUI (because some links to the libGL driver got broken, the driver itself removed). After that everything showed up fine and I no longer experienced problems with the fglrx ATI drivers.

As a test - what does your fglrxinfo say? If it lists MesaGL.org in the driver information then the drivers didnt 'take'.

---

### Post by kob0724 on 2007-10-28
When I type fglrxinfo into the terminal my screen goes black and all of sudden i back at the log in screen.
When I look in my synaptic package manager is says that the xorg-drivers-fglrx version is 8.34.8

---

### Post by carlosjuero on 2007-10-28
> **kob0724 said:**
> When I type fglrxinfo into the terminal my screen goes black and all of sudden i back at the log in screen.
When I look in my synaptic package manager is says that the xorg-drivers-fglrx version is 8.34.8
It sounds like fglrx wasn't installed properly, or something else odd is happening.

I am pretty new to Gusty & fglrx so my troubleshooting doesn't extend much past what I already posted.

(Question: Are you still on Feisty when you typed the command in? Or did you try reinstalling Gusty?)

---

### Post by kob0724 on 2007-10-28
I'm now on a fully updated version of feisty.

---

### Post by kob0724 on 2007-10-28
I reinstalled the fglrx drivers by doing:

sudo apt-get remove xorg-driver-fglrx

then
sudo apt-get install xorg-driver-fglrx

Now my fglrx drivers are working again and here is what i get when i type fglrxinfo:
blah@blah-desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

So it would appear that the problem is occurring exactly when i try and install the new 8.42 drivers, because the fglrx drivers that you get when you type sudo apt-get install xorg-driver-fglrx are older versions of the fglrx drivers.

---

### Post by carlosjuero on 2007-10-28
> **kob0724 said:**
> I reinstalled the fglrx drivers by doing:

sudo apt-get remove xorg-driver-fglrx

then
sudo apt-get install xorg-driver-fglrx

Now my fglrx drivers are working again and here is what i get when i type fglrxinfo:
blah@blah-desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

So it would appear that the problem is occurring exactly when i try and install the new 8.42 drivers, because the fglrx drivers that you get when you type sudo apt-get install xorg-driver-fglrx are older versions of the fglrx drivers.

Try uninstalling the fglrx, then follow the instructions in the link I put up above - that might help with the problem. The fact that the Mesa information is showing up means that the ATI drivers aren't installing properly (at least thats what I have figured out from when it happened to me).

---

### Post by kob0724 on 2007-10-28
Still nothing. The best I can get when typing in fglrxinfo is 
blah@blah-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


It's like it doesn't recognize the graphics card that i have is a Radeon X1600XT. It just thinks it's some generic card.

---

### Post by strabes on 2007-10-28
You need to completely remove xorg-driver-fglrx and the linux-restricted-modules-<kernel>-generic packages.```
sudo aptitude purge xorg-driver-fglrx linux-restricted-modules-`uname -r`
sudo updatedb && sudo rm -R `locate fglrx`
sudo aptitude update
sudo aptitude install linux-restricted-modules-`uname -r` xorg-driver-fglrx
```

You now need to make sure fglrx isn't disabled:```
gksudo gedit /etc/default/linux-restricted-modules-common
```

On the bottom of that file there will be a line that looks something like this: DISABLED_MODULES="fglrx"

Remove the "fglrx" inside the quotes, making the line look like this: DISABLED_MODULES=""

If it already looks like that, leave it alone.

Now run these commands:```
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```


ATI does not provide correct drivers for their hardware, so you will have to deactivate the composite extension in /etc/X11/xorg.conf , otherwise you will get a jerky video display:```
gksudo gedit /etc/X11/xorg.conf
```

Add the following lines to the bottom:> Section "Extensions"
        Option      "Composite" "disable"
EndSection

Now restart your X server using CTRL+ALT+BACKSPACE.

After you log in, run fglrxinfo and it should look something like this:> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

By the way, I got these instructions from [here](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b). They work on my and everyone else's computer.

---

