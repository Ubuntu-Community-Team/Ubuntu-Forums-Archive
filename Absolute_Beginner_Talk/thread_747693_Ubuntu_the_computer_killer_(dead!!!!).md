---
title: "Ubuntu the computer killer (dead!!!!)"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by svetlo56 on 2008-04-06
I have installed Ubuntu on a PC which run great for a while and then suddenly the computer died dead. No video, even BIOS startup screen, the light on monitor stays yellow (no signal). OK, the computer died,seen this before, and I replaced the motherboard with another one with integrated video and everything was fine and dandy for a few days, then puff and the second computer dies. No BIOS start up screen, no nothing. Tried to put different video card, power supply, monitor, removed HD to get BIOS startup screen, **removed everything but memory and CPU** to get BIOS startup screen, nothing works, the light on monitor stays yellow. Dead dead. It does start and shut using the power button.

I and confused, whats going on? Is Ubuntu killing the computers and how? Why don't I get even BIOS startup screen?

Please, NOT EVEN BIOS STARTUP SCREEN!!!!!

I know it's insane, but why 2 computers died?

I am not a beginner, I have put together about 40-50 computers so far and have wide experience with both Windows and Linux, but never like this. 

TOTALLY DUMBFOUNDED.

---

### Post by Yes on 2008-04-06
It's (near) impossible for software to brick computers to the point where they won't even POST.

Try resetting the CMOS.

---

### Post by JoshuaRL on 2008-04-06
I agree, software doesn't kill hardware.  Also try another set of RAM.  If the memory is bad then it wouldn't POST to BIOS.

---

### Post by bsharp on 2008-04-06
The motherboard may be making contact with your case and shorting something out.  Try getting an anti-static bag (the one your motherboard came in would be great) and try booting with the motherboard on that (not too long, just see if it POSTs).  If it works I would recommend going through your case to find where it could possibly be shorting.

---

### Post by jay019 on 2008-04-06
If its any consolation, I had the same problem a short while ago. Only my computer was running XP. So I doubt the OS had anything to do with the hardware failures.

---

### Post by svetlo56 on 2008-04-06
The other motherboard came with different set of RAM. In fact, the second one was totally different computer, Duron based, which worked with XP for at least 3 years without flaw. Power supply, video card, HD and pretty much everything else was different.

Still worth a shot to reset the CMOS and try different RAM.

I do know that it's difficult to kill hardware with software, that's why I am dumbfounded.

---

### Post by Jareth on 2008-04-06
Hmmm, wouldn't have a clue myself but to check other "variables".

Where are you doing the building? Is there anything that might screw it up lying around you might have overlooked, like a mighty magnet?
Or have you recently made any other changes to your area that might be affecting it?

I'm trying to remember a story I heard of something similar to this that a boffin at work told me. In that case it was something ridiculous like the customer was putting fridge magnets on their case.

I'm just suggesting that its something other than faulty hardware or Ubuntu.

:confused:

---

### Post by wormser on 2008-04-06
> **JoshuaRL said:**
> I agree, software doesn't kill hardware.  Also try another set of RAM.  If the memory is bad then it wouldn't POST to BIOS.

It would be more accurate to say software *rarely* doesn't kill hardware.  I personally had the [upgrade to Gusty]("http://ubuntuforums.org/showthread.php?t=620618") kill my external amplifier and now I have no external sound.  The point is it can happen but is extremely rare and probably unlikely.

---

### Post by svetlo56 on 2008-04-06
Actually I did kill (a different computer) by forcing a DDR memory in DDR2 socket. The video died. But not this time I swear.

(Obviously, I am a gentle soul).

---

### Post by tad1073 on 2008-04-06
Where you pluged into a surge protector-probably a dumb question but I have to ask. Maybe your fan shorted and the sys. is overheating, maybe your power supply has a short somewhere, just some ideas...

> **bsharp said:**
> The motherboard may be making contact with your case and shorting something out.  Try getting an anti-static bag (the one your motherboard came in would be great) and try booting with the motherboard on that (not too long, just see if it POSTs).  If it works I would recommend going through your case to find where it could possibly be shorting.

find some spacers or put a couple of washers to use as spacers

