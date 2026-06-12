---
title: "cannot record through audacity"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by niteblind on 2008-04-09
Hi All,

Can anyone assist me with this? I am using a brand new macbook running Gutsy 7.10 with both the KDE and Gnome desktop installed  and I want to record the sound from a video I have so that I can listen to it walking to work on my MP3 player.

I have loaded the video in Movie player and all is fine with the playback of sound and video I have no issues there at all. When I click the record option in audacity it goes through the motions of recording but there are no spikes etc to show there is actually any sound be picked up.

I have checked the setting and originally it was set t use /dev/dsp as this did not work I tried to change this to ALSA HDA Intel ALC882 (Analog and Digital are there an I have tried both) still no joy.

Is there something obvious I am doing wrong. As I understand it I am simply trying to record the output from the sound card but something is going wrong here.

niteblind

---

### Post by Crafty Kisses on 2008-04-09
That's really odd, sorry for your troubles. Is there anyway you can post the following output?
```
lspci
```
Thanks.

---

### Post by kpkeerthi on 2008-04-09
Open a terminal and type **alsamixer**. Check if the mixer channel for your mike is muted or has volume level at zero.

---

### Post by niteblind on 2008-04-09
as requested here is the output of lspci. I have also checked alsamixer. All the record levels apart from master were at zero. So i cranked them all up to about 75% and tried again still nothing being recorded.



a00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
04:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

Any other ideas at all?

niteblind

---

### Post by niteblind on 2008-04-11
bump :D

---

### Post by niteblind on 2008-04-12
bump :D

---

### Post by skralljt on 2008-04-13
in alsamixer, up at the top you will notice it says "Playback" and "Capture".  If you hit the tab key you can select between them.  Go to Capture and then use the direction arrows to go to the mic or whatever source you want to record from.  Then, when it is highlighted, hit the spacebar to select it as the recording source.  
That probably won't work, at least it isn't for me with a soundblaster live platinum.  Also you may have to select which mic you are recording from if your soundcard has many bells and whistles.

---

### Post by causticburning on 2008-04-14
I had a similar issue (now solved, thanks skralljt) where I had sound coming through the speakers but no ability to record.  I have a soundcard which alsa seems to think is an 882 but it's meant to be an 889A (any help?)

Following your advice opened a terminal and ran: alsamixer

I started in the [Playback] menu
Earlier, I was fooled into thinking this screen only had 8 sliders; but there's > indicators to the right of the screen if you can go further right and it will scroll across.

I went across to the first capture source.  On my card it has sliders when scrolled to the the far right (from left to right):
LFE - Side - Line - Mic - IEC958 - Input So -  Input So  - Input So

I scrolled across to the first Input So to make it <Input So> and pressed up and it selected Line as my input source instead of Mic.

Next I went back to audacity and selected edit-> preferences
In this box i went to recording and from the "Device:" drop down menu I selected "ALSA: HDA Intel: ALC882 Analog (hw 0,0)"

I pressed OK, and hit record - and did a few of these ones:guitar:
Sound recorded perfectly.
Hope this helps you.

---

