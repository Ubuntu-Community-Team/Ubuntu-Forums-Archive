---
title: "sound not working"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by slade on 2005-11-21
I have a Dell Optiplex GX150, which i got for free when a college gave it away, and i decided to install ubuntu on it.  a few days later my other computer, a 4+ year old Dell, died on me.  so i moved my video card, sound card and extra ram to the computer with ubuntu.  I just got the video card working today, but the sound card is still not working.  i can hear sound through the integrated sound, but of course that sounds horrible for anything besides tones.  if i go to system>preferences>sound, i can choose from "Intel 82801BA-ICH2", which is the integrated sound, or "SBLive! Value [CT4780]", which i take it is the sound card i installed.  If i change "Intel..." to "SBLive..." the sound no longer works at all.

in the terminal, if i enter "lspci" i get:

0000:00:00.0 Host bridge: Intel Corp. 82815 815 Chipset Host Bridge and Memory C ontroller Hub (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82815 815 Chipset AGP Bridge (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 11)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 11)
0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 11)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 11)
0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 11)
0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 11)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (r ev 11)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200 ] (rev a3)
0000:02:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07 )
0000:02:07.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev  07)
0000:02:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev  78)

does anyone know what i have to do to get the sound working?

---

### Post by apjone on 2005-11-21
Go
System > Preferance's > SOund 
and just change your default sound card

Then change the settings in 
System > Preferance's > multimedia System selector

---

### Post by slade on 2005-11-21
[QUOTE=apjone]Go
System > Preferance's > SOund 
and just change your default sound card

Then change the settings in 
System > Preferance's > multimedia System selector[/QUOTE]
[QUOTE=slade]if i go to system>preferences>sound, i can choose from "Intel 82801BA-ICH2", which is the integrated sound, or "SBLive! Value [CT4780]", which i take it is the sound card i installed.  If i change "Intel..." to "SBLive..." the sound no longer works at all.[/QUOTE]
thanks for trying to help, but...  i already tried that.

---

### Post by slade on 2005-11-22
^
^^
^^^
^^^^
^^
^^
^^
^^
^^

anyone?

---

### Post by phanboy_iv on 2005-11-22
Try disabling the "System sounds" option in System->Preferences->Sound and see if that works.

---

### Post by slade on 2005-11-22
[QUOTE=phanboy_iv]Try disabling the "System sounds" option in System->Preferences->Sound and see if that works.[/QUOTE]
thanks, but that didnt work.  i dont think ubuntu is fully recognizing the video card, even though it showed up under system>preferences>sound.

---

