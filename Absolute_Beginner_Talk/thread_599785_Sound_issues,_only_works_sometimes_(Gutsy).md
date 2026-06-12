---
title: "Sound issues, only works sometimes (Gutsy)"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by gunhippy on 2007-11-01
I'm still relatively new to Ubuntu so I'll try to be as clear as i can, and any replies well, if you can work on the assumption i know NOTHING of what you're really saying that'd be best, because chances are I won't.

If it's relevant, this happened back in Feisty too before i upgraded (via the upgrade button in Add/Remove).

I don't know how relevant any of this stuff is to my problem, but i want to include everything i can so i can get a fix, if there's anything else you need to know wet me know and i'll find it =]

Essentially, my sound sometimes works fine, no problems whatsoever, but sometimes i get nothing, the only sound working being MIDI tracks playing from a Java game I like. The only "fix" i have found, is to reboot, as many times as it takes. Seems like basically every time I boot up there's a 50/50 chance of my sound working/not. (this includes the start-up sound for Ubuntu, you know the bum de dum dum dum noise thing :p)

When sound isn't working, the volume control in my Totem music player is greyed out.

I've gone through checking volumes, everything up to the max and unmuted.

Sound card/speakers are all fully functional, the soundcard is on-board, asus A8N SLI SE, it uses Realtek sound or something or other, not quite sure what it is, the manual doesn't even seem to give it a mention.

right click Preferences gives me two options, "Realtek ALC850 rev 0 (OSS Mixer)" and "NVidia CK804 (Alsa mixer)", the Realtek one being picked by default. I've tried switching between them without anything changing.

In my Sound Preferences menu, everythign is "Autodetect" except "Sound Capture" which is set to ALSA, and the "Default mixer track" which is set to "Alsa mixer".

when i click "Test" on any of these i receive:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```

"Enable software sound mixing" is enabled, i mention this because when searching for solutions somebody said to switch it off, but it had no effect.

That's pretty much everything I can think of that might be relevant, if there's anything else let me know. I've searched for this problem, and seen a few things, tested them and nothing seems to happen, and the rest of it i don't really know what they where saying to do, so if you could talk in simple terms that'd be great. Thanks very much for any replies.

-andy

---

### Post by Crafty Kisses on 2007-11-01
Hmmm, post the following output:
```
lspci
```

---

### Post by gunhippy on 2007-11-04
Sorry it took so long to get back >_<

When sound isn't working:

```

andy@ubuntu:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
```

When sound is working:

```
andy@ubuntu:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

```

thanks

-andy

---

### Post by xjgnsdof on 2007-11-04
I have this exact same problem, though nobody has posted a single answer in my thread. Any ideas on this (our) problem?

---

### Post by gunhippy on 2007-11-05
Bump for us both

---

### Post by daimaru on 2007-11-05
hey there gunhippy i may have a similar problem. do you have VLC media player installed? if not install it :) and go to preferences -> audio -> output modules -> alsa . 
what does it say under "alsa device name:" ? 
when i have sound mine says hw:0,0 if i don't it says either hw:0,1 or hw:1,0 so i'm looking for a solution to bind my audio to hw:0,0 from boot. 
since i have a usb audio i only have to unplug it and reinsert it, but maybe the same thing is happening with your soundcard. don't know for sure but i hope someone can give an answer on this .

---

### Post by gunhippy on 2007-11-05
MY ALSA device is simply Default, when i change it between 0,0 and 0,2 both of them leave me with no sound, switching back to default sets sound working again.

I'm not using USB for my sound yet, haven't gotten round to buying a new headset, i'm just using a basic, thing, not sure what they're called O.o speakers with a thin cable and a lil metal thing on the end that you find as standard on mp3 player headphones and stuff (i'm technical arn't i? :] )

---

### Post by SunnyRabbiera on 2007-11-05
you can try OSS or something

---

### Post by gunhippy on 2007-11-05
Could you explain what that is/what it would do/how to do it please?

Thanks

---

### Post by xjgnsdof on 2007-11-05
When I go into VLC (when I get no sound), my ALSA device is set to "default." When I select my Sound Blaster (1,0), videos play with full sound in VLC only. I get sound nowhere else. I guess this is a step forward...

---

### Post by gunhippy on 2007-11-07
Still happening, i'm without sound atm :c

changing anything in VLC doesn't give me sound.

---

### Post by xjgnsdof on 2007-11-13
I think I've solved the problem.

```
gksudo asoundconf list
```

This will give you a list of soundcards. Note the name of your soundcard in the list. Then, input

```
gksudo asoundconf set-default-card *sound card*
```

Where *sound card* is the name of your sound card in the list above.  I've reboot my PC multiple times and have gotten fully-functional sound after each boot. Give it a try.

---

### Post by xjgnsdof on 2007-11-15
Also, you want to disable any other sound cards to remove any conflicts between them and your installed sound card. To do this, find the sound cards that you want to disable after inputting ```
lsmod | grep snd-*
```. Then, ```
 sudo gedit /etc/modprobe.d/blacklist
```, where you will input ```
blacklist (name of sound card to blacklist, as given by the lsmod command)
```.

---

