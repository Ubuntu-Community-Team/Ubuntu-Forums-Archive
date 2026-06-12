---
title: "ATI driver install comes to a dead end"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-11-20
Hello linux users....

I am hoping to get some assistance on my ATI video card I am trying to install. Let me fill ya in on the 411 and see if you can figure out what I'm doing wrong....

First I typed:
sudo apt-get update

sudo apt-get install build-essential module-assistant\ fakeroot dh-make debconf libstdc++5 gcc-3.3-base

Then:
sudo apt-get install xorg-driver-fglrx

---Everything was cool. Up to this point...
Lastly, I typed:
sudo chmod +x ati-driver-installer*.run
--At this point, the computer gave me its equivalent of "File not found"

So, I tried find ati-driver*..
nothing found.

What do I need to do....?   :-k ?

---

### Post by junglepeanut on 2006-11-20
You might want to point us to what you are following because what I see looks like parts of three different installers...the ati proprietary binary, the open source fglrx and the open source ati.

---

### Post by saintj0n on 2006-11-20
Well initially I had a standard integrated video and that was fine for my needs. However, I recently opened the case to put in a sound card (SBLIVE). So, I added an ATI Radeon card as well and rebooted. I got a bunch of hostile messages from the shell and that's where the boot up sequence came to a halt. No X Windows. I am currently typing commands out of a book, "Ubuntu Unleashed". However, it made it sound like these files should be on there from what I've done so far. I just want to use my Radeon card, the simpler the better.

btw... Getting the sound card to work wont be this hard will it?

---

### Post by ReaderRat on 2006-11-20
**[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)**
**[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Installing_the_driver](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Installing_the_driver)**
[**Radeon Driver Info**](https://help.ubuntu.com/community/RadeonDriver)
These may help

---

### Post by saintj0n on 2006-11-20
Hmm.. why mess with ATI when I have an Nvidia card? It seems to me that ATI is a lot of extra work to install... I just put in a Nvidia card and did an "apt-get install nvidia-glx" Then, I ran sudo nvidia-xconfig. Everything looks ok when I checked the xorg-conf. However, I booted up and my monitor started clicking and popping. The  monitor then stated that it was out of the frequency range (102.6 was the freq. What is a safe frequency to use and do I need to run anything else. I think there is a utility to test safe frequencies isn't there?:mad:

---

### Post by saintj0n on 2006-12-04
I just downloaded the NVIDIA drivers for my card and decided to restart in recovery mode and install it. I got some weird errors about an SDK that it couldn't find and it continued on. Then I typed startx and the screen went black and I'm pretty sure the frequency was off. So I adjusted that and I got the message: No default screen was found. Here is what I put into xorg.conf...

Section "Device"
        Identifier   "NVIDIA Video Card"
        Driver       "nvidia"
        Bus ID       "PCI:0:5:0"
EndSection

Section "Screen"
        Identifier  "NVIDIA Video Card"
        Device      "NVIDIA Video Card"
        Monitor     "RIC"
        DefaultDepth 24
        SubSection "Display"
             Depth 1
             MODES     "1024x768" "800x600" "640x480"

My question is this..How do I know what the Bus ID is and why didn't everything go back the way it was when I copied the backup into xorg.conf? My PC is down and will not go into X at all. How do I fix this?](*,)

---

