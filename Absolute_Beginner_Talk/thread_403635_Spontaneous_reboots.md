---
title: "Spontaneous reboots"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by metol on 2007-04-07
I've gone through my share of hardship over this one...  hopefully someone will find this useful.  Fortunately, I do not give up easily.  Problem appears to be with power management, anyone know what would cause this?

**_Symptom:_**

Completely random reboots.  These are not freezes. You can be working along then all of a sudden, boom, the bios comes up and reboots.  Like someone just reached over and hit the reset button.  The only consistent thing about this (that I can tell thus far) is that the system is not idle when it happens.  It seems to be able to sit at the login prompt all day without rebooting.  I checked the logs to verify this. 

Sometimes it reboots within minutes, sometimes it can go several hours.  This makes diagnosis difficult and frustrating.  It goes along for a few hours and you think you fixed it, then you find yourself staring at the BIOS screen.

**_OS & Hardware Summary:_**

- Ubuntu (32bit) - Edgy Eft
- Kernel: Linux 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux
- nVidia drivers installed via Envy

- PSU: Antec 350W and tried 430W (both new)
- MB: MSI PM8PM-V (new)
- CPU: Pentium D, 2.8GHz Dual-core (new)
- Video: Nvidia FX 5200, 128Mb, 8X AGP
- Monitor: Acer X191
- Memory:  2x512Mb - Kingston DD2-533 (new)
- HDD: 2 - 30Gb IDE Drives, one Maxtor, one Western Digital  (old)
- Belkin wireless network card (new)


**_What I have tried_**

- Reseated all boards / CPU

- Checked for any BIOS updates.. nothing new.

- Checked logs for anything significant before crash... nothing out of ordinary that I can see.

- Memory:
[INDENT]  - reseated several times
  - swapped chips
  - ran memTest several times without errors
[/INDENT]
- Cooling: 
  [INDENT]- Added extra fan to the case
  - Bought thermal grease for CPU/heatsink and made sure there was good contact
  - installed sensor app to monitor CPU temp,  nothing above 51C.  No correlation to CPU temperature and crash propensity.
  - side off of case & 10" fan blowing full blast inside the case... still crashes[/INDENT]

- Disbled all but essential on-chip MB devices(ie no serial ports, internal network, etc.)

- Disabled USB, also toggled legacy support option in BIOS

- Video:
[INDENT]  - Turned off AGP via nvapg="0" in xconfig file.
  - Set AGP to 4X mode  
  - per Nvidia's website, tried several AGP Driving Values (from DA - FF) 
  - swapped video cards from my XP system
  - used the internal video chipset in VESA mode (nvidia card removed from system)[/INDENT]

- Disabled wireless network card

- Disabled IPV6

- Tried a couple different Kernels

- Went and bought a new power supply... $80 dollars wasted.

- ACPI (have not been able to try this)
 [INDENT] - tried to turn off in BIOS but gave kernel panic
  - tried to set acpi=off in grub but also gave a kernel panic[/INDENT]

- Disabled Power Management under 'Services' (both acpid and apmd) 
 [INDENT]  ----> **ALL HAS BEEN FINE FOR SEVERAL HOURS NOW**
   ----> **CURRENTLY SEVERAL HOURS INTO DAY TWO! NO PROBLEMS **(still keeping my fingers crossed)[/INDENT]

---

### Post by dwblas on 2007-04-07
Random, or any other kind of reboot is a hardware problem, almost without exception.  Especially on a distro like Ubuntu where you are using the same system as everyone else and you are the only one with the problem.  An intermittent power supply problem could be causing this.  If it does not reoccur, then the $80.00 might not be wasted.

---

### Post by ed-j on 2007-04-07
Hi Metol !

If you have an FX5200, you may need to use the Edgy "legacy" drivers in [COLOR="SeaGreen"]Add/Remove.[/COLOR]

Also I think the system you are running is too powerful for this Nvidia card. I have a 7600GS, 1G 533 DDR2, 3200+ and no reboot problems with Edgy.

Hope this helps!  :)

---

### Post by metol on 2007-04-07
Thank you for the reply.

After disabling power management (both acpid and apmd) all has been well.  If this is a hardware problem, would it be the motherboard?  I went back to my original power supply and things are still rock solid with power management disabled.

I want to make sure this remains stable over the next few days, then I will try to figure out if it is acpid or apmd causing the problem/conflict.  I'm just happy things are working now.

---

### Post by ed-j on 2007-04-07
Nice one! :)

---

### Post by hardyn on 2007-04-07
that was exactly what i was going to say... random reboots are very often a motheboard or a ram failure.  i have receintly scrapped a motherboard for just that reason, random reboots.

but you reaching some success with the old powersupply says somthing about the new one.

---

### Post by metol on 2007-04-07
](*,)  Well seconds after I posted my last reply.... boom... reboot.  I really had my hopes up this time.  It had gone over 6 hours without crashing.

