---
title: "Sound problems, I think I'm narrowing them down..."
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by CaptOwski on 2007-11-28
Apparently this no sound issue must be pretty common. I have read about them over a number of message boards. I've tried alot of different terminal commands, but no good.

**lspci** gives me this:

```
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 18)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 9100 IGP
02:08.0 Ethernet controller: 3Com Corporation 3Com 3C920B-EMB-WNM Integrated Fast Ethernet Controller (rev 40)
eric@eric-desktop:~$ 


```


Something I noticed when I run **gstreamer-properties**, a multimedia systems selector pops up and in the terminal :

```
W: main.c: WARNING: called SUID root, but not in group 'pulse-rt'.
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
W: main.c: WARNING: called SUID root, but not in group 'pulse-rt'.


```


Now so far my situation has been that the only program I can run sound is in Totem with Windows Media files and the default CD player. Sometimes my usb speakers will pop and crackle. No system sounds except the onboard beep. No dice for Amarok or any of the other media  players. And **of course** no sound for flash. And it seems most chatrooms that run flash do not run at all when I visit them. If anyone could just give me some tips or just wants to see what I get after a terminal command. No sound can be kind of irritating especially with most content out there.

---

### Post by CaptOwski on 2007-12-06
Still nothing. I can play CDs and windows media files through totem. No flash or system sounds. Installed Pulse audio. Installed esound. :mad:

---

