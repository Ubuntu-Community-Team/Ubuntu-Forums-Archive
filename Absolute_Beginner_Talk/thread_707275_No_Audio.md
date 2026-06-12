---
title: "No Audio"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2008-02-25
Ubuntu Gutsy just recently installed.  The audio is not muted and turned on and up in all areas from the speakers to the media player.  I still have no sound, any ideas?

---

### Post by forestpixie on 2008-02-25
quick guess only - I had a digital/analog switch on a creative audigy I had to switch off, dbl clk vol icon see if you've a swtches tab

otherwise not sure I can help, but it might help someone else if you give a bit more information of your soundcard - post your ```
lspci
```

---

### Post by pedro_orange on 2008-02-25
Dude...

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

Sweet.

---

### Post by poordamnedfool on 2008-02-25
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)
02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:0a.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
02:0c.0 Multimedia audio controller: Creative Labs SB Audigy LS

---

### Post by sayakb on 2008-02-25
Goto System -> Preferences -> Sound
From there, for sound playback, select ALSA or your appropriate device.

---

### Post by poordamnedfool on 2008-02-25
ok its fixed now thanks alot for the help.

---

