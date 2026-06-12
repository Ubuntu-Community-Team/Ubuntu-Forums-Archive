---
title: "No display when booting! (urgant help needed!)"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by say592 on 2007-04-08
I am getting nothing. I booted fine from the live disk, but when I went to reboot, I am getting nothing! The BIOS screen doesnt even come up! 

On one monitor, it wasnt even detecting a system, so I took the computer downstairs to the other monitor. That one detected the system, but didnt display anything, it went into hibernate mode.

I really need to get this taken care of ASAP, as I got my parents to make the switch, but I think they are worried that I broke their computer.

The computer is an older Gateway, originally designed for windows ME. The live CD ran fine with no problems. I did the install identically to how I have done it in the past, using all defaults and choosing the best settings for this computer.

The computer runs a 900mhz processor, and one stick of 256mb ram and another of 128mb. I put in a 20gb hdd just before I booted from the live CD.

---

### Post by igknighted on 2007-04-08
> **say592 said:**
> I am getting nothing. I booted fine from the live disk, but when I went to reboot, I am getting nothing! The BIOS screen doesnt even come up! 

On one monitor, it wasnt even detecting a system, so I took the computer downstairs to the other monitor. That one detected the system, but didnt display anything, it went into hibernate mode.

I really need to get this taken care of ASAP, as I got my parents to make the switch, but I think they are worried that I broke their computer.

The computer is an older Gateway, originally designed for windows ME. The live CD ran fine with no problems. I did the install identically to how I have done it in the past, using all defaults and choosing the best settings for this computer.

The computer runs a 900mhz processor, and one stick of 256mb ram and another of 128mb. I put in a 20gb hdd just before I booted from the live CD.

If you have multiple hard drives perhaps you need to tell the bios to boot from the other hard drive?

---

### Post by say592 on 2007-04-08
No, single hdd. It was a blank one I put in, and I let it auto format. Im not even getting to the BIOS of it. It just shows nothing.

---

### Post by igknighted on 2007-04-08
> **say592 said:**
> No, single hdd. It was a blank one I put in, and I let it auto format. Im not even getting to the BIOS of it. It just shows nothing.

hmm... did you install the HD properly?  The issue would have to be hardware related, you can't waste the bios by installing linux... thats no possible.  Check you connections and that you vid card is installed properly and everything is hooked up.  Its amazing how many people spend hours trying to find the hard solution when the issue is something really simple like something unplugged.  I know its not likely, but best to rule that stuff out first.

---

### Post by say592 on 2007-04-08
I have checked conections. I know it cant be the BIOS, that just didnt seem possible. I am a n00b at linux, but Im no computer n00b.

Anyways, it is an onboard video card. I know its probably not OS related, but I still need help with this, and for some reason, I just think somehting had to have gone wrong, becuase it was fine just minutes before when it was running live. durring the instal.

---

### Post by LaurelLynn on 2007-04-08
Dear say592,

Check to make sure the second monitor still works with the computer you borrowed it from.  It is not unknown for graphics settings (especially the Hz rating) which are beyond a monitors ability to damage the monitor (very unlikely, but possible).

Laurel Lynn

---

### Post by say592 on 2007-04-08
Monitor is working on the other one, as a matter of a fact, im using it on my windows machine as we speak.

I have no clue what the deal could be....I just want to cry, because I know my dad (a windows network maintance technician) is going to blame the linux and try to make me buy the computer if I dont get it working.....:( Oh well.....

---

### Post by LaurelLynn on 2007-04-08
At that point it has to be a change in the bios, or  something loose (like the monitor cable), or (gasp ) damaged in the hardware. Possibly by static.

Sounds like it could be the first, I certainly hope it is not the last.  The contents of the hard drive have not even been touched at that point.

Without seeing the system upclose....  90% of the times I had a similar problem, it was the monitor cable.

Check and double check all cables. Hit each and every Function key on boot (ten times if necessary), because without graphics, your not even going to be able to reach the bios.

Laurel Lynn:(

---

### Post by say592 on 2007-04-08
Ok, well, as far as a change in the BIOS goes, I didnt think that was possible, I mean, unless it alters the BIOS durring instalation, then it should be fine, completely unaltered.......

Now, I dont think its a loose cable, I have tried two monitors, and I played around to try to figure it out. 

So what does that leave? I mean, static, but how likely is that? I have been building systems for about 5yrs now, and I rarely use static protection *knocks on wood* I know they recomend it, but they do have guards in the hardware now to..........

How do you think I would be able to tell if there was a static issue though? I mean, it looks like the only thing left, anyone know if there is a calibration test I can do with a volt meter or something?

---

### Post by LaurelLynn on 2007-04-08
I mentioned static as a possibility when I read that you had replaced the harddrive.  I admit I have only seen that happen once in 25 years, and then there was an actual pop.

I seem to recall getting past a blank screen and no bios a couple of times before, by unplugging everything but the graphics card (which is on your motherboard anyway).  Then when I booted, I got a error (doesn´t like it without a keyboard).  But the error was visible on the screen.  Then I put the system together one component at a time until I found out which one had the problem.

Laurel

---

### Post by medad on 2007-04-08
Have you pulled out, cleaned, and reinstalled your memory cards or checked you power supply?  Is the fan running?

---

### Post by LaurelLynn on 2007-04-08
Good point medad,

The basic point is to get something on the display, ANYTHING on the display.  Sometimes the only way to do that is to pull everything but the graphics and power out.  It won´t come close to booting, and will beep like crazy. But that is the beep of life. If anything appears on the monitor you at least have something to work with.

That is a lot better than fumbling in utter darkness.

Laurel

---

### Post by say592 on 2007-04-08
Hmm, well, considering that its 3am, I think I will try tommorrow, Hopefully this will all get working......

I dont really think its broke (as in unfixable) so if anyone else has ideas, please let me know. I can then get on to showing my parents how amazing linux can be!

---

### Post by LaurelLynn on 2007-04-08
Best of Luck, I´ll check back again sometime tomorrow. Let me know how it turns out.

Laurel Lynn

---

### Post by say592 on 2007-04-08
I really didnt end up doing anything special. It just worked. I dont know what was wrong, but I tried it on the other monitor with nothing but the monitor plugged in (hdd attached, everything, just monitor and power cables where the only external cables) and it worked!

I brought it to the other one and it worked on that to!

I now just cant get the network to work, but that is in a new thread :)

---

### Post by LaurelLynn on 2007-04-08
Some problems are just like that, you think ¨there just can´t be anything that could cause this!¨. You start unplugging things to isolate what could of caused the problem.  All of a sudden it is back.

So you start plugging things back in expecting one of them to cause the problem again.

Suddenly everything is in AND everything is working.

What caused the problem in the first place??? We may never know.

Anywho, I´m just glad your parents computer is safe and sound.

Laurel Lynn ):P

---

