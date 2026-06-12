---
title: "MacBook2,1, Internal Microphone does not show-up"
date: 2010-10-16
forum: Apple Hardware Users
---

### Post by book on 2010-10-16
On my white MacBook2,1 , the Internal Audio Analog Stereo device does work, and, in the "Sound Preferences", it 
shows up on the Output Tab. 

The MacBook2,1 has an internal microphone. In the "Sound Preferences", however, no device shows up on the Input Tab where it tells to "Choose a device for sound input", neither can I check or uncheck the Mute checkbox, nor can I slide the volume control bar. In sum, the internal Mic does not yet work. I need the Microphone for Skype etc.  

Sound was said to work out-of-the-box already in Karmic Koala, but it didn't. Somewhere, I was then recommended to update to Lucid Lynx, which I did. 

On the page [https://help.ubuntu.com/community/MacBook2-1/Lucid/](https://help.ubuntu.com/community/MacBook2-1/Lucid/)  it is, again, promised that the Sound will work out-of-the-box. It still doesn't.

What shall I do? Boot Mac OSX, or get the Mic working? Here is what I have done sofar:

I have updated the ALSA Driver so that now I have:

[INDENT] Advanced Linux Sound Architecture Driver Version 1.0.23.
 Compiled on Oct 14 2010 for kernel 2.6.32-25-generic (SMP).
[/INDENT]
Also, I installed Alsa Mixer, which I believe should have been there from the start, but it was not.

And, I have a line in **/etc/modprobe.d/alsa-base.conf **,  which says:

[INDENT]options snd-hda-intel power_save=10 power_save_controller=N model=intel-mac-auto
[/INDENT]


Here is the list I get with the command lspci:

[INDENT]00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)[/INDENT]

---

### Post by book on 2010-10-19
Following a hint from ZeroLinux <http://ubuntuforums.org/showthread.php?t=1439009>, I installed PulseAudio Device Chooser, packages paman and padevchooser

Results:

**paman** starts, lets me choose devices, and change their properties. Unfortunately, only the output device of my macbook shows up. 

**padevchooser** does not start. It gives this error message:  (padevchooser:2481): WARNING **: pa_browser_new() failed. :(

---

