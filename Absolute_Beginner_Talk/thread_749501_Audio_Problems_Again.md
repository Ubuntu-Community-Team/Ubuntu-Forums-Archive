---
title: "Audio Problems Again"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Mesenja on 2008-04-08
[SIZE="3"] [FONT="Palatino Linotype"] 

I woke up this morning my sound was dead. It worked last night with no problems. I have an Soundblaster Audigy 2 soundcard which I had turned off. I am also running a beta version of Hardy Heron.  The reason for this is that I had audio problems before and  better some sound then none at all. I still have sound when I log in for instance by none when I launch any external sound or video player. The other problem I have is that my  Mozilla Firefozx Beta 5  doesn't play audio

[/FONT].[/SIZE]

---

### Post by buried on 2008-04-09
Run this in terminal
```
alsamixer
```
and turn volumes up, tell me if it works.

---

### Post by Crafty Kisses on 2008-04-09
You may also want to post the following output:
```
lspci
```

---

### Post by Mesenja on 2008-04-09
[FONT="Verdana"][SIZE="3"]

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
02:00.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
[/SIZE][/FONT]

[FONT="Verdana"][SIZE="3"]I can play now play video and sound within Thunderbird and Firefox although there is a  synchronization problem between the video and audio.[/SIZE][/FONT]

---

### Post by Mesenja on 2008-04-09
[SIZE="3"][FONT="Verdana"] That is the good news. It appears however  that it only works on certain Gnome audio or video players. Another slight problem is that I have no sound in embeded video on sites like Google Video . Is there any way that I can save the  settings  permanently?   Is there also a way that I can get my VLC player to work? Thanks for all the help  .[/FONT][/SIZE]

---

### Post by Mesenja on 2008-04-11
> **Mesenja said:**
> [SIZE="3"][FONT="Verdana"] That is the good news. It appears however  that it only works on certain Gnome audio or video players. Another slight problem is that I have no sound in embeded video on sites like Google Video . Is there any way that I can save the  settings  permanently?   Is there also a way that I can get my VLC player to work? Thanks for all the help  .[/FONT][/SIZE]

[FONT="Palatino Linotype"][SIZE="3"]The sound still does not work in Firefox. However I do not know how or why but I can now view and hear audio and video files in any player. I will check around and this forum and see if I can solve my remaining problem.[/SIZE][/FONT]

---

### Post by herbster on 2008-04-11
```
speaker-test -c2 -twav -Ddefault
```

What do you hear? Hit CTRL+C to end the test.

Also, do you have an ~/.asoundrc file? If so, paste the contents.

---

### Post by Mesenja on 2008-04-12
[SIZE="3"]> **herbster said:**
> ```
speaker-test -c2 -twav -Ddefault
```

What do you hear? Hit CTRL+C to end the test.

Also, do you have an ~/.asoundrc file? If so, paste the contents.

I hear a womans voice saying "front left" and then "front right" in each of the individual speakers.. I did a search for ~/.asoundrc file but came up empty. This has nothing to do with my sound problem but I will bring it up here anyway. How do you list all of the changes that you have done in the about:config file. I want to reverse my last change to default. [/SIZE]

---

