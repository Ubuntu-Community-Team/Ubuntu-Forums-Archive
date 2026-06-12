---
title: "What would cause a sound card to stop working?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by TheFourElements on 2008-04-10
Last December I bought and installed a new sound card. It worked fine until last night. I shut down my computer for a while and when I turned it back on it just wouldn't work. I can't explain what happened any better than that because I really don't know. Any help is greatly appreciated.

---

### Post by edm1 on 2008-04-10
Have did you install anything new? Post the output of 'lspci'.

---

### Post by buried on 2008-04-10
try this is terminal
```
alsamixer
```
and enable everything :)

---

### Post by TheFourElements on 2008-04-10
> **buried said:**
> try this is terminal
```
alsamixer
```
and enable everything :)

No dice. Didn't work.

---

### Post by TheFourElements on 2008-04-10
> **edm1 said:**
> Have did you install anything new? Post the output of 'lspci'.

I haven't installed or upgraded anything for a while. And what is "Ispci"?

---

### Post by Bruce H. McCosar on 2008-04-10
lspci should show the PCI cards attached to your system.  You open a terminal window, type ```
lspci
```, highlight the output, copy the text, and post it here inside the code tags (one of the buttons above -- look how it reformatted the 'lspci' text in the example above).

---

### Post by TheFourElements on 2008-04-10
```
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

Here it is. I hope it helps.

---

### Post by Bruce H. McCosar on 2008-04-10
Ouch.  I see a couple of possibilities in there.

First, your soundcard seems to be a SoundBlaster Audigy LS.  I'm not familiar with that brand, but I know that there are ALSA drivers that work with it.  Case in point: it WAS working.  Therefore, something changed in the configuration.

OK, let's try some detective work.  In a terminal window, try the following commands, and in each case, post the output here.  If you get a huge amount of info, try to sort through the output and only print the parts that seem to be about the sound system.

You can copy and paste these commands directly into your window.  Be sure to tell us which command gave what output.

#1:

```
lsmod | grep snd
```

This should show which ALSA sound modules you have loaded and running.

#2

```
for X in cards devices modules ; do echo $X && cat /proc/asound/$X ; done
```

Similar, but what I'm looking for is something that has put the system in confusion.  This is looking at the problem from a different direction.

#3 (the big one, if you get to this stage, just post the whole thing.)

```
ps -A
```

This will show every active process in the form of a list.

I'm not sure how much help I can be, but I spent a good bit of time debugging sound on my old Debian distro -- every now and then, for no real reason, the levels in Alsamixer would drop down to zero.  That's what one of the posts above was asking about.

If you have time, look through your system settings menus and try to find the 'sound mixer' application of your choice.  I run Kubuntu, so mine is called KMix; there's a little button at the bottom that lets you pull up an actual mixer panel and change the levels of your sound sources and outputs.  The trick is, depending on the card, some of these choices are good, and some are bad.  In general, you want to try flipping on and off the different outputs and inputs, in different combinations, at reasonable sound levels.  I'd say take a media player that worked, load a sound file in it, and run the player -- make sure your speakers are on, and listen for the output as you run your speakers.  Often there are output sliders called 'PCM' and 'Master'.  These should be the business end of things.  Make sure they are **enabled** (not muted, or switched off).  Try different sound sources -- does the CD player work, but not a file on the hard drive?  Can you get any sound through the Line in or aux inputs of your card?

Sorry it took me a while to get back -- I was cleaning tile and painting doors almost all day.

---

