---
title: "Real Player - Sound issue"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Octaine on 2008-04-07
I've installed Real Player and video is fine, but no audio.

Hmm, any suggestions?

---

### Post by riven0 on 2008-04-07
I'm getting this solution from somebody else's thread:

1. Open the terminal

Install alsa-oss: 

2. sudo apt-get install alsa-oss

3. Now do what is mentioned in this thread to make the changes permanent: [No sound in Realplayer 10]("http://ubuntuforums.org/showpost.php?p=1626534&postcount=6")

---

### Post by Crafty Kisses on 2008-04-07
You may also want to post the following output:
```
lspci
```

---

### Post by Octaine on 2008-04-07
I can't save the file to make it permanent, assuming it would work after doing this as it didn't work after installing alsa-oss.

lspci:
> 00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

---

### Post by riven0 on 2008-04-07
> **Octaine said:**
> I can't save the file to make it permanent, assuming it would work after doing this as it didn't work after installing alsa-oss.



Probably because your not using sudo. Try opening the file through the terminal using: **gksudo /usr/lib/realplay-10.0.8/realplay** then make the changes, restart Realplayer and save.

---

### Post by Octaine on 2008-04-07
Still nothing. :(

Just noticed it's version 10.0.9.

---

