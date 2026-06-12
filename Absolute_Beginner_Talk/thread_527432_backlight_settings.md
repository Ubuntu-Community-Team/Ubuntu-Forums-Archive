---
title: "backlight settings?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by tobyfountain on 2007-08-16
Hi everyone.
I have just installed ubuntu on my laptop (sony vaio VGN-N21M). So far, so good - i esspecially love the desktop effects and the cube thing!!

However, the only problem so far is that I cannot change the brightness of my backlight, and it is not as bright as i need it. How can I change this? I have tried the hotkey on my keyboard for it, but it has no effect (even though the sound one worked well).

Please can someone tell me an easy, step-by-step way to make my screen brighter?


Thanks in advance,

Toby Fountain

---

### Post by oilchangeguy on 2007-08-16
> **tobyfountain said:**
> Hi everyone.
I have just installed ubuntu on my laptop (sony vaio VGN-N21M). So far, so good - i esspecially love the desktop effects and the cube thing!!

However, the only problem so far is that I cannot change the brightness of my backlight, and it is not as bright as i need it. How can I change this? I have tried the hotkey on my keyboard for it, but it has no effect (even though the sound one worked well).

Please can someone tell me an easy, step-by-step way to make my screen brighter? 


Thanks in advance,

Toby Fountain

are you running on battery power? if so change the power settings in the bios, to allow full power when using batteries. this will of course, decrease your run time.

---

### Post by tobyfountain on 2007-08-16
im connected to the mains power all the time.
any ideas?

---

### Post by tobyfountain on 2007-08-16
anyone? please?


thanks

---

### Post by blithen on 2007-08-16
Did this just suddenly happen?
Also I would recommend changing the BIOS settings to what the other person said.

---

### Post by amazingtaters on 2007-08-16
On my Acer Aspire there are built in key commands (the Fn key plus the left/right arrows) to adjust my brightness. Do you have anything like that?

---

### Post by polyscene on 2007-08-21
Hi 
I also run Ubuntu on a VGN-N21M
For brightness go to: 
System
      Preferences
              Power Management 

and change the brightness there.

Otherwise - open the terminal window and change the gamma by with the following:
xgamma -gamma 0.8

I have my screen set at 0.8 but you can change this number up and down to get what you want

Cheers

Polly

---

### Post by pHreaksYcle on 2007-10-14
I have looked into this for my Dell 1501 laptop and the short answer I found is "downgrade your BIOS" 

Hope this is some help.

---

### Post by crono141 on 2007-11-02
> **polyscene said:**
> Hi 
I also run Ubuntu on a VGN-N21M
For brightness go to: 
System
      Preferences
              Power Management 

and change the brightness there.

Otherwise - open the terminal window and change the gamma by with the following:
xgamma -gamma 0.8

I have my screen set at 0.8 but you can change this number up and down to get what you want

Cheers

Polly

My power management doesn't have a brightness setting.  Is there a file which governs this that I can gedit so I get full brightness all the time?

---