---

### Post by AndrewEsther on 2008-04-06
I remember reading somewhere, whilest I was deciding whether or not to use ubuntu, that there was something about ubuntu (linux in general, maybe?) not controlling the cpu fan correctly... were all your fans running when you turned your computer on?

---

### Post by alejo0823 on 2008-04-06
I would recommend checking less obvious things if everything else fails, check the power cord or the wall socket, also some power supply's have a switch to change the voltage, be sure that's set properly. remember that an electrostatic charge can damage electronics when you are handling them.

---

### Post by xyphur on 2008-04-06
1) Severe overheating damage, CPU fan/heatsink is either clogged, not receiving proper voltage, or has not been interfaced to the CPU core properly. 
2) Case is contacting mainboard somewhere and tripping the ATX power supply's short-circuit protection. Somewhat rare, but indeed not unlikely. In the event the power supply doesn't have proper short-circuit protection, the PSU could be attempting to supply massive amounts of current to keep up with the demands that the short-circuit is causing on the mainboard, resulting in blown components that aren't designed for those currents.
3) Power supply is bad and is supplying out-of-spec voltages/currents to the equipment causing permanent damage to vital parts, usually the CPU/RAM power circuitry.
4) Power supply set on wrong input voltage. Usually this isn't an issue as most decent power supplies will refuse to power on if the wrong input voltage range is selected... but if you've got a sub-par unit (which is easier than one would think), there is a possibility that it ignores the selected AC range and just goes ahead and tries to power the equipment regardless. This is a bad thing. Unlikely though in your case as you probably would've seen smoke by now...

To be completely honest, I'm leaning more towards the problem stemming from some sort of power supply issue. Get an ATX power supply tester, they're not expensive and they are an invaluble tool to have to prevent both wasted time & headaches troubleshooting parts of a computer that work fine, when in the end it's a faulty PSU after all.

As someone else suggested, connect everything up with the mainboard laying on something completely non-conductive like the anti-static bag the mainboard came in. Be certain nothing is coming into contact with anything it should not be. Double - no, scratch that - TRIPLE check this.

One final note, ALWAYS WEAR A STATIC GROUNDING STRAP. Too many people ignore this very simple premise, and too many of those people wonder why their brand new RAM or CPU refuses to POST after popping it into their machine. Yes it is possible to handle computer components without being ground-strapped and nothing happens, but why take the risk, right?

Hope you get everything figured out so you can get back to enjoying Ubuntu ;)

---

### Post by dmizer on 2008-04-06
actually ...

i have lost 5 computers of various make and hardware (mostly laptop, but also one desktop).  all in the last 3 months, and all running ubuntu (feisty and gutsy).  all with the exact same results.  computer suddenly dies (sometimes and audible "pop" can be heard), and is bricked to the point where bios won't even post.

i have tried resetting the cmos with zero success.  these 5 computers are dead beyond repair.  power is not being supplied to the main board.

i'm not saying that ubuntu was the cause of this, but i did find it strange to kill so many computers in such a short time.  i'm down to my backup laptop and my server.

---

### Post by Roaster on 2008-04-06
Are you dual booting? If so, if you shutdown Ubuntu from inside Ubuntu the computer will not power up again until you actually pull the power plug out for several minutes and then plug it back in and  turn the computer on again. Don't know if this is any help. Hope you find the solution,

---

### Post by svetlo56 on 2008-04-07
tad1073 is genius!

I had the computer plugged into the surge protector and surge protector into the battery backup system, auxiliary circuit (non battery backup, supposed to connect into the wall). I plugged the computer straight into the wall and it works!!! 

Don't ask anything, I do not understand either, you learn as long as you live.

Ubuntu is saved!! I will continue to swear at M$. I think Bill Gates was a benign guy when compared to this Ballmer guy who looks evil.

I thank everyone else for help with thoughts of things so obvious that one would not think of them. I feel very humbled.

---

### Post by JoshuaRL on 2008-04-07
Woot!

You might want to thank tad1073 by clicking the little gold star next to Quote on the post that helped you.  And you can go into Thread Tools at the top and Mark Thread as Solved.

Go Ubuntu and Open Source!

---

