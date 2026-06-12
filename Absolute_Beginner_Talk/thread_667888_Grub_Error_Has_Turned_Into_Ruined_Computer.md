---
title: "Grub Error Has Turned Into Ruined Computer"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by Squizz on 2008-01-14
I've recently had some problems with Grub errors.  Error 17 appeared to be just a loose SATA connection, but on my next reboot I received a new error - Error 21.

I assumed that this error could be fixed by playing with my connections again, but to no avail.

There was a bit of light when Ubuntu then started to load, but failed at the loading bar bit.  Loads of text came up, which ended up with the message "kernel panic - hardware error" or something similar.

Attempts after this were me t with "cannot find operating system" or similar.

I've checked my BIOS, and now I cannot see the hard drive that used to have Vista on it - but I can see the one that has Ubuntu on it, although Ubuntu refuses to load.  I also cannot see my CD rom in the BIOS menu anymore either.

So now basically I cannot do ANYTHING as the BIOS isnt recognising my CD rom, I don't have a floppy drive, an my MB won't let me boot from a USB key (to my knowledge - it's an ASUS A8N-SLI) and Ubuntu wont boot from its home.

Any idea on how I can even begin to fix this mess?

---

### Post by Moop on 2008-01-14
You didn't say if you ever had Ubuntu and Vista successfully dual booting but if you did then it sounds like you have a hardware problem. Ubuntu isn't going to make your cd player disappear from the bios. 

Check all the connections again and even try another cd player if you have one. If you think the bios maybe corrupted you can reset that to defaults per the manual. Sometimes a bad harddrive or cd player can make strange things happen. If you have 2 harddrives unplug one at a time and try booting. Do the same with your cd drive and try and see if you can find the problem.

---

### Post by Squizz on 2008-01-14
Before today I have been able to dual boot for the past 2 months at least.

I've tried 2 quad speed drives (as I dont have any other spares) and neither of them were detected.  The jumpers were set to master too btw)

I also tried several combinations of Hard Drive 1/2/CD Rom plugged in and didn't have any decent results.

I'll have to have a look through the motherboard manual to see about resetting the BIOS, but are there any other possible solutions anyone can think of?

---

### Post by Squizz on 2008-01-14
So far:

I'm about to go to bed, but my plan of action for tomorrow is thus:

- Download the most recent BIOS files from asus & put them on a floppy.
- Remove a floppy drive from another computer & install that in my current pc
- somehow find a PCI graphics card, as the wire I need to power up a floppy drive also powers my graphics card - so it's either have a floppy or have a monitor at the moment.
- Use the floppy to upgrade my BIOS
- Hope that the bios was the problem to begin with :O

If anyone can suggest an easier solution that might work, I'd be very grateful to hear it, as this looks like it's going to be a ballache - and I'm only going to bed now as I'm sure that if I carry on then I'm going to throw the machine out of the window.

I'll check back here before I do anything in the hope that one of you lovely people can help me me:)

---

### Post by stalkingwolf on 2008-01-14
The jumpers were set to master too btw)

Your win drive should be set to master or Cable select (CS) and plugged into the primary plug.
Ubuntu drive should be set as Slave or CS and plugged into the secondary plug.   

Usually you can remove the MB battery for about 1 minute and it will reset the bios to the original default
settings.  you shoujld also be able to do it from the setup area.

---

### Post by Ex-windows on 2008-01-15
In Addition to stalkingwolf's suggestion  maybe you could then  try  the Super grub disk to get ubuntu  or vista to load.. Not sure if it will work in your situation but worth a try.. It worked for me a while back. Good luck

---

### Post by Squizz on 2008-01-15
OK - I got a floppy installed and did the following.

Updated the BIOS - no change
Removed the battery - no change
Checked all the jumpers - all correct
Run super-grub from a floppy....

I can get my regular GRUB up, but I have to use "live swap" to male it work.

When Ubuntu tries to load then, the loading bar goes up by a fraction, then a black screen of text comes up, which ultimatly ends with;

