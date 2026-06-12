---
title: "No Sound"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Quakky on 2008-03-13
Hey,
Just like the rest of the posts that talk about sound problems, this is one of em.

My sound was working yesterday when I installed 7.10 from clean partition. I couldnt get the graphics card to work right so I didnt really notice when the sound disappeared (could have been after i updated) 

Anyways Ubuntu doenst see a soundcard, but it does (i think) detect some kinda playback device. 

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8277
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

I tried alot of solution methods that were suggested here..but no matter what, i always get "aplay: device_list:204: no soundcards found..." 
My speaker thing on the panel is got a "mute" on it and when I click it, it says "No volume control GStreamer plugins and/or devices found." 

any suggestions?

My soundcard (Supremefx II  -ADI1988B) can be concidered onboard since it comes with the motherboard, I just have to plug  it in like any other normal soundcard.

Thanks in advance

---

### Post by spiderbatdad on 2008-03-13
you could try ```
sudo modprobe snd-hda-intel
sudo modprobe snd_intel8x0
```

Then run ```
asoundconf list
```

and post back the results.

---

### Post by Quakky on 2008-03-13
for "sudo modprobe snd-hda-intel" i get "FATAL: Module snd_hda_intel not found."
for "sudo modprobe snd_intel8x0" i get nothing
for " asoundconf list " i get 
'Names of available sound cards:
U0x46d0x8b2'

---

### Post by Oldsoldier2003 on 2008-03-13
> **Quakky said:**
> for "sudo modprobe snd-hda-intel" i get "FATAL: Module snd_hda_intel not found."
for "sudo modprobe snd_intel8x0" i get nothing
for " asoundconf list " i get 
'Names of available sound cards:
U0x46d0x8b2'
Take a look at this thread, its very useful for fixing sound issues:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Quakky on 2008-03-13
well i have tried everything except compiling my own drivers..
2 things I would like to mention: 

when I type "aplay -l" I Dont get "aplay: device_list:221: no soundcard found." , but rather I get " **** List of PLAYBACK Hardware Devices ****" and then Nothing.. 

also when I type alsamixer, I get "alsamixer: function snd_ctl_open failed for default: No such device"

Im going to try to compile my own drivers..even though i strongly believe that this step should have been not needed...so much for user friendly eh?....

---

### Post by konungursvia on 2008-03-13
Did you try installing the backports? do this then reboot:

sudo apt-get install linux-backports-modules-generic

Hope this helps.

---

### Post by Quakky on 2008-03-13
Problem was solved..

I reinstalled Ubuntu, as soon as i logged in I downloaded vnc, and had a professional user install essentials.. 

sorry to say that this was my solution, but honestly ppl who having sound problems, if you cant justify hours of work just to get ur audio to work, then dont even start..just reinstall and be happy with the fresh ubuntu.. if u can get someone to help u, then do so..if you cant and uve failed many times at trying to get ur sound to work, then I really dont know what to say

Hopefully sooner than later, ubuntu will get easier, and more compatible as time goes along.

I used up 2 days trying to get Ubuntu to have sound, and in the end It took this guy 20 mins to get me started..

Thanks Daan!

---

