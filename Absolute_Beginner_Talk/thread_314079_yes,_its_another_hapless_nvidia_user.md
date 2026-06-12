---
title: "yes, its another hapless nvidia user"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-12-07
Hello...
I am desperate. I have an nvidia Geforce MX 4000. It worked great until yesterday when some unknown gremlin screwed it up. I switched to my onboard video and all is well until I try to run Blender. So, I need my nvidia card up and running...

I ran these commands so far:
----------------------------------------------------
sudo apt-get install nvidia-glx-nvidia-kernel-common

sudo nvidia-glx-config enable

sudo dpkg-reconfigure xserver-xorg
----------------------------------------------------
nvidia-glx is already up to date.
nvidia-glx-config had some dependency issues that I couldn't nail down
configuring xserver resulted in "no nvidia GPU found" 


I even tried manually editing the xorg.conf, but to no avail. I will try loading vesa graphicsvand using automatix2 for configuration.

Anyone think of anything else???

---

### Post by pay on 2006-12-07
Did you compile your own kernel?

---

### Post by saintj0n on 2006-12-07
I loaded Ubuntu off an iso dvd which I downloaded from the net. I may have upgraded the kernel along the way. As far as compiling it, I didn't load it into an IDE or anything, so I am not sure. Maybe I ran apt-get install <kernel upgrade module>?? In any case, I haven't done anything like that since yesterday morning when the nvidia card was working okay. Would it help if I go from Dapper to Edgy? I do not know how to do it though??

---

### Post by pay on 2006-12-07
It's hard to know how to fix it without knowing what the gremlin did. Could you post your xorg.conf? ```
gedit /etc/X11/xorg.conf
```If your not sure whether you compilled a kernel or not then thats a no. An upgrade to edgy probably won't do anything but if you want to try you need to change your sources.list to an edgy sources.list then ```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by saintj0n on 2006-12-07
Section "Monitor"
Identifier "Monitor0"
VendorName "unknown"
ModelName "unknown"
#Option "DPMS" "true"
HorizSync 30.0 - 75.0 # Warning: This may fry old Monitors
VertRefresh 59.0 - 61.0 # Very conservative. May flicker.

EndSection

Section "Device"
Identifier "Card0"
Driver "nv"
BoardName "unknown"

#BusID "PCI::10:0"

Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
DefaultColorDepth 16

SubSection "Display"
Depth 8
Modes "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "10240x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "640x480"
EndSubSection
SubSection "Display"
Depth 32
Modes "640x480"
EndSubSection

Section "Screen"
Identifier "ATIScreen"
Device "Card0"
Monitor "ATIMonitor"
DefaultColorDepth 24

SubSection "Display"
Depth 8
Modes "1024" "800x600" "640x480"
EndSubSection
EndSection

SubSection "Display"
Depth 15
Modes "1024" "800x600" "640x480"
EndSubSection
EndSection

SubSection "Display"
Depth 16
Modes "1024" "800x600" "640x480"
EndSubSection
EndSection

SubSection "Display"
Depth 16
Modes "1024" "800x600" "640x480"
EndSubSection
EndSection

SubSection "Display"
Depth 24
Modes "1024" "800x600" "640x480"
EndSubSection
EndSection

Section "serverLayout"
   Identifier "Default Layout"
   Screen "NVIDIAScreen"
   Input Device "Generic Keyboard"
   Input Device "Configured Mouse"
   Input Device  "stylus" "SendCoreEvents"
   Input Device  "cursor" "SendCoreEvents"
   Input Device  "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection

---

### Post by pay on 2006-12-07
it shouldn't be talking about ati if you have an nvidia card like here
Section "Screen"
Identifier "ATIScreen"
Device "Card0"
Monitor "ATIMonitor"
DefaultColorDepth 24

and this bit ```
Section "Device"
Identifier "Card0"
Driver "nv"
BoardName "unknown"
```should be like this```
Section "Device"
Identifier "Card0"
Driver "nvdia"
BoardName "unknown"
```it seems like Ubuntu has had some trouble detecting your hardware

This time edit the file as root, but back it up first```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by K.Mandla on 2006-12-07
Did you try using the nvidia-glx-legacy driver instead? Your card should run under nvidia-glx, but I occasionally find the legacy driver to work better with some older cards (my GeForce4 440 Go is one).

---

### Post by saintj0n on 2006-12-08
I will try that. My current video card is an nvidia Geforce MX 4000. I think it is about 4 years old. I don't know if that qualifies as 'legacy' though..

---

### Post by saintj0n on 2006-12-08
I have just installed nvidia-glx-legacy and it removed nvidia-glx from my system. I ran dpkg-reconfigure-xorg-conf (I think that was what I typed) and reconfigured X. I then rebooted the PC for good measure and it said the GDM was aborted and dropped back to the command line after a couple of dialog boxes that show /var/log/Xorg.0.log........

I tried configuring it to use vesa this time as well. No luck.
I tried startx -depth16.     No luck.

I'm stumped.....
:confused:

---

### Post by saintj0n on 2006-12-14
Just in case anyone stumbles across this thread...
I figured out the problem. I ran automatix and restarted, same problem. I noticed an error about "couldn't find nv". Hmm...sounds familiar, eh? I then went into xorg.conf under the Device heading and replaced the line: "driver     nvidia" with "driver     nv".

From that point, I rebooted and everything came up fine!

---

