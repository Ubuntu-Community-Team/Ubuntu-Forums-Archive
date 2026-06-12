---
title: "[SOLVED] Inspiron 9300 Gutsy"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by farueulogy on 2007-10-18
Basically I tried to install the RC1 release a week-ish ago and though the live cd worked fine (I turned off effects as you can't do restricted drivers on a live cd) **but** the installed version never ran:

I would switch on, get past grub and have a black screen.

Now this may be a CD error or it may be something that's now fixed. My questions are:
[I]
How do you do a M5 checksum or whatever it's called? (I'm so 1337)

Has anyone successfully installed 7.10 on an dell inspiron 9300? (ATI radeon graphics card)

          -If so how are the effects after installing the restricted driver?[/I]

---

### Post by Daveth on 2007-10-18
3rd option down on the first picture, here

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by farueulogy on 2007-10-18
> **Daveth said:**
> 3rd option down on the first picture, here

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Cool, thanks - now - has anyone managed to install on a dell inspiron 9300?

---

### Post by jda1701 on 2007-10-21
My Inspiron has a few quirks with Gutsy, but the install went without a hitch. 

Inspiron 9300
Pentium M 750 (1.86GHz)
1GB OCZ DDR2-553 Memory
60GB 7200 Hard Drive
nVidia GeForce Go 6800 256MB
WUXGA+ 1920x1200 LCD Screen

The quirks I am having I believe are kernel-based.  acpi-cpufreq does not properly scale the CPU frequency and ALSA seems to think "Master Mono" controls the subwoofer while "Master" controls the other two speakers.  I'll post links to the two posts I make about these issues.

---

### Post by farueulogy on 2008-03-28
So I worked all this out. From a blank install of the final release 7.10.

Install 7.10 as per the onscreen instructions - turning off the effects as soon as posible.

On first boot be patient. It is apparently a problem with the splash screen. When at your desktop turn off the effects for now.

Terminal:
sudo gedit /boot/grub/menu.lst

replace all instances of "splash" with "nosplash"

Install the restricted drivers from the graphics card (system>administration>restricted drivers manager). Restart your computer.

Typed in terminal:  sudo gedit /etc/X11/xorg.conf
then edit:
> Section "Extensions" 
	Option		"Composite"	"0" 
EndSection

edit to:
> Section "Extensions" 
	Option		"Composite"	"1" 
EndSection

Typed in terminal:  sudo apt-get install xserver-xgl

Restart your computer. Turn effects back on.

To install EMERALD
Synaptic: installed "emerald" and "libemeraldengine0"

Ran emerald via 
alt-F2: > emerald --replace

Added themes called "Beryl emerald themes" of gnomelook

Refreshed emerald via 
alt-F2: emerald --replace

To install "custom" effects

system>administration>synaptic package manager
installed "compizconfig-settings-manager"
"advanced desktop effects settings" added to system>preferences

---

