---
title: "[Xubuntu] Installation stalls at desktop image"
date: 2007-11-18
forum: Apple PPC Users
---

### Post by chromebox on 2007-11-18
I'm trying to install Xubuntu Gutsy on my [[COLOR="Blue"]_G4 dual 1GHz MDD_[/COLOR]]("http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_1.0_dp_mdd.html").

Because I was out of blank CDs I used a blank DVD-R instead to burn the image I downloaded from cdimage.ubuntu.com/xubuntu/ports/releases/7.10/release/xubuntu-7.10-desktop-powerpc.iso

Now, I reboot the computer with the DVD in the drive pressing C and it boots into yaboot. I type "live-nosplash-powerpc" and it loads up to the point where I see what seems like a desktop image. It's a blue image with the cute mouse logo of Xfce. There is nothing else on the screen except the mouse pointer which I can move around. Left or Right-clicking doesn't do anything.

I tried Alt-F2 to bring up the run command so I can type xfdesktop but nothing happens when I type Alt-F2. Only Alt-F4 works and it brings up a box with options like "Restart", "Logout", "Shutdown" etc.

Any ideas?

---

### Post by frog_pilot on 2007-11-18
For your special problem I have no idea. But there are still several issues with the gutsy-ppc-branch. That's why I would recommend you to first give feisty a shot.

I'm on PMG4MDD Dual1,25 with 1,5 GB and Radeon9000pro and running feisty with compiz-fusion very smooth. I have the gnome desktop environment installed.

There is only one issue when the live cd is coming up. The free ati driver is trying to address the vram as on x86 bios. To resolve the problem you have to access your xorg.conf file after the xserver error. Add the line ```
Option "NoInt10" "yes"
``` to the drivers section and restart the xserver and everything will be fine.

---

### Post by chromebox on 2007-11-18
> **frog_pilot said:**
>  Add the line ```
Option "NoInt10" "yes"
``` to the drivers section and restart the xserver and everything will be fine.

Can you be a little more specific?

---

### Post by frog_pilot on 2007-11-18
No problem :) step by step...

If you start with the feisty-desktop-ppc...

1. On the xserver error you will be prompted to read a detailed log of the xserver error. Skip this!

2. Once you entered the command line, execute```
sudo nano /etc/X11/xorg.conf
``` 

3. Now you entered the xorg.conf with writing permissions.

4. Look for a passage similar to the following:> Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"	"false"
EndSection

5. Add the line ```
Option		"NoInt10"	"yes"
``` above> EndSection

6. Save your changes to the file.

7. Manually start the Xserver by executing```
startx
```

Now you will come up to the gnome-desktop.

If you will install ubuntu,  you will have to apply the same procedure to your local install. I hope, this can help you. :KS
It will be the same for Xubuntu...

---

### Post by chromebox on 2007-11-19
Thank you, indeed Feisty works on my G4 MDD when I follow your instructions. I'll stick with Feisty Xubuntu. Thanks again.

---

### Post by chromebox on 2007-11-19
I just wanted to make another note that on my installation this line
```
Option	 "UseFBDev"	"false"
```
was set to this by default
```
Option	 "UseFBDev"	"true"
```
but I changed it to false. Not sure what it does exactly. It works anyway!

---

### Post by frog_pilot on 2007-11-19
It is for activating the Framebuffer-Device. Also don't know the exact technical relations. But it's deactivation increases 3d-speed.

And there is another isssue whitch is bothering me since installation. My sound from the soundcard output is very quiet. I have to turn up my amplifier when I boot into ubuntu to a very high level to hear anything. In OSX the sound is much louder. Did you mention a similar problem?

---

### Post by chromebox on 2007-11-20
The sound is low on my ubuntu too. Too much lower than in OSX.

---

### Post by frog_pilot on 2007-11-20
Okay. Then I can tell you I didn't find a solution for this yet. If you find one, please let me know

btw. don't forget to install the multi-processor kernel-metapackages
```
sudo apt-get install linux-image-powerpc-smp linux-headers-powerpc-smp linux-restricted-modules-powerpc-smp linux-powerpc-smp
```

And I suggest you to take xine-ui, mplayer or ogle DVD Player. These are the only players which support the altivec hardware acceleration.

---

