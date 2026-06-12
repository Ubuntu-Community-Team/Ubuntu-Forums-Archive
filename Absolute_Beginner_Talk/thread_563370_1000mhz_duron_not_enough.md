---
title: "1000mhz duron not enough?"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by uknowho008 on 2007-09-29
or am is it a different problem?

i tried with 2 video cards and 128mb ram and 512mb ram

the comp crashes either at the login screen or after you logged in and run something like updates.

the live cd wont even run with 512. it crashes once its completely booted up into ubuntu.

the only thing i havent tried is a different hd. but as the live cd doesnt run that cant be it right?

whats going on? bad cpu? bad mobo?

also, if i run the system monitor the cpu gets to 100% and after a few seconds it crashes while running updates. so it makes sense that it would be the cpu but i thought 1000mhz would be enough??

---

### Post by qpieus on 2007-09-29
A 1000 mhz duron is good enough. It won't be super speedy, but it's enough. My server is a 1000 mHz duron, in fact.
There must be a hardware problem. Isn't there a memtest option on the grub bootup menu? Run that to see if there is a problem with the ram.

---

### Post by Pumalite on 2007-09-29
Mobo?Brand of video card?Did you try the Alternate CD?

---

### Post by overdrank on 2007-09-29
> **uknowho008 said:**
> or am is it a different problem?

i tried with 2 video cards and 128mb ram and 512mb ram

the comp crashes either at the login screen or after you logged in and run something like updates.

the live cd wont even run with 512. it crashes once its completely booted up into ubuntu.

the only thing i havent tried is a different hd. but as the live cd doesnt run that cant be it right?

whats going on? bad cpu? bad mobo?

also, if i run the system monitor the cpu gets to 100% and after a few seconds it crashes while running updates. so it makes sense that it would be the cpu but i thought 1000mhz would be enough??

HI the thing I am wondering is how much memory is on the system? I understand you worries about the video card bu the main concern is the memory of the system.

---

### Post by uknowho008 on 2007-09-29
i tried 2 different sticks of ram which i no are both good.....

---

### Post by rsambuca on 2007-09-29
Run the memtest on the Ubuntu CD for a few hours and see if anything turns up

---

### Post by uknowho008 on 2007-09-29
ok, ill run the memtest. but like i said, i tried to different ram sticks. i didnt mean a 128mb video card and a 512mb video card i meant i tried 2 different video cards and 2 different sticks of ram.

the mobo is ep-8kta3

and one video card is an ati xtacy something which i swapped out of my everyday computer so i know that one is good.

thanks for all the responses.


EDIT: i did run the alt cd and it installed just fine. it seemed to take a long time though. and it crashes at the loggin screen or just after while running something. like i said at the beggining.

---

### Post by Pumalite on 2007-09-29
I hope you are using the Alternate CD.

---

### Post by uknowho008 on 2007-09-29
> **Pumalite said:**
> I hope you are using the Alternate CD.

yes im using the alt cd

---

### Post by handydan918 on 2007-09-29
> **uknowho008 said:**
> yes im using the alt cd
How about duplicating the error and posting the output of 
```
dmesg | tail -40
```
That may give a clue as to why it's crashing.
BTW, what do you mean, crashing? What exactly happens?

---

### Post by uknowho008 on 2007-09-29
there is no error to give you. by crashing i mean the whole computer just restarts without warning.