```

CPU 0: Machine Check exception
TSC 5a9b4fa7cf
This is not a software problem!
Run through mcelog --ascii to decode and contact your hardware vendor
Kernal panic - not syncing: Machine check

```

Oh dear.....

Any help?

---

### Post by philinux on 2008-01-15
Can you get into the bios ok. And does it complete the POST without any warning beeps?

---

### Post by Squizz on 2008-01-15
Yes, I can get into the BIOS and there are no beeps at all.  If I leave it to its own devices, then it (now) gets to my old GRUB, but none of the commands work.

---

### Post by philinux on 2008-01-15
Shouldn't there be one short beep to inform that POST was ok?

---

### Post by Squizz on 2008-01-15
This one has never beeped on startup....

---

### Post by philinux on 2008-01-15
Found this OOOOH  ARRRRGH

[http://en.wikipedia.org/wiki/Machine_Check_Exception](http://en.wikipedia.org/wiki/Machine_Check_Exception)

Not good.

Could be the ram gone west?

---

### Post by Squizz on 2008-01-15
Doesn't look at all promising does it.

I've spent hours already trying to fix it, but it looks like it might be screwed :(

Do you think replacing the motherboard would help, or would I need to to somehow diagnose which bit of hardware is being **** and replace that?

---

### Post by Squizz on 2008-01-15
> **philinux said:**
> 
Could be the ram gone west?

Just tried booting with both sticks seperatly - no joy.  I'm guessing if the ram had died then it would only be one of them.

Exactly the same error each time.

---

### Post by Yoke &amp; Chung on 2008-01-15
Is your RAM dual channel type? If so, pulling out 1 stick wouldn't work.

---

### Post by Lord DarkPat on 2008-01-15
can u boot from livecd? maybe you could try that and reinstall.

---

### Post by Squizz on 2008-01-15
It is dual channel, but it worked for about a year with only one stick in there.

I think I'm just going to give up on it for now and use it as an excuse to upgrade.

---

### Post by Yoke &amp; Chung on 2008-01-15
> **Squizz said:**
> It is dual channel, but it worked for about a year with only one stick in there.

I think I'm just going to give up on it for now and use it as an excuse to upgrade.

:) It sure looks like MB problem if RAM is ok. Just to be sure, unplug your HD and try it on another computer and see if it boots properly.

---

### Post by mister_p_1998 on 2008-01-15
Sounds to me like you were dual-booting with two hard drives (correct me if Im wrong)
with probably Vista on your first drive and Ubuntu on your second. If your first drive has either died or become unplugged from the power or data connections it would do this. Your Grub menu will be on your 1st hard disk, so if this dies or becomes detached you cant choose ANYTHING to boot from as the Grub hasnt been loaded. Its either get the vista drive working or replaced, and then restore you Grub on the Vista drive.

---

### Post by Squizz on 2008-01-15
> **mister_p_1998 said:**
> Sounds to me like you were dual-booting with two hard drives (correct me if Im wrong)
with probably Vista on your first drive and Ubuntu on your second. If your first drive has either died or become unplugged from the power or data connections it would do this. Your Grub menu will be on your 1st hard disk, so if this dies or becomes detached you cant choose ANYTHING to boot from as the Grub hasnt been loaded. Its either get the vista drive working or replaced, and then restore you Grub on the Vista drive.

Yeah, you've got that right.  I've a sneaking suspicion that the Vista drive (which was the original hard drive) has died completely.  Would this account for the bios not recognising the DVD drive either?  If the hdd is damaged beyond repair, is there any other way to get the thing up and running?  I have old hard drives that I could use a temporary thing (just to get it working) but would that help?

---

### Post by phidia on 2008-01-15
> **Squizz said:**
> Yeah, you've got that right.  I've a sneaking suspicion that the Vista drive (which was the original hard drive) has died completely.  Would this account for the bios not recognising the DVD drive either?  If the hdd is damaged beyond repair, is there any other way to get the thing up and running?  I have old hard drives that I could use a temporary thing (just to get it working) but would that help?