Only two things left to try, MB and CPU....  any guesses?  Perhaps I will order both on Monday.

---

### Post by metol on 2007-04-07
hardyn, I saw your message after I posted.  Thanks for the info, I will try a new MB next.

---

### Post by ed-j on 2007-04-07
Graphics Card drivers? :)

---

### Post by jeffathehutt on 2007-04-07
> Sometimes it reboots within minutes, sometimes it can go several hours.

Do the reboots ever happen back to back?  For instance, you turn the computer on, 3 minutes later it reboots, and then 3 minutes after that it reboots again.

---

### Post by dwblas on 2007-04-07
> went back to my original power supplyStay with the new power supply.  If I read your post correctly, everything was OK until you went back to the original power supply

---

### Post by metol on 2007-04-07
Thank you all very much for your replies, they have been very helpful.  To answer some of the questions that you had:

- Graphics drivers: tried no driver, drivers in symantic and the latest drivers via Envy.  All resulted in crashes.  Even tried a different card.  Also tried using the MB's internal graphics card in VESA mode. I'm pretty confident this has nothing to do with video.

- Both power supplies I tried produced the same result (random crashes).  Both power supplies were brand new (Antec).  So, I'm pretty confident it is not a power supply issue.

- I have had a reboot occur back-to-back a few times.  Usually it will go an hour or so before a reboot occurs.  Sometimes it will go several hours and sometimes within a few minutes of login.  It behaves very randomly.

A bad motherboard makes since, but the CPU could be an issue as well.  As I mentioned earlier, it "almost" always occurs during processor activity... usually when I'm scrolling or with a mouse click.  But this could just be a coincidence.

---

### Post by jeffathehutt on 2007-04-07
In your first post, you say the motherboard and cpu are new.  Does that mean you just bought them and your computer started rebooting, or the computer was rebooting before you bought them?

I have a feeling your problem is caused by power issues.  Since you got a new power supply, it is unlikely to be the culprit.  I wonder about your electrical service though.  If you are getting brownouts or surges from the power company, buying a new power supply wouldn't fix it.

Before you go out and buy a new motherboard, try moving the computer to a different circuit in your house, maybe one that doesn't already have a high load on it.  Also, see if you can identify any kind of pattern related to major appliances.  For instance, your computer reboots right after the air conditioning turns on.  If that is the case, buying a small UPS should fix the problem for you.

Of course I cannot diagnose computer problems over the internet, but it could save you money if it turns out to be something so simple.

---

### Post by metol on 2007-04-07
Excellent suggestion Jeff.  I upgraded an old P2-450 box.  I pretty much replaced everything except for the case, cd-drive, and hard drives.  PSU/MB/CPU/Video Card/Monitor, etc are all new. The PSU on the P2-450 was only 125W, so it was not drawing much current.  My power strip is quite old... that could be it.  That did not occur to me.  I'm at my in-laws house now and I will try as you suggested when I get home.

The old system was running Win98 and it never had problems, but aqain probably only drawing half the current.

Thank you all, you have been very helpful.

---

### Post by eljavi99 on 2007-04-11
I have the same problem, but i have dual boot (windows and Linux), 
on windows everything works fine . i was trying different ways to solve the problem but i couldn't yet.
 
I think that the problem cut be some incompatibility with the MB (PM8PM-V) and Ubuntu.

---

### Post by Trailer_Lizard on 2007-04-11
You could have the same problem as I do every so often.  I have an old Dell with a Nvidia like yours.  Have you just happened to of updated the Linux kernel header files? If you have then your Nvidia drivers probably need reinstalling.  It is something to do with X-windows which cause seemingly random crashes.  Someone with more technical knowledge would probably be able to explain it better.  On mine it was caused by the screen saver running Open GL screen savers.  You can test it by opening one of the 3D screen savers in preferences.  If it causes a crash then you have found the problem.

If it is this then you could use the nv drivers with ubuntu, but you're probably better using the correct ones for your card from the Nvidia website.  There is also a script called ENVY that apparently works well.

---

### Post by metol on 2007-04-12
eljavi99,  Interestingly enough I was using the same MB as you!!!  An MSI PM8PM-V and it rebooted in an almost random pattern.  I just received a new motherboard today, a PC-Chips P4M800 pro and it has been running several hours without any crashes.  Hopefully it is not too early to declare victory.  I will keep you posted if anything goes wrong via this thread.  I picked this MB up cheap at Newegg.com for ~$42.  I'm still keeping my fingers crossed that this will solve the problem.  This has been a rather frustrating ordeal to say the least.  On newegg, someone running XP was reporting an identical reboot problem with the PM8PM-V.

Trail_Lizard, I have not had any problems with the OpenGL screen savers.  I even tried running on the internal video card in VESA mode and still had the spontaneous reboot problem.  I'm fairly confident that my reboots were not a result of the nvidia card since it was completely removed from the system when it crashed.  I am running the latest drivers installed via Envy though.

---