ive been running memtest for almost 15min now and still no error. i guess if i can figure this out by later tonight i will try installing xp and see how that runs on it. :(

---

### Post by handydan918 on 2007-09-29
> **uknowho008 said:**
> there is no error to give you. by crashing i mean the whole computer just restarts without warning.

ive been running memtest for almost 15min now and still no error. i guess if i can figure this out by later tonight i will try installing xp and see how that runs on it. :(

That may be a very good idea. A spontaneous reboot may also be the result of a bad power supply, mobo, or other hardware issue.
And 15 minutes is not long for memtest. Don't be afraid to just leave it running all nite.

---

### Post by uknowho008 on 2007-09-29
well i dont know about all night cause its it my room and very loud. but ill let it go for a few more hours. although im sure the memory is fine.

it is only testing the ram correct??

both sticks work fine in other computers.

---

### Post by Neobuntu on 2007-09-29
Test the CD disc both for MD5 match and run it's integrity check from the CD.

Sometimes you just have a poor media/blanks.

If all that is well, make sure you hardware is 100%; with another OS.

---

### Post by uknowho008 on 2007-09-29
the disk is fine. i installed on another system with the same disk.

im going to try xp later. i just really dont really want to run xp on this system.

---

### Post by uknowho008 on 2007-09-30
looks like xp is doing the same thing. so its either my cpu or mobo? anyway to test?

---

### Post by Paulmd on 2007-09-30
> **uknowho008 said:**
> or am is it a different problem?

i tried with 2 video cards and 128mb ram and 512mb ram

the comp crashes either at the login screen or after you logged in and run something like updates.

the live cd wont even run with 512. it crashes once its completely booted up into ubuntu.

the only thing i havent tried is a different hd. but as the live cd doesnt run that cant be it right?

whats going on? bad cpu? bad mobo?

also, if i run the system monitor the cpu gets to 100% and after a few seconds it crashes while running updates. so it makes sense that it would be the cpu but i thought 1000mhz would be enough??

Eenie meenie miney moe. 

Your processor and 512MB ram ARE sufficient to run fiesty. Not 128mb.

To test RAM, run memtest86, it's one of the choices when you press f1 (or is it escape?) during boot.

Many motherboards that were populated with durons failed from bad capacitors.
Capacitors look like itty bitty soda cans. If any are bulging, or leaking- even a little bit - they're bad, and your motherboard is shot.

Also consider overheating, possibly due to excessive dust, or fan failure. 

The duron chips themselves rarely die.

---

### Post by Paulmd on 2007-09-30
> **uknowho008 said:**
> looks like xp is doing the same thing. so its either my cpu or mobo? anyway to test?


To test for overheating, put you fingers on the heatsink, while it's running. If it's painfully hot, it's overheating.

Odds are motherboard, by better than 3 to 1. CPUs don't die that often. No good way to test. There are some diagnostic programs, supplied by the manufacturer. But a duron is far more likely to live in an off-brand, or self built computer than a major manufacturer. 

I'd assume motherboard. 

You can get a secondhand motherboard, and processor cheap (as long as you do the work yourself). Or you can look at it as an excuse to get a better computer.

---

### Post by Shunketsu on 2007-09-30
it could be that the hard drive itself is knackered, how old is it? i've experienced a similar problem before on an old hdd when booting up XP it gets to the logo bit with the bar at the bottom and then the whole system just reboots, if you can hear your hdd making funny whizzing noises when it does this chances are that it could be on it's way out. 1000mhz duron is fine, i have kubuntu feisty running on an 800mhz duron :)

---

### Post by atlfalcons866 on 2007-09-30
is duron the lowend version of athlon? as to celeron is the low end version of pentium

---

### Post by qpieus on 2007-09-30
> **atlfalcons866 said:**
> is duron the lowend version of athlon? as to celeron is the low end version of pentium
yes

---

### Post by armandh on 2007-09-30
Ubuntu runs quite well on an 800 mhz P-III 256 meg ram
it will not install with 128 easily 512 should work fine.
hardware problems  are often the crash cause
I have pitched a lot of old cdr(s)

---

### Post by bobpur on 2007-09-30
I have a Compaq 5WV252 from about 1999 that has been much modified from stock. CPU is up from 750 mhz AMD Duron to a 1ghz AMD Duron. Memory is up from 64 mbs to 640 mbs.
This machine dualboots Windows XP and Ubuntu v7.04. Runs like a Swiss watch. I added a couple of extra fans because I heard, also, that Duron boards are likely to die from heat.

---

