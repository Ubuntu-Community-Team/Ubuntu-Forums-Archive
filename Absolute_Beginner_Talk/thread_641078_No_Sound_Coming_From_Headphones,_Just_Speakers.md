---
title: "No Sound Coming From Headphones, Just Speakers"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Valnorsith on 2007-12-15
Hi, I am trying to figure what is going on with my sound on my Toshiba Laptop.

Sound comes out perfectly fine from the speakers, however when I plug my headphones in, there is no sound from them, just the speakers.

I can't figure out what is causing this and I've tried looking on the forums for the solution with no real luck. Odds are, I'm completely overlooking the thread that has the answer.

Anyways, if someone could help me, I'd really appreciate it. Here is a screen shot of the Volume Control so hopefully it can help the one who tries to help me:

---

### Post by siciliancasanova on 2007-12-15
On board speakers or external?  If it's on board have you first tried a pair of speakers or tried your headphones on another piece of equipment to rule out that it's not the headphones.

---

### Post by Dark_Stang on 2007-12-15
What type of sound card do you have? I had to upgrade alsa to 1.0.15 and edit the file /etc/modprobe.d/alsa-base to get mine working.

---

### Post by Valnorsith on 2007-12-15
They are external headphones, plugged into the front of my laptop, and yes, I have tried multiple ones to make sure it isn't that particular set of headphones.

---

### Post by Valnorsith on 2007-12-15
> **Dark_Stang said:**
> What type of sound card do you have? I had to upgrade alsa to 1.0.15 and edit the file /etc/modprobe.d/alsa-base to get mine working.

I really am not certain. I'm not a major tech person like my friend unfortunately. I don't mess around with this kinda stuff usually and let her help fix it. Unfortunately, she's away for a bit so that's why I'm coming here for help.

Where can I find what type of sound card I currently have? Through a terminal command?

Yes, I am a major noob for the most part as you can easily tell.

---

### Post by Dark_Stang on 2007-12-15
Post the output of lspci

---

### Post by Valnorsith on 2007-12-15
> **Dark_Stang said:**
> Post the output of lspci

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
09:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Dark_Stang on 2007-12-15
[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

Also, I'm not sure if it's included in there, you may have to add this line to /etc/modprobe.d/alsa-base
```
options snd-hda-intel model=laptop
```

---

### Post by chips24 on 2007-12-15
I have the same problem on my HP, but i never really found it important to ask about.

---

### Post by Dark_Stang on 2007-12-15
chips24: To fix your hp click the link in my sig and scroll down to the sound card section. I have the fix posted there for our sound cards.

---

### Post by Valnorsith on 2007-12-15
Thank you for your help.

---

### Post by airbornemist6 on 2007-12-15
sorry for hijacking your  thread, but i tried installing alsa 1.0.15 and all i managed to do was break my sound completely. i followed the instructions exactly, but i guess i screwed up at some point. i followed stag's howto when i first got this laptop and it worked perfect, but i never tried out the sound part, and now i'm wishing i had known more about what i was doing.

---

### Post by Dark_Stang on 2007-12-15
Alsa sometimes resets everything to mute whenever you re-install. Just run alsamixer to check that. If not, just try to install them again.

---

### Post by emotional1 on 2007-12-16
I am using an HP tx1220us (tx-1000) and installed alsa 1.0.15 and got the sound working. the headphones are muted by default and I just opened the volume control preferences at the top right of the desktop(little speaker) and the headphones worked.  Is the DV2000 a touchscreen tablet?  If so did you get it working?

---

