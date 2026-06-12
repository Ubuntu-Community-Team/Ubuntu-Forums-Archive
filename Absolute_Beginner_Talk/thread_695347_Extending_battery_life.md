---
title: "Extending battery life?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Dissident85 on 2008-02-12
I have just installed ubuntu on my laptop and I have noticed that the battery doesn’t last all that long compared to when I was running windows vista on it. I am lucky to get an hour of use on it now… dose anyone have any tips on how I could extend the battery life?

---

### Post by Boelcke on 2008-02-12
Er, I forget how I setup mine, but I have a dual core processor.  I had to install something to be able to fiddle with how it adjusts the scaling of the processor.  Now, I have a clickable thing up in the top bar that lets me pick On-Demand (the default), Conservative or PowerSave.  It also lets you see what it's scaling your processor to.

Sorry I don't have the technical details in front of me, but that's what you should be looking for.

Additional benefit: When I run it on Conservative or PowerSave, I hear the CPU fan kicking on a bit less, which is nice.

---

### Post by oedha on 2008-02-12
i used my laptop just like handphone.....
use it without acpower until reached critical %
then recharge it......until it 100%....
i unplug the ac again.......use it on battery until critical again....( cycle back )
with this treatment.....i can use mine up to 3 hour........( normal work....typing, browsing, ubuntuforums, plus listening to music through headphone )
i am using HP2258 and gutsy reported my battery is 45%
:)

---

### Post by nwadams on 2008-02-12
Li-ion batteries don't have a memory, so fully recharging it/fully discharging it will not have any effect on how long your battery will last, it will mak eyour power manager time remaining estimate mor accurate but that is all. What kind of laptop do you have? and how long of a battery life were you getting with windows vista?

---

### Post by Whiffle on 2008-02-12
> **nwadams said:**
> Li-ion batteries don't have a memory, so fully recharging it/fully discharging it will not have any effect on how long your battery will last, it will mak eyour power manager time remaining estimate mor accurate but that is all. What kind of laptop do you have? and how long of a battery life were you getting with windows vista?

Incorrect, fully killing the battery is bad to a Lithium Ion battery,

[http://www.batteryuniversity.com/parttwo-34.htm](http://www.batteryuniversity.com/parttwo-34.htm)


Ubuntu gutsy has some unsolved issues with battery life at the moment, no idea why.  

[www.lesswatts.org](www.lesswatts.org) has a wealth of information on saving power in linux...

---

### Post by Dissident85 on 2008-02-12
Boelcke: That sounds exactly like what i need.. or a program that will also turn off hard drives after a certain time... 

if you can remember what that program that you are using is called please post back  :) 



oedha: I do the same thing, its a helps extend battery life... but i know i can get more out of it because 2 days ago when i had windows on it, it was lasting much longer.

---

### Post by nwadams on 2008-02-12
i know fully discharging is bad for any battery, what I meant was discharging until it automaticlaly hibernated, but my laptop gets better battery life with ubuntu than windows...at the worst, ,very similar

---

### Post by Dissident85 on 2008-02-12
> **nwadams said:**
> Li-ion batteries don't have a memory, so fully recharging it/fully discharging it will not have any effect on how long your battery will last, it will mak eyour power manager time remaining estimate mor accurate but that is all. What kind of laptop do you have? and how long of a battery life were you getting with windows vista?

its a hp 530, and i use to get about an hour and a half to about two hours.(i was also able to close the lid and pick it up 2 days later and with in about 3-4 seconds i was back into it)  now i am lucky to get an hour depending on what i am doing.

---

### Post by oedha on 2008-02-12
i suggest to friends of mine who like to plug/unplug the acpower to use no battery at all......unplug the battery........and i am sure about what i've done

---

### Post by oedha on 2008-02-12
as far as i know......windows force the BIOS power management to safe energy and ubuntu defaultly leave it off since ubuntu realize that it's not goog to messed up BIOS setup....let BIOS be handled by BIOS vendor......not OS
(correct me if i am wrong )

---

### Post by LowSky on 2008-02-12
i have an old dell inspiron 8100 running great if not better than it was on XP, You should do a complete cycle or two for the system to learn the normal battery life. Yes letting a Lith-ion battery drain down to 0% is bad, but get it to about 10% the recharge two full times, lets ubuntu learn the limits of the battery.

May I also suggest truning down the LCD brightness, turn off extra settings like compiz, traking, and anyother programs you dont really need running in the backgorund, if suspend and turn off monitor and hard drive features work for you then use those as well. Typical life of a full charge battery is about 3 hours... 5-6 if your a light user... some newer models ae claim 8+ hours but I just dont believe them. Until I see them do it.

---

### Post by PurposeOfReason on 2008-02-12
Important factors are the screen brightness, cpu scaling, and if the hard drive is always being read. I use laptop mode tools with archlinux, I don't know if Ubuntu has it (it should). Mess around in gnome-power-manager.

---

### Post by Whiffle on 2008-02-12
> **PurposeOfReason said:**
> Important factors are the screen brightness, cpu scaling, and if the hard drive is always being read. I use laptop mode tools with archlinux, I don't know if Ubuntu has it (it should). Mess around in gnome-power-manager.

Or disable gnome-power-manager, its known to be a bit on the buggy side as far as saving power goes.  It wakes up Xorg too often and brings the cpu out of sleep.


[http://www.lesswatts.org/projects/powertop/known.php](http://www.lesswatts.org/projects/powertop/known.php)

---

### Post by PurposeOfReason on 2008-02-12
> **Whiffle said:**
> Or disable gnome-power-manager, its known to be a bit on the buggy side as far as saving power goes.  It wakes up Xorg too often and brings the cpu out of sleep.


[http://www.lesswatts.org/projects/powertop/known.php](http://www.lesswatts.org/projects/powertop/known.php)
Learn something new everyday. Useful link, too bad I don't use most of that.

---

### Post by Boelcke on 2008-02-23
Add the CPU Frequency Scaling Monitor from Gnome applets (right click the top menu bar, click add to panel)

Once you've got that up and on there, check out one of these to take control of the frequency scaling.
[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html]("http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html")

[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/]("http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/")

---

### Post by quanumphaze on 2008-02-23
When I try the CPU scaling applet I get an error:

```
**CPU frequency scaling unsupported**

You will not be able to modify the frequency of your 
machine. Your machine may be misconfigured or 
not have hardware support for CPU frequency 
scaling.
```

My CPU should be able to do it, it's a CeleronM420 @1.6Ghz and should scale to 800MHz

---

