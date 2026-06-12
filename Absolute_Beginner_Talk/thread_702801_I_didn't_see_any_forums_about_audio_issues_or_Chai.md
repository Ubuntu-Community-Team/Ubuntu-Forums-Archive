---
title: "I didn't see any forums about audio issues or Chaintech cards"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by doondoon on 2008-02-20
I don't know why I don't have sound all of a sudden. Chaintech av-710, I don't know if the card quit working or something in the OS changed. Where and what do I look for in the shell, or how do I check my sound card?I'm running Gutsy...er its still running me. I'm having a ball with it.

00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:08.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0e.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GS] (rev a2)
Will this help you help me?

---

### Post by gimfred on 2008-02-25
I had a problem like this, and the problem was I (or an inadvertent program)  had changed the channel that was selected, and muted the main channel (PCM on my system). Can you check that?

Try this [search]("http://ubuntuforums.org/search.php?searchid=36895471")

and to filter your logs for the relevant info try using grep

Here is something that as been prepared earlier...

> if you type 'lspci' into the terminal, what comes up? We can filter some of the data by asking only for information that concerns ethernet using the 'grep' command after 'lspci'. We need to connect the two commands via a "pipe" '|' ( My "pipe" is the shifted backslash '\' key i.e. 'shift + \' = '|', it isn't lower-case L nor J nor upper-case i nor numeral 1. It looks like two vertical dashes similar to the colon, ':')

Thus the command is:
Code:

```
~$ lspci | grep ethernet
~$
~$ lspci | grep Ethernet
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
05:05.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
```

As you can see the first time I searched for ethernet it didn't find anything so it filtered out everything. So before you run grep on a term run the first command without any filter to be sure you are getting the information you want! If you want to know more specialised commands for grep, you can type 'man grep' into your command line. man <the command you want to know about> will often give you some info about a command.I.e. 'man lspci'. The man pages can get a little cryptic or technical at times.

You would use the command like this:
```
gimfred@zandergraph:~$ lspci | grep audio
gimfred@zandergraph:~$ lspci | grep Audio
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

```

---

### Post by doondoon on 2008-02-26
Thanks gimfred,
Presto123 said I should look you up for questions like the one above and here you are. So, what other similar commands are similar to this or is there a web page or book I can acquire to assist me?Is there a similar command for the AGP or other hardware? I've got it working now thank you for your help.

---

### Post by doondoon on 2008-03-07
My audio quit again and this time it's not the cable vs cat.

---

### Post by gimfred on 2008-03-26
Hi Doondoon, are you still having this problem? would you mind eliciting it again -- I've been concentrating on other things and seem to be having trouble understanding what the problem is exactly.

---

### Post by doondoon on 2008-04-08
Sorry it took me so long to get back to you here's the result of the last command :
bill@bill-desktop:~$ lspci | grep audio
00:0e.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
I'm not sure where to go from here,but I'm not sure this is the right audio card. Maybe one of them are.

---

### Post by stmiller on 2008-04-08
^ Those two devices listed are first the PCI audio card, and next the onboard sound. Make sure you are turning up the volume/unmuting the PCI one, and not messing with the onboard sound with the mixer program.

---

### Post by doondoon on 2008-04-11
Is this done in SYSTEM>PREFERENCES>SOUNDS? If so I have checked there. After playing a dvd movie and having sound, I am wondering if it is a problem with the flash player? How does the "--fix --missing" script or command work? Or a better question is how would I type it, " <FLASHPLAYER> --FIX" OR "<FLASHPLAYER> --missing"?

---

