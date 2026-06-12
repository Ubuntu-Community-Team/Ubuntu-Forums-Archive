---
title: "Multiple applications using soundcard at once?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by MattThLinuxNewb on 2007-07-18
Hi, I've been using Ubuntu for about half a year now and have been very impressed with it, but there's still one problem that I can't seem to fix:- Only one application can use the sound card at once, i.e. all applications that output sound must be closed/stopped before another application can use it. I've looked around for answers in this forum and google but can't find any clear solutions. [ This link ]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Getting_more_than_one_application_to_use_the_soundcard_at_the_same_time") came the closest to being helpful, but unfortunately when I used 'aoss' in the console before the command to run ET I just got some strange static noises.
This is what lpsci -v returned related to my sound card:

```
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=256]
        Memory at d0003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>
```

Any help would be great, by the sounds of it I'm not the only one having this problem.
Thanks, Matt

---

### Post by FleetAdmiral74 on 2007-07-19
I have a similar problem. I think I can play something in the browser and another program like mPlayer or VLC at the same time, but if I try to use Hydrogen then it does not work. I wonder if this is a kernel or ubuntu thing...

---

### Post by Atomic Dog on 2007-07-19
You know this is something I have just accepted and never looked into why.  Some things seem to be able to work simultaneously, some don't.  For instance, I can ise totem and vlc at the same time, I cannot get sound from a parallels or VMware VM, or RDC if anything else is using sound.  Not the hill I want to die on, but I'm curious about what some people have done to get things to work myself.  I'll watch this thread and see what some others have done before attempting to fix this myself.

---

### Post by detroit/zero on 2007-07-22
I've noticed the same thing. 

It's not that big of a deal if you're talking about, say, listening to music and watching a video at the same time. Who does that?

Where I find it to be annoying is, for example, playing pool on Yahoo Games and having an IM conversation with someone - I can't hear the alert when their message comes through or when someone logs on/off any more. 

Want to have a VOIP conversation and listen to music? Forget it.

I've learned to deal with it and all.. but it sure would be nifty if someone looked into it (hint hint).....

---

### Post by rod.naph on 2007-07-30
yeah this is my biggest problem with using ubuntu (linux in general it would seem), it is something i've just come to accept and work around almost unconciously.  but when friends use my computer it's just embarrasing!

actually it's not just cause it's crap for friends, there are many many reasons why you'd want to be able to play sounds at the same time from multiple applications.  you may turn it off in one as soon as it starts playing in another, but to have applications lock up or refuse to start because they can't use the sound card is ridiculous, and amazingly annoying!

(seeing kaffeine (i'm kubuntu btw, ;)) dissapear into the background and force me to open a terminal to kill it just because some little flash applet in firefox has decided to take the sound without me noticing... AAAHHH!!!!)

i've put up with this for waaaaay too long, so now an answer would be nice.  does anyone know what the problems are?  what are the issues involved in solving this?

---

### Post by Dylock on 2007-07-30
The problem is that your probably using OSS, which only supports sound from one source. If you want sound from multiple sources, use ALSA. 

Have you downloaded the alsa stuff with synaptic?

---

### Post by qwertas on 2007-07-30
This thread fixed it for me in feisty. [http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound](http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound)

---

