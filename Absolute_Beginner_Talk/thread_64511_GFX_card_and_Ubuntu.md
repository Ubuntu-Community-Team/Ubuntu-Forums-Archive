---
title: "GFX card and Ubuntu"
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by h0tpants on 2005-09-11
I have a GeForce 5500 I didnt have it installed when i installed Ubuntu.  i then installed the card and drivers on winxp (i have a dualboot).  When i try to boot up Ubuntu it freezes on "Starting hotplug subsystem". Not sure what i should do about this.  gracias

---

### Post by davmac on 2005-09-11
I've not had the problem myself but if I was in your position, I'd take the card out, get my system booting up correctly and then install the nVidia stuff (sudo apt-get nvidia-glx nvidia-settings) and then put the card back in.

Hope this helps,

Dave Mac

---

### Post by tseliot on 2005-09-11
Turn on the computer and when you see the word "Grub" keep in pressing ESC.

Select Recovery mode from the list

after it boots to the command line type:

dpkg-reconfigure xserver-xorg

it will ask you several things(if you don't know the answer just press Enter):

Tell it to autodetect the card and then select "nv".

It will ask you (I don't remember when) you desired resolutions:

select the one you need and press the spacebar to enable it (press Enter when you've finished)

When it comes to the refresh rate question select "advanced" and put the values of your monitor (horizontal and vertical refresh) if you know them, [COLOR=Red]otherwise[/COLOR] select the easiest and recommended mode.

[COLOR=Red]REMEMBER: when you don't know the answer to its questions just press ENTER (and the recommended answer will be chosen)
[/COLOR]
Then restart your computer. The computer will work now. Of course you will have to uninstall the nvidia drivers and to reinstall them.

---

### Post by h0tpants on 2005-09-11
so i uninstalled the nvidia drivers (but left the gfx card in)  and rebooted to the grub recovery mode.  it started going through the process but then came up with: [4294689.812000]  <0>Kernel panic - not syncing:Fatal exception in interrupt, at which point i restarted into windowsXP.  anything else i should try? thanks.

---

### Post by tseliot on 2005-09-11
This is weird. However if your computer doesn't boot in normal mode (i.e. not in recovery mode) and you have kernel panic you might have to reinstall the system from scratch.

---

### Post by h0tpants on 2005-09-11
okay, i did reinstall ubuntu and then followed the ubuntuguide.org step to install nvidia drivers and then restarted and everything booted up okay. then i installed the gfx card itself (but left my moniter plugged into default) and booted up just fine. then i plugged my moniter into my gfx card and tried booting up and nothing comes up on the moniter (not the GRUB booter or anything).  so i tried plugging moniter back into default and tried your ubuntu recovery mode again but got another error message after restarting.  grrrrr...

---

### Post by tseliot on 2005-09-12
Why didn't you install Ubuntu with your gfx card in?

---

### Post by h0tpants on 2005-09-12
well, i tried that a couple times and ubuntu wouldnt finish installing.  i'll try that again.

---

### Post by h0tpants on 2005-09-12
So here is what i've done so far:

1. booted into bios setup and switched Primary Vid. Adapter to "pci"
2. booted from ubuntu cd (setup partition)
3. install ubuntu, unmount & eject cd
4. reboot to finish install but freezes on "starting hotplug subsystem"

then i tried (inbetween a&b i reinstalled falling above steps):

A. 1. Rebooting into ubuntu recovery
    2. trying your dpkg-reconfigure xserver-xorg advice but it came up saying the xserver-xorg was not installed

B. 1. (after step 4)reboot into bios and change Pri. Vid. Adapt. back to "onboard"
    2. Finished ubuntu install (no "hotplug" freezing)
    3. Logged in and followed ubuntuguide.org's nvidia driver install process (seemed to work)
    4. reboot to bios and changed Pri. Vid. Adapt. to "pci"
    5. boot up ubuntu only to get a frozen "starting hotplug subsystem" message

i still have no idea how to fix this, gonna keep trying though.

---

### Post by tseliot on 2005-09-12
try (in recovery mode)

nano /etc/X11/xorg.conf

Then find the section Device and make sure the word I put in red is “vesa”:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver [COLOR=Red]"nv"[/COLOR]
BusID "PCI:1:0:0"

CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

restart your computer and select the graphic card you want to use in your bios

Let's see if it works

---

### Post by h0tpants on 2005-09-12
one question, does it matter which PCI slot the gfx card is actually in for the 
BusID  "PCI:1:0:0" step?

ps. thanx again for the help, i'd be killing people right now otherwise!

---

### Post by tseliot on 2005-09-12
[QUOTE=h0tpants]one question, does it matter which PCI slot the gfx card is actually in for the 
BusID  "PCI:1:0:0" step?

ps. thanx again for the help, i'd be killing people right now otherwise![/QUOTE]
if you want to make sure you use the right slot:
repeat the whole "dpkg-reconfigure xserver-xorg" thing again BUT when it asks you which graphic driver you want to use, SELECT "vesa" instead of "nv". restart your computer and see if it works.

---

### Post by h0tpants on 2005-09-12
nope, same thing as before...freezes at "starting hotplug subsystem".

---

### Post by tseliot on 2005-09-12
It's weird, I'm running Ubuntu with my Geforce 5500.

1) What's your motherboard model?

2) does Ubuntu work properly if you boot using the integrated graphic card?

---

### Post by h0tpants on 2005-09-12
i have no idea what mb model i have. yes, right now i'm running ubuntu on my integrated card.  i got some instructions from nvidia.com so i'm gonna try those and see what happens.

oh yeah, the instructions were saying something about disableing the x server and resetting the run level, would you happen to know how to do that??

---

### Post by tseliot on 2005-09-12
[QUOTE=h0tpants]i have no idea what mb model i have. yes, right now i'm running ubuntu on my integrated card.  i got some instructions from nvidia.com so i'm gonna try those and see what happens.

oh yeah, the instructions were saying something about disableing the x server and resetting the run level, would you happen to know how to do that??[/QUOTE]
I know what you mean. No, we do things differently in Ubuntu.

BUT

I've written a guide (for newbies) about how to install the latest nvidia drivers (it has worked for many people until now)

[http://www.ubuntuforums.org/showthread.php?t=57368](http://www.ubuntuforums.org/showthread.php?t=57368)

If you have any questions about the guide, please post them there.

---