It can't hurt to try an old (known working)  hard drive just to check if that is the problem. 
On IDE/ATA systems depending on how your optical/dvd drive is connected then yes the master dying could cause the bios to fail to see the dvd. 
I would also check the connections to the mother board and the cables themselves-those old ribbon cables have been known to fail.

---

### Post by Squizz on 2008-01-15
I tried putting the original hard drive (Vista) into a windows machine (as a slave) and it gave the blue screen of death and wouldn't load - so I guess that hard drive is dead.

I tried plugging in an old hard drive, but the BIOS doesn't recognise it so thee's no change.

I can use super-grub to attempt to load my ubuntu from the sata hd by changine the root from (1,0) to (0,0) by the way.

---

### Post by bumanie on 2008-01-15
If you have some old hard drives around, it would be a good idea to try one of those (if you know they work). If one of them works and allows the computer to boot, it will confirm your suspcions about the original hard drive dying.

---

### Post by Squizz on 2008-01-15
I've tried with the only 2 other IDE hard drives I have lying about and neither of them were recognised by my machine.  I don't think I have a ribbon that will fit onto my motherboard other than the one that says "floppy drive" on it - will they all be the same or are they specific?

---

### Post by dstew on 2008-01-15
There may be information on exactly what caused the machine exception in the file /var/log/mcelog, if you can get to it to read it.

---

### Post by Squizz on 2008-01-15
To be honest I think that's a bit beyond me.  I have not got a clue if or how I could get a terminal to run at the moment (apart from the grub prompt which I got to run accidentally earlier)

---

### Post by bumanie on 2008-01-15
> **Squizz said:**
> I tried putting the original hard drive (Vista) into a windows machine (as a slave) and it gave the blue screen of death and wouldn't load - so I guess that hard drive is dead.

I tried plugging in an old hard drive, but the BIOS doesn't recognise it so thee's no change.

I can use super-grub to attempt to load my ubuntu from the sata hd by changine the root from (1,0) to (0,0) by the way.

Have you tried to boot with super grub disc yet? If you can get into ubuntu you could then look at mcelog as suggested. 

I don't think I have a ribbon that will fit onto my motherboard other than the one that says "floppy drive" on it - will they all be the same or are they specific?
 
As far as I know, a floppy drive ribbon is not compatible with a hard drive.

---

### Post by Squizz on 2008-01-15
> **bumanie said:**
> Have you tried to boot with super grub disc yet? If you can get into ubuntu you could then look at mcelog as suggested. 

I don't think I have a ribbon that will fit onto my motherboard other than the one that says "floppy drive" on it - will they all be the same or are they specific?
 
As far as I know, a floppy drive ribbon is not compatible with a hard drive.

No, cannot get into Ubuntu at all, even with the Supergrub disk it only attempts to load my Ubuntu but fails during load.  If I try then I get the fatal error that I'm trying to get around.  I think the only way to look at the mcelog would be to use gedit from the command line if I can somehow mount the hard drive - I have no clue how to do that from the grub menu though.  If anyone knows them I'm willing to try though!

I'm about to completely dismantle my PC and rebuild it in the hope that I've knocked something loose or something now though.

---

### Post by dstew on 2008-01-15
You can try to view the mcelog using grub only, no need to have Ubuntu up. If your Ubuntu partition is the first on the first disk, then the grub command would be```
grub> cat (hd0,0)/var/log/mcelog
```Grub can do a lot of things besides boot. Try```
grub> help --all
```to see the commands.

---

### Post by Michl on 2008-01-15
Very helpful thread on diagnosing a problem.  Thanks!

---

### Post by Squizz on 2008-01-17
I gave up and bought a new motherboard - only to discover that it was the IDE ribbon that wasn't working :(

Ah well, at least I got an upgrade out of it :)

---

