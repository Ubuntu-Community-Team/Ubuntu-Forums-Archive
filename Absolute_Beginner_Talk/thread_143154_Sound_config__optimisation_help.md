---
title: "Sound config / optimisation help"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by mackinax on 2006-03-11
I'd like to limit my sound card's output level. Is there a way I can prevent the mixer's master volume from going above 50%, or otherwise cut the output level in half? (such as with a custom alsasink output pipeline?)

---

### Post by Pragmatist on 2006-03-12
Making settings in this file should do it: /var/lib/alsa/asound.state
You can find out more about that with: ```
man alsactl
```
You can read more about different alsa programs by: ```
man -k alsa
```

---

### Post by mackinax on 2006-03-12
If I understand this file correctly, asound.state is only used to restore the mixer settings when alsa starts up. If that is not correct, please explain how I can lock the master volume with it.

Thank you!

---

### Post by Pragmatist on 2006-03-12
Just so I understand exactly what your trying to do, "lock it" from what or whom?  Other programs? Other users?

---

### Post by mackinax on 2006-03-13
From everything.

The output level from this onboard sound device is much too high (it's wayyy higher than the output from my PCI sound card ...which happens not to be Linux compatible). If the mixer is set too high, I get nothing but high-pitched shrieking out of my amplified speakers, and their volume is not not even at 50%. (Klipsch Promedia 2.1)

So basically I want to prevent the output from rising to a level that could damage my speakers.

---

### Post by meborc on 2006-03-13
i can understand your avatar now :D  (sorry for off-topic post)

---

### Post by Pragmatist on 2006-03-13
What type of onboard sound do you have (chipset if you have it. motherboard info?)?
Is the volume all the way up in the alsamixer when this happens?
Have you tried OSS?
What type of speakers are you using?
How are they connected to the card (stereo jacks? RCA?)?
Is anything else attached to the soundcard?

Give us the output of these please:
```
lspci | grep audio
```
```
lsmod |grep snd
```

---

### Post by mackinax on 2006-03-13
[QUOTE=Pragmatist]What type of onboard sound do you have (chipset if you have it. motherboard info?)?[/QUOTE]Mobo= ECS K7S5A : Chipset= SiS SI7012 / C-Media CMI-9738 , AC'97

> Is the volume all the way up in the alsamixer when this happens?I believe it happens before vol reaches 100%

> Have you tried OSS?Not really.

> What type of speakers are you using?Klipsch Promedia 2.1

> How are they connected to the card (stereo jacks? RCA?)?Stereo mini jack to the Line-out. The board has Line-In, Line-out, and Mic. jacks.

edit: The speaker system has an amp, and idealy should be connected to a "*line level*" output. 
The soundcard's line-out is surely being amplified much beyond line level. ... [http://en.wikipedia.org/wiki/Line-level](http://en.wikipedia.org/wiki/Line-level)

> Is anything else attached to the soundcard?A TV tuner [WinTV BT878] is connected to the Line-in.

> Give us the output of these please:
**lspci | grep audio**
```
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:0b.0 Multimedia audio controller: VLSI Technology Inc Thunderbird (rev 06)
```
Note - I dual boot with Windows, and the second entry above is a Philips Acoustic Edge PSC706 PCI soundcard that I'm not able to use in Linux.

> **lsmod | grep snd**
```
snd_bt87x              13768  0
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  9 snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  3 snd_bt87x,snd_intel8x0,snd_pcm
```

---

### Post by Pragmatist on 2006-03-13
Try this:
```
hal-device-manager
```
Find both sound cards.  When you click one of them on the left, you will see information on the right contained in 3 different tabs (Device, PCI, Advanced) Check all of the information and give it to us here for both cards.  We especially need to driver information for both cards.

---

### Post by seismicmike on 2006-03-13
[QUOTE=mackinax]I'd like to limit my sound card's output level. Is there a way I can prevent the mixer's master volume from going above 50%, or otherwise cut the output level in half? (such as with a custom alsasink output pipeline?)[/QUOTE]

That's funny, I have the opposite problem. I have sound but it's REALLY REALLY quiet, and I can't boost the volume. Does anyone know how I can fix that???

---

### Post by mackinax on 2006-03-13
Onboard sound device -

Device: [[IMG]http://img102.imageshack.us/img102/1535/device6fu.th.png[/IMG]](http://img102.imageshack.us/my.php?image=device6fu.png)   PCI: [[IMG]http://img55.imageshack.us/img55/9172/pci9vk.th.png[/IMG]](http://img55.imageshack.us/my.php?image=pci9vk.png) Advanced: [[IMG]http://img55.imageshack.us/img55/3886/advanced8ig.th.png[/IMG]](http://img55.imageshack.us/my.php?image=advanced8ig.png)


Is the other card really relevant? It's not used by Linux, as there are no drivers for it. I can remove the card from it's slot if it might cause some sort of conflict.

---

### Post by Pragmatist on 2006-03-13
>  Is the other card really relevant? It's not used by Linux, as there are no drivers for it. I can remove the card from it's slot if it might cause some sort of conflict.  
If it were me I would definitely try removing the PCI card and just test the onboard. To answer your question, I do think the other card might be relevant. Even though there is no driver that works for your card, doesn't mean that there is no driver attributed to the card. I'm no expert on this stuff, but I have done my share of trial and error with linux hardware. The basic rule is isolate and test and then add one more element...then isolate and test again...then add one more element, etc...

The images of hal-device-manager are nice, but the full information is better. I can't fully read what is in the left column and I would like to see the information for both cards.

What led me to all of this was a comparison of your lsmod to mine.  You have these two:
[B] snd_bt87x 
 snd_intel8x0 [/B]

I believe these are both drivers. I have every snd module you have, and the one driver for my card.  You seem to have two drivers.

As I said, I would try removing the PCI card and see if that helps.  If it doesn't that is also useful information.

---

### Post by mackinax on 2006-03-14
[QUOTE=Pragmatist]

What led me to all of this was a comparison of your lsmod to mine.  You have these two:
[B] snd_bt87x 
 snd_intel8x0 [/B]

I believe these are both drivers. I have every snd module you have, and the one driver for my card.  You seem to have two drivers.
[/QUOTE]
Oh, well as I mentioned in post #8, I have a TV tuner card, which would account for the "snd_bt87x"

I don't think there is anything wrong here except that the line-out signal from this onboard 'card' is able to go way above standard "line level" power level. That isn't too unusual / surprising. I just want to, on the software level, limit the maximum possible volume - since the hardware lacks an actual line level output.

---

### Post by Pragmatist on 2006-03-14
> I just want to, on the software level, limit the maximum possible volume  A driver IS software.  My advice is the same:  
 1. Test your on-board card without ANY other sound devices attached.
2. Control for some variables such as: put your speaker's volume control at the lowest possible and manipulate volume totally on the computer. Note the exact volume level where there is a problem. Then do the reverse. 
 
There are at least two ways to solve a problem: Wait for somebody to give you the exact answer your looking for. Or, try to troubleshoot the problem and figure it out yourself. I have been trying to help you with the second method
 
There may be a simple solution, and I hope there is. My guess, however, is that you are experiencing the effects of combining a poor, limited, soundcard (as most onboard soundcards are), with a good set of speakers.

---

