---
title: "Sound just spotted working"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-10-06
I don't know why but my sound just stopped working, when i go to system->preferences->sound and hit any of the test it just closes that window.  How can i debug this?

---

### Post by Lord Illidan on 2007-10-06
Apart from the irony that the title and the content of the post are evidently opposite to each other...

What is the make of your soundcard? Try typing lspci in a terminal, and copy/paste the output here. Also, did you upgrade anything?

---

### Post by GavinZac on 2007-10-06
protip: try restarting X

ctrl+alt+backspace

(save your work first)

---

### Post by RyanZec on 2007-10-06
here it is:

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
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7600 GS (rev a2)
02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS

ctrl-alt-backspace did nothing

PS: if a mod or admin could change my title that would be great.

---

### Post by Pumalite on 2007-10-06
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by RyanZec on 2007-10-06
sudo apt-get install linux-headers-`uname -r`

i don't get what that means, I don't know which linux-headers to install, how do i find this out?

---

### Post by Pumalite on 2007-10-06
At the Terminal, input the command (it's best to copy and paste, especially for a newbie)

---

### Post by RyanZec on 2007-10-06
/proc/asound/card0/codec

This does not exist after doing the first part before the reboot, the asound folder does not exist, anyone know whay?

---

### Post by RyanZec on 2007-10-06
it would be nice if i could get this working without re install but if i can't find an answer in the next few hour that is what i will just do.  I am right now just playing about with ubuntu, testing out programs, themes, Virtual Machines, Desktop Interfaces, etc... until my new laptop gets here.

---

### Post by Dawnmist on 2007-11-02
Just managed to get ALSA sound working on my partner's machine - which has the same:
> Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
device.

It appeared that the 'default' ALSA sound card had not been set.

To determine if this is the case for you:
```
$> asoundconf list
Names of available sound cards:
ICH5
$> asoundconf is-active
$>
```
If the 'is-active' shows no cards active, then the default hasn't been set.

To fix it:
```
asoundconf set-default-card ICH5
```

This creates a file /home/<username>/.asoundrc.asoundconf that will now specify the ICH5 card as the default ALSA sound card, instead of trying the non-existant 'default' card.

Tools like alsamixer should now work, and ALSA sounds should work properly :)

---

### Post by BeardlessForeigner on 2007-11-02
My sound also stopped working last night. I installed Gutsy a week ago and everything was fine. Not to mention I have been using Feisty since April. And all of a sudden sound stopped working. So I will try the various fixes, but if other ppl who had sound are losing it this is definitely a problem. The only changes I made that I can think of was installing gpodder.

edit:
I have a Thinkpad t43p and here is my lspci:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
04:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
04:02.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

---

### Post by BeardlessForeigner on 2007-11-05
My problem turned out to be that PCM was muted in volume control. I'm guessing since it was so simple I just muted it somehow and forgot >_<

---

