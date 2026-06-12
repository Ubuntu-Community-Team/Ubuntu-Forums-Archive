---
title: "I can't hear any sound!  Help me please! (Details inside )"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by Mohdgame on 2007-09-15
Hi everyone, I am having a problem with ubuntu regarding sound. I use logitech USB headset with its own sound card. It was working when i first installed Ubuntu but I had flash plug-in problems and I tried to fix these flash related sound problems, but then it got worse and now the problem has extended to all Ubuntu.

Before I could hear music files and movies, but I can't hear music or sound on Youtube. Now I can't hear BOTH! I have searched the forum and the Internet and I am completely lost. This was my last resort and I hope my problem will be solved.

I'll post everything I did in details. At first, I tried to play with the flash plug-in and reinstalled but I don't think that has anything to do with it. Anyhow, I tried to setup a "Pulse Audio" server which I think screwed the sound up and edited the "Asound.conf".

This is the content of my Asound.conf
> pcm.pulse {
 type pulse
}
ctl.pulse {
 type pulse
}
pcm.!default {
 type pulse
} 
ctl.!default {
 type pulse
}

I also edited Firefoxc file but i don't think it has anything to do with the sound. I downloaded gnome-alsamixer but it didn't worked. It didn't help. 

Where is the problem? How to solve it?

---

### Post by Tecguy2 on 2007-09-15
dp this command in terminal it wont fix it but justdetects usbdevices > lsusb

---

### Post by Crafty Kisses on 2007-09-15
You might want to try posting the following output:
```
lspci
```

---

### Post by Mohdgame on 2007-09-15
> mohammad@mohammad-desktop:~$ lsusb
Bus 005 Device 003: ID 1058:0701 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c041 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 Tablet
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 046d:0a02 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
mohammad@mohammad-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
05:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
05:01.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
05:02.0 Communication controller: Conexant Unknown device 2f30 (rev 01)
05:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
mohammad@mohammad-desktop:~$ 


It does detect the Logitech headset but it doesen't produce any sound, thats what annoys me. It did it before until I played with it.

---

### Post by Tecguy2 on 2007-09-15
boot the linux live cd does sound play in there

---

### Post by Mohdgame on 2007-09-16
> boot the linux live cd does sound play in there

Yes, it dos play sounds.

---

### Post by Mohdgame on 2007-09-16
Bump, someone has a solution or an idea?

---

### Post by kfrance on 2007-09-16
I have had similar problems lately, although I don't have a good answer for why it happens.  I find that running pidgin or other program that use flash sound on my computer will sometimes make me have problems. I just close pidgin and restart firefox.  If things get really bad I restart the computer and things are generally back to normal.

---

### Post by questpro on 2007-09-17
I have experienced the same problem.  I uninstalled the ALSA drivers and reinstalled them. Then   its been solved.
This HOWTO is explained clearly in : [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

It makes you hear the sound, but I guess not in the browser. (I mean like youtube.com) :(

I solved this before. I cannot remember right now. Please post it if you did. I am sure will post, if i do.

---

### Post by burt_57 on 2007-09-17
> **Codename said:**
> You might want to try posting the following output:
```
lspci
```
My problem is that the sound is to low.. even at full capacity !

robert@robert-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:03.0 Mass storage controller: <pci_lookup_name: buffer too small> (rev 13)
01:0a.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
04:00.0 VGA compatible controll

---

