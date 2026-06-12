---
title: "Low resolution projector on macbook 5,5"
date: 2009-10-09
forum: Apple Hardware Users
---

### Post by julio33 on 2009-10-09
Hello, i have a macbook pro 5,5 and i use the nvidia driver and jaunty, however when i connect a projector it only shows 640x480 on it, i read on this guide:

[https://help.ubuntu.com/community/MacBookPro5-5/Jaunty](https://help.ubuntu.com/community/MacBookPro5-5/Jaunty)

That i have only to add this line:

Option     "NoEDID" "True"to /etc/X11/xorg.conf 

Well i add that line in many different places and it not only don't works, but sometimes it show me only colored vertical lines in the screen so i have to enter as recovery mode and remove it to access my X windows :)

Also i try with:

nvidia-xconfig --no-use-edid

But it only makes my x windows to show the colored vertical lines

If you have any idea of this please help me, i'm trying many things but maybe you can give a clue.

Thanks,
Julio

---

### Post by Niels den Otter on 2009-10-09
This can be a real pain (at least it is for me on a 5,1 macbook). 

First you could check if it works when you restart your X session with the beamer connected. If the beamer sends EDID information it very likely works.

I have tried a lot of specific Nvidia driver settings, but none works optimal. If I use Ignore... settings in the end some beamers work, but some are completely out-of-sync.

What I have done to get it working with our office beamers is to read the EDID information from the beamer (startup connected and use the nvidia-settings app to read and save the edid.bin file) and then to fool the driver at startup that such a beamer is connected;

---------------------------------
Section "Device"
    ...
    Option "NoLogo" "True"
    Option "CustomEDID" "DFP-2:/etc/X11/edid.bin"
EndSection

Section "Screen"
    ...
    Option         "ConnectedMonitor" "DFP-0, DFP-2"
    Option         "TwinView" "True"
    Option         "ModeValidation" "DFP-2: NoDFPNativeResolutionCheck, NoDisplayPortBandwidthCheck"
-----------------------------------

However now it doesn't read EDID information when something else is connected... It would be great to be able to load EDID information from the nvidia-settings tool when things fail and otherwise to use the information received.

I hope that you find a nice solution to this. Please let me know ;-)


-- Niels

---

### Post by crocowhile on 2009-10-10
> **julio33 said:**
> Hello, i have a macbook pro 5,5 and i use the nvidia driver and jaunty, however when i connect a projector it only shows 640x480 on it

The NoEDID thing used to work. In the last weeks doesn't work any more and for this reason I ****** up a couple of job interviews (my job interviews require projections). It was the first time in my life I thought maybe I should not rely on linux for serious business.

---

### Post by gotgenes on 2010-05-07
Has this been fixed in Lucid 10.04?

---

### Post by buntuLo on 2010-05-08
i had very much pain too, MBP5.1 here, karmic koala.
i realised that every time the beamer is hanging from the ceiling, thus an extension vga-cable is used, the nvidia driver cannot not read edid infos. it appears that many extension cables have less pins that that the beamer's connector has. instead i never had any trouble using small portable beamers directly connected with their cable to the laptop.

---

### Post by nmilyaev on 2010-05-27
I guess we need to report this issue as a bug..

---

### Post by beaufils on 2011-09-14
Did anyone filed a bug (same problem in 11.04 on MacBookPro6,2) ?

---

