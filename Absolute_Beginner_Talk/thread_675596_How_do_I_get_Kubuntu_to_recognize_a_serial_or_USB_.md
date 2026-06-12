---
title: "How do I get Kubuntu to recognize a serial or USB port?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by fester225 on 2008-01-22
How do I make Kubuntu (7.10) recognize my serial port?
How do I make Kubuntu (7.10) recognize my USB port?
Do I 'install' them?
Do I 'mount' them?

---

### Post by gunksta on 2008-01-23
What exactly are you trying to do? Linux (Kubuntu, Ubuntu, etc.) are quite good at recognizing most hardware. You certainly don't need to mount them. Mounting is what we have to do for file-systems. 

If you just want to know what Linux is recognizing, go to the terminal (konsole) and type in :

```
lspci
```

and look at the output. If you aren't sure post the output here (cut and paste) and I'm sure someone will help you figure out if it's recognized.

Or, you could just start kinfocenter and look there. I suspect you are trying to connect a printer to your computer. If you are, try to just plug it in and see if Kubuntu can set it up automatically. If not, come back here and we'll see if we can figure it out.

---

### Post by fester225 on 2008-01-24
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

---

### Post by fester225 on 2008-01-24
I'm looking for access to my USB port for my scanner, and for my serial port for my home automation program. Both of these will be run in VMware.

---

### Post by gunksta on 2008-01-25
It looks like your USB port is recognized. I haven't plugged anything in to a serial port in so long that I really don't remember what to look for in the lspci output (sorry) but serial ports and parallel ports are simple and generally supported unless you are using an unusual motherboard or card.

I would plug in the scanner and try to use something like XSane to get it set up. Two websites of interest:

[http://www.sane-project.org/related.html](http://www.sane-project.org/related.html) -- These guys make the software to make scanners work under Linux.

[http://www.xsane.org/](http://www.xsane.org/) -- GUI for GNOME . . I've never used it.

EDIT: I don't have any ideas for your other project.

--andy

---

