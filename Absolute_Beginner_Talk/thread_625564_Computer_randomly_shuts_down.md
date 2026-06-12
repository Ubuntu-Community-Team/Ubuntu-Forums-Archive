---
title: "Computer randomly shuts down"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by gcrussell1 on 2007-11-28
I'm running Gutsy on an HP zx5000 laptop, and I've just started running into a problem with the computer shutting down after a relatively short period of time (10 minutes to 2 hours). It started happening this morning and it's happened 4 or 5 times since then. The computer doesn't seem to be running too hot, so I don't think it's a heat problem - I've had that problem before on Windows, but it's not running nearly as hot as it was then (been cleaned a couple times in the interim). I've been using Ubuntu for over a month, and the problem just started today, so I'm not really sure what could be causing it. I don't think I changed anything that would cause this problem during the session when it started - the problem first occurred directly after I downloaded the wesnoth-1.3.11 tarball from sourceforge, but I'm not sure if they've got anything to do with each other.

I get info on processes on a black screen when it shuts down like this, so I'll try to give what it says (though it won't be exact).

> Starting anac(h)ronistic cron anacron --- Done
Starting deferred execution scheduler ATD ---Done
Starting Periodic Command Scheduler --- Done
Checking battery state --- Done
Running local boot scripts /etc/r.local --- Done

The battery's full, and the computer's plugged in, so the battery state check shouldn't be the problem. The cron/anacron thing might have something to do with it, but I've done nothing with cron or anacron myself.

Any ideas about what might be causing this? It usually happens when I'm using the computer, but it's happened when the computer's been idle as well. There might be threads on this somewhere else, but a quick search yielded nothing helpful.

Oh, and the video card's a mobility Radeon 9600, with the latest ATI open source drivers (8.43.3 I think).

---

### Post by rax_m on 2007-11-28
Have you checked your system logs for any additional information? 
System->Administration->System Log

There might be something in there that gives a clue.

---

### Post by nudnik on 2007-11-28
Sounds like more of a hardware problem than anything else. It is likely overheating again, or the unit suffered damage when it overheated previously..

---

### Post by ukripper on 2007-11-28
Go into BIOS and change your shutdown temperature (increase it).

---

### Post by athomson on 2007-11-28
Hi,

It is a heat problem.  These laptops have a very bad reputation for overheating. Running anything with graphics causes the graphics chip and cpu to work more, hence it overheats.  You will need to take it apart and clean it. Do not blow compressed air into the vent from the outside, this just causes the dust to become more embedded.   I suspect you find that there is a lot of dust in it.  

Here are step-by-step details [with pictures] on how to do it:

```
http://www.instructables.com/id/Cleaning-Your-Laptop-Cooling-System/
```

Andy

---

### Post by gcrussell1 on 2007-11-28
> **athomson said:**
> Hi,

It is a heat problem.  These laptops have a very bad reputation for overheating. Running anything with graphics causes the graphics chip and cpu to work more, hence it overheats.  You will need to take it apart and clean it. Do not blow compressed air into the vent from the outside, this just causes the dust to become more embedded.   I suspect you find that there is a lot of dust in it.  

Here are step-by-step details [with pictures] on how to do it:

```
http://www.instructables.com/id/Cleaning-Your-Laptop-Cooling-System/
```

AndyAlright, I'm gathering that it's almost definitely an overheating problem (though the symptoms only really match that possibility in that overheating tends to force a laptop to shut down). I'll clean it out again tomorrow, though I did it a few months ago and I run the laptop elevated for better airflow. Thanks for the tip about not blowing compressed air into the vents, though I'm not noobish enough to make a mistake like that. Anyone know how to get to the gpu of this machine? I've cleaned out the cooling system a couple times before, but I've never been able to get the entire case open - I think there's a keyboard screw somewhere that I don't know how to remove or something.

Anyway, thanks - I'll get this guy cleaned out tomorrow and then whine and moan at everybody again if the problem continues. ;)

---

