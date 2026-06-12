---
title: "Sound Blaster Audigy SE problems"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by ylwsub68 on 2008-02-19
I'm completely new to Linux, and I've only had it installed for three days. So please bear with me. :-)

I have a Sound Blaster Audigy SE card, and it's been working intermittently on and off with different little things I tried that I found in the forums. I'm not sure what I did, I just followed the directions, but now my sound is completely not working again, and I'm not sure where to start.

That's just it... I'm not sure what to try, lol. I step-by-stepped through [this guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound") and it worked, but then the next time I started my computer (this one), my sound just isn't working now.

Suggestions?

---

### Post by jan de beuker on 2008-02-20
If you type alsamixer in a terminal you will get a control panel maybe your audio is just mute.
Using the up/down and left/right arrows you can control it

---

### Post by ylwsub68 on 2008-02-20
Strange, I just booted up my computer again and the sound works when I play music from Rhythmbox. However, I get no sound from Totem for some reason.

I checked alsamixer and nothing was muted. Any guess why this is so intermittent?

---

### Post by Therion on 2008-02-20
I have a similar sound card, and was having similar problems.  

Try this:  Open up the Volume Control, go to the "Switches" tab, and untick the check-box labeled **Analog/Digital Output Jack** and see if you get sound a little more consistently.  That's what solved the problem for me.

---

### Post by ylwsub68 on 2008-02-20
I don't have that box in my Switches.

But here are the devices it lists in the "Change Device" menu:
CA0106 (Alsa mixer)
Intel ICH5 (Alsa mixer)
USB Audio Device (Alsa mixer)
mixer00 (OSS mixer)

Being totally new to Ubuntu, I don't know why there are four devices when there really should be two: my sound card and my mixer (that's the USB Audio Device).

Does this give any more insight to the situation?

---

### Post by jan de beuker on 2008-02-21
Does your motherboard have onboard sound ?
If so try switching it of in the bios 
Mayby some time's the wrong soundcard is used

---

### Post by Therion on 2008-02-21
> **ylwsub68 said:**
> I don't have that box in my Switches.
Open Volume Control and then Edit/Preferences. 
Under the "Show tracks to be visible" put a check in the box for **Audigy Analog/Digitial Output Jack**.
NOW go to the "Tracks" tab and try turning the Analog/Digital Jack on or off (if one doesn't work, try the other) and see if that solves the problem.

---

### Post by warrior24 on 2008-02-21
I have the same problem But I am lost by your directions .

---

### Post by ylwsub68 on 2008-02-21
> **Therion said:**
> Open Volume Control and then Edit/Preferences. 
Under the "Show tracks to be visible" put a check in the box for **Audigy Analog/Digitial Output Jack**.
NOW go to the "Tracks" tab and try turning the Analog/Digital Jack on or off (if one doesn't work, try the other) and see if that solves the problem.

I don't even have that in my Tracks. But it seems now the only problem is getting sound out of Totem.

---

### Post by Loki*PI on 2008-02-22
Right on.  Been messing with stuff for two days and your suggestion got it working.  Maybe the last needed tweek.  Thanks

---

### Post by Therion on 2008-02-22
> **warrior24 said:**
> 

I have the same problem But I am lost by your directions .
Let me see if I can clarify for you:

1.  Right-click on the Volume Properties icon in the panel.
     [1a.  If you don't HAVE a Volume Properties icon in your panel, right-click ON the panel and add it.]
2.  Click on the Edit menu.
3.  Click on Preferences.
4.  Scroll through the list ("Show tracks to be visible") put a check in the box for **Audigy Analog/Digitial Output Jack**.
5.  Exit the Preferences menu, but not Volume Properties.
6.  Click on the "Tracks" tab at the top.
7.  Try enabling, and/or disabling, the check box for "Audigy Analog/Digital Output Jack" to see if doing one or the other solves your problem.

> **Loki*PI said:**
> 

Right on.  Been messing with stuff for two days and your suggestion got it working.  Maybe the last needed tweek.  Thanks
Glad to hear it!  Assuming your comment was directed at me...

---

