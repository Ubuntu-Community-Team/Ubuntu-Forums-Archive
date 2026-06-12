---
title: "Sound magically STOPPED working lol"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by lase on 2008-04-04
Okay, 

Sound stopped working. Have no clue why. I noticed that timidity had failed to start but I don't know what that does and everything works fine so...?/

How do I fix it :P

---

### Post by northern lights on 2008-04-04
What version of Ubuntu are you running?

Can you post the output of ```
cat /proc/asound/cards
```

---

### Post by lase on 2008-04-04
7.10 is my version.

Output: cat: /proc/asound/cards: No such file or directory

---

### Post by northern lights on 2008-04-04
Wicked. You don't have a soundcard installed. I'm a bit dumfounded, to be honest. But if you had any soundcard, virtually any, that file should exist. Can you post the output of ```
lspci | grep audio
```

and if that gives you nothing the entire ```
lspci
```

---

### Post by lase on 2008-04-04
Yeah, it doesn't make sense considering I was listening to music RIGHT before I restarted :P

```

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)

```

Thats for lspci, lspci | grep audio didn't return anything.

---

### Post by northern lights on 2008-04-04
"lspci | grep audio" didn't work cause of case sensitivity. What's "Audio device" for you is "Multimedia audio controller" for me. "... grep Audio" would have returned the required line.

Anyways, the good thing is, your device is there. Bad thing is we gotta look for a new solution. Can you check whether ALSA is installed and running properly?

---

### Post by lase on 2008-04-04
And ALSA is...??

Sorry, Linux newbie :P

---

### Post by northern lights on 2008-04-04
ALSA is the linux sound architecture. For starters try running ```
alsamixer
```While you're at it, check whether the PCM or anything else is muted.

--> MM is muted, OO is not...

---

### Post by lase on 2008-04-04
alsamixer: function snd_ctl_open failed for default: No such device


.......?

---

### Post by northern lights on 2008-04-04
mkey, we're getting there.

the absence of a proper ALSA seems to be the core of the problem.

Check whether the packages "alsa-base" and "alsa-utils" are installed (Synaptic!)

---

### Post by lase on 2008-04-04
Yes,

They be installed :P

What now?

---

### Post by erginemr on 2008-04-04
I am sorry for barging in, but I believe by following the steps in this howto:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

you will be able to have the sound work. Granted your sound card doesn't match the one for which this howto has been written, but since it is HDA, chances are that it will work.

---

### Post by northern lights on 2008-04-04
> **erginemr said:**
> I am sorry for barging in
Jesus Murphy - the more the better.

> **erginemr said:**
> Granted your sound card doesn't match the one for which this howto has been written, but since it is HDA, chances are that it will work.

Are you sure that, just cause the device bears "High Definition Audio" in its name, it's in anyway related/comparable to Intel's HDA (ICH8 family) chipsets? This guy was saying it worked at some point. Intel's ICH8 cards never work out of the box in Gutsy. Further, while not working properly, they still show up in "/proc/asound/cards".

Fair enough though, give it a go. I'm lost now also. Dunno what else to do.

---

### Post by lase on 2008-04-04
Still isn't working...... XD

---

### Post by erginemr on 2008-04-04
OK. I guess we have to play the hard ball and venture to install the latest ALSA driver. (Actually, apart from the HDA Intel vs. HDA NVidia reference, what that link did was to update some ALSA modules to a later version, 1.15 I guess.)

Here there are two easy to install scripts that will update your ALSA driver to ver. 1.16. Please give it a go:
[http://ubuntuforums.org/showpost.php?p=4450631&postcount=5](http://ubuntuforums.org/showpost.php?p=4450631&postcount=5)

---

### Post by lase on 2008-04-04
It works now :P

Me is happy :P

---

### Post by erginemr on 2008-04-05
Great news! :D

And for the sake of documentation for future solution seekers who happen to come across this thread, could you please explain what exactly you did to solve your sould problem?

---

### Post by lase on 2008-04-05
I used the scripts that someone had posted.

---