### Post by david_kt on 2007-04-12
> **metol said:**
> eljavi99,  Interestingly enough I was using the same MB as you!!!  An MSI PM8PM-V and it rebooted in an almost random pattern.  I just received a new motherboard today, a PC-Chips P4M800 pro and it has been running several hours without any crashes.  

When you are using this new motherboard, please try to see whether it has direct rendering:

```
glxinfo | grep render 
```

If it is no, you will need to install video driver. Below method work for me:

[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

DK

---

### Post by metol on 2007-04-12
It appears direct rendering is active, here is the output from "glxinfo | grep render":

[I]direct rendering: Yes
OpenGL renderer string: GeForce FX 5200/AGP/SSE2[/I]

---

### Post by koanhead on 2007-04-12
I had this happen recently with my spare computer, and then again with my main one after I rebuilt it. My current computer is a bunch of junk crammed into an open case with inadequate standoffage so that if it gets bumped slightly it will reboot "spontaneously". I could easily fix this by moving it into another case but I'm waiting until I have the rest of the parts I want to rebuild it. The spare has a faulty power supply, as has been pointed out as a probable culprit by others in this thread. 
     My 10 bits: If the machine was recently rebuilt open it up and check all connections, both mechanical and electrical, to the motherboard. The board should be adequately supported *away* from the metal base plate with plastic standoffs in all available mounting holes, and screwed down nice and tight wherever there's a place for a screw. The power supply connections should be tight. The base plate should contact the rest of the case's chassis in such a way that there's continuity between them, i.e. all the metal parts of the case should be equal to one big "ground" when everything is hooked together.
      If both power supplies you've been using are new then I suspect that your case is at fault, or that the power supplies are / were improperly mounted. 
      Also you could have a loose screw rattling around in there. Eh... The computer case, I mean 8`)

---

### Post by nudnik on 2007-04-13
It sounds like a bad motherboard, specifically dodgy capacitors. Other components of the board might cause this as well, but the behavior is identical to that caused by faulty capacitors. I'll bet your new, cheap (I like cheap, cheap is always good) MB will do the trick.

---

### Post by metol on 2007-04-13
> **nudnik said:**
> It sounds like a bad motherboard, specifically dodgy capacitors. Other components of the board might cause this as well, but the behavior is identical to that caused by faulty capacitors. I'll bet your new, cheap (I like cheap, cheap is always good) MB will do the trick.

I think you are absolutely correct nudnik.  It is day 2 with the new motherboard and I have not had the slightest glitch.  Thank you all very much for your help, it is _greatly_ appreciated.

Now that the Linux system is up and running smoothly, my kids will not let me on it.  I am reduced to using the WinXP system at the moment...#-o

---

### Post by sirius10 on 2007-06-03
Hi! I think I have the same problem. 
I used Dapper for almost a year now. Everything was perfect till last few weeks when it began to restart by itself for no reason apparently.  Didn't paid much attention cause I wanted to upgrade to Feisty anyway. I made a fresh install from a liveCD with no problems and thought everything was OK. But the system started to reboot in Feisty as well. I have dual boot with XP, every OS with its own HD., no problem with XP but Feisty drives me crazy. Doesn't matter whether i browse the net or work on my documents, the system just restarts after few minutes or more. 
I didn't made any change in the system configuration for more than a year so what could be the problem? It worked perfectly in Dapper until recently. What could have changed in the last four weeks or so for this to happen?
Please, help!

---

### Post by southernman on 2007-06-03
> **metol said:**
> I think you are absolutely correct nudnik.  It is day 2 with the new motherboard and I have not had the slightest glitch.  Thank you all very much for your help, it is _greatly_ appreciated.

Now that the Linux system is up and running smoothly, my kids will not let me on it.  I am reduced to using the WinXP system at the moment...#-o
It's my hope metol the new mobo was indeed the problem. I can feel your pain since just going through this with my dad's computer.

I went through every part of his box with a fine tooth comb... apparently the comb was missing a tooth. It turns out the problem was a bad stick of ram. One of the gold tabs had loosened and I just happened to notice it on the 14 hundredth attempt at diagnosing the problem. Removed the ram and his box has purred like a kitten every since.

I can't tell you how many times I used the excuse to him... "It's that bloated OS your running... you really should switch to Linux!" ;)

---

### Post by robin on 2007-06-03
I have had this happen and found out that it was caused by bad capacitors.  Look at the capacitors on the motherboard or in the power supply (they are the round things like a little can) and see if they appear bulged at the top or have any brown goop coming out of them.  If you do an internet search for bad capacitors, you'll find the whole story about how there were a lot of bad capacitors made because of some imperfect industrial espionage.

---

### Post by benner on 2007-06-04
i'm coming in here a bit late but in case anyone is still on this thread, i have the same problem and it turned out to be a crappy case and static electricity.  i live in china and a lot of cheaper cases here apparently have the same problem.  if my cat comes anywhere near the machine it suddenly reboots.  putting the tower on a rubber surface helped a bit.

---

