---
title: "[SOLVED] Hard drive problem"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by linux phreak on 2008-04-09
Since last two days my computer is having trouble starting up.When i push the power button it fires up but within a second or two the system dies.The system shuts off after emitting a sound similar to a squeaking sound.I have two hard drives.One is old 3 years(Master) and one that is about a year old.Is the computer startup trouble related to hard drive?.Has the drive reached it's expiry date?.

---

### Post by ruy_lopez on 2008-04-09
> **linux phreak said:**
> Since last two days my computer is having trouble starting up.When i push the power button it fires up but within a second or two the system dies.The system shuts off after emitting a sound similar to a squeaking sound.I have two hard drives.One is old 3 years(Master) and one that is about a year old.Is the computer startup trouble related to hard drive?.Has the drive reached it's expiry date?.

Sounds like your Master HD is dying. If the other drive was sick, it wouldn't affect booting. I hope you have a backup?

---

### Post by linux phreak on 2008-04-09
Yes i have a full back up.But i do not know to set master and slave.Its two PATA drives.

---

### Post by ruy_lopez on 2008-04-09
> **linux phreak said:**
> Yes i have a full back up.But i do not know to set master and slave.Its two PATA drives.

Usually the Master is set by configuring jumpers on the drive itself. The drive should show the possible jumper configurations on its paper label.

Something like this:
[IMG]http://www.pcbuyerbeware.co.uk/HDDConfigChart.gif[/IMG]

---

### Post by linux phreak on 2008-04-09
The older one i have is a maxtor too but it does not have such sticker.So i stick the jumper to the two pins right?.Also the wires to the hard drive have two plugs.These wires are huge and causing cooling problems in the pc.Should i buy another single wire?.(i mean with one plug)

---

### Post by ruy_lopez on 2008-04-09
> **linux phreak said:**
> The older one i have is a maxtor too but it does not have such sticker.So i stick the jumper to the two pins right?.Also the wires to the hard drive have two plugs.These wires are huge and causing cooling problems in the pc.Should i buy another single wire?.(i mean with one plug)

Experiment with the jumper until the drive is recognised as Master by the BIOS. For a Master, the jumper normally bridges the first two pins, top and bottom.

Providing you dress the cable properly (keep it away from the CPU fan) it shouldn't cause too much overheating.

In my experience, Hard Drives occasionally break for no reason. I've had drives break that were only a few months old. Yet, sometimes they last forever.

---

### Post by linux phreak on 2008-04-09
Thank you ruy_lopez.I will try to set to master.The CPU case is small and it is very congested inside with umpteen wires and graphics card,modem and similar crap.I will try to tie it up as i possibly can.

---

### Post by StRiFe10101 on 2008-04-09
When you say your computer just shuts down, is that the power turns off... or it just "crashes" and you still see stuff on the screen?  If it turns off completely you might be looking at a power supply problems.  It happens all the time.  

I'd run a hard drive test on the drive also. If you have access to another computer, download a tool to test the hdd.  Seatools for instance.  You can download a cd ISO and boot form it.  Granted those tests aren't 100% accurate but a good place to start.  

The previous "poster" is on the right track... see if you can get things to work ok off ur secondary hdd.

---

