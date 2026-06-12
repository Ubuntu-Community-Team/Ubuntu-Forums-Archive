---
title: "No Sound"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by andy_6590 on 2007-08-09
I have just recently installed Ubuntu onto my desktop. When I try to play videos and and music the media plays but no sound comes out of my speakers. I have tried using headphones and plugging them into my actual tower but still I get no sound. I think its my sound card not being read properly. I went into device manager and the only audio component I could see was this.  

IXP SB400 AC'97 Audio Controller.

The speaker icon in the top left of the task bar has a red X next to it and when I double click I get an error message which says:

"No volume control GStreamer plugins and/or devices found"

I have installed some GStreamer plugins to allow me to play MP3 and other file extensions but even without these I thought I would get sound from websites such as Youtube, but I don't. 

Can anyone help me on this situation, help is much appreciated. Thank you.

---

### Post by splintercellguy on 2007-08-09
Can you post the output of lspci?

---

### Post by andy_6590 on 2007-08-09
"Can you post the output of lspci?"

Sorry I'm not very good with Linux at the moment or computers. If you tell me where I can find this information I will post it immediately.

Thank you.

---

### Post by splintercellguy on 2007-08-09
My apologies. Go to Applications -> Accessories -> Terminal. Then type lspci then Enter. Select all the text the command outputted, then copy into a new post. Thank you :).

---

### Post by andy_6590 on 2007-08-09
I typed it in and got this information.

andrew@andrew-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
andrew@andrew-desktop:~$ 

Hope this helps. Thank you.

---

### Post by splintercellguy on 2007-08-09
This thread might help: [http://ubuntuforums.org/showthread.php?t=365342](http://ubuntuforums.org/showthread.php?t=365342) Post here if you have any questions.

---

### Post by andy_6590 on 2007-08-09
I followed these instructions.

"(1) Double-click the speaker icon in Ubuntu's system tray and click Edit -> Preferences in the Volume Control window that appears. In the list, look for the Master Surround entry, and put a checkbox in it. Then look for External Amplifier and put a check in it. Click the Close button then click the Switches tab in the Volume Control window. Remove the check against External Amplifier.
(2) Then click the Playback tab and click the Speaker icon beneath the Master Surround slider, so that it's no longer muted. Then adjust the slider. Playback some audio and you should find everything now works. Basically, the Master Surround slider is now your volume slider. Weird, but true. To make the system tray applet use the Master Surround to control the volume, right-click the system tray speaker icon, select Preferences, and select Master Surround in the list. "

But I went into System> Preferences> Sound, because it wouldn't let me double click like in the instructions. I got a window open with 3 Tabs Devices, Sounds and System beep. I can't find the Master Surround entry. but all the playbacks are set to Autodetect and the sound capture is ALSA - Advanced Linux Sound Architecture. I tried to test them but it just closed the window and did nothing. 

Thanks.

---

### Post by Dr Small on 2007-08-09
Has your system been without sound the entire time, or did your sound just up and leave?

---

### Post by andy_6590 on 2007-08-09
I have always had sound, you see I only put Ubuntu on my computer yesterday. I have duel booted it with Windows XP Media Center Edition. My sound works fine in Windows but for some reason Ubuntu isn't picking up my sound card. 

Thanks again.

---

