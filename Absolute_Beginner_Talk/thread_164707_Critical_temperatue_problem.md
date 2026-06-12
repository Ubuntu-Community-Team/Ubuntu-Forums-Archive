---
title: "Critical temperatue problem"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Mrtn on 2006-04-23
The moment I start using lots of resources the computer shuts down stating that the temperature exceeds 60 degrees celsius. I already tried turning ACPI off in grub, but then my system did not boot anymore. Being the newbie that I am, I reinstalled ubuntu and lost all my stuff =/

Is there any other way to disable ACPI? Or to change the temperature when it shuts down?

---

### Post by jazzmuzik on 2006-04-23
It sounds like the computer is legitimately warning you of a problem and your solution is to find a way to ignore that information. I wouldn't ignore a heat problem.

Are you on a laptop or desktop? My experience is with a desktop.

Your CPU fan may be going bad. The CPU's heat sink may be full of dust. I recently cleaned my fan and cpu. I also found that removing all the old silicone gel between the CPU chip and heat sink and applying new gel ($2 at Radio Shack) was absolutely critical to disperse heat. That old gel gets crusty over time.

The cpu fan should spin super easily. If it gets bumpy or doesn't move easily it's a sign that you need a new fan. 

I use a cheap paint brush to clean out the dust. Some people use compressed air and blow the dust out.

---

### Post by Bartender on 2006-04-23
Mrtn -
My first guess would be the CPU heatsink fan died.  (Whoops, too late - hi jazz)

If the fan is still spinning, is it hopelessly clogged with dust bunnies?  Could the heatsink have come partially unclipped from the CPU due to a severe jarring of the PC or from someone ;) wrestling around inside the case?

Can you dual-boot to Windows and run Speedfan or some other temp-monitoring program?  If not, can you bring up System Monitor in Ubuntu and verify that the CPU is running full-tilt constantly til it shuts down?  There's a lotta stuff I don't know but never heard of ACPI causing run-away CPU temps.

---

### Post by Mrtn on 2006-04-23
[QUOTE=Bartender]Mrtn -
My first guess would be the CPU heatsink fan died.  (Whoops, too late - hi jazz)

If the fan is still spinning, is it hopelessly clogged with dust bunnies?  Could the heatsink have come partially unclipped from the CPU due to a severe jarring of the PC or from someone ;) wrestling around inside the case?

Can you dual-boot to Windows and run Speedfan or some other temp-monitoring program?  If not, can you bring up System Monitor in Ubuntu and verify that the CPU is running full-tilt constantly til it shuts down?  There's a lotta stuff I don't know but never heard of ACPI causing run-away CPU temps.[/QUOTE]

Well, I checked the temp in bios so it is correct. Is a temperature of 60 degrees really bad for your CPU?

I just wanna disable ACPI if its possible and its not bad for the CPU.

Thanks for the help guys!

At the moment I changed my fan settings in the bios and while it is making a lot of more noise it hasn't crashed on me so far.

---

### Post by Bartender on 2006-04-23
Mrtn -
This is just my opinion.  
Heat is the enemy.  The chip manufacturers try to make it sound like you're OK right up to the point that the CPU goes into alarm, but that's bull.  Cooler is better.  Your PC will be happier and your parts won't die an early death from the heat/shrink cycles.  To me, no different than running your car with the radiator half empty and the temp needle at the redline.  Car still running?  Yeah.  Is it going to last longer this way?  No.

BIOS isn't a guarantee that temps are correct (still relying on the same thermal probe) but it probly is.  If this is a desktop I'd open up the side and point a room fan in there, see what happens.  Failure of thermal probe seems to be pretty rare but that'd be one way to check.  If it's still overheating with room fan then the CPU heatsink definitely needs to be cleaned and thermal paste re-applied (as jazz said) then try again.   
  
As jazz asked, we talking a lappy or desktop?

I'm not really up on ACPI.  The most I've ever done is tweak with power mgmt. in Control Panel (Windows)

---

### Post by Bartender on 2006-04-23
Mrtn -
Is this what you did in grub?

[http://ubuntuforums.org/showthread.php?t=135511&highlight=acpi+configure](http://ubuntuforums.org/showthread.php?t=135511&highlight=acpi+configure)

---

### Post by futz on 2006-04-23
[QUOTE=Mrtn]Well, I checked the temp in bios so it is correct. Is a temperature of 60 degrees really bad for your CPU?

I just wanna disable ACPI if its possible and its not bad for the CPU.

Thanks for the help guys!

At the moment I changed my fan settings in the bios and while it is making a lot of more noise it hasn't crashed on me so far.[/QUOTE]
60 degrees under load is high, but not dangerous yet. Dangerous starts at 70ish. I assume this is an Intel P4 Prescott? Socket 775? Their stock coolers are totally inadequate to deal with the heat that chip makes.

Intel rates their cpu's for up to 90 something, but I would never want mine to exceed around 60 degrees max at **extreme** load.

If the Prescott *is* what you're running, I recommend an aftermarket cooler. The best (it's HUGE!!!) air cooler, IMHO, is the Thermaltake Big Typhoon
[http://www.thermaltakeusa.com/product/cooler/retail/cl-p0114/cl-p0114.asp](http://www.thermaltakeusa.com/product/cooler/retail/cl-p0114/cl-p0114.asp)
It keeps Prescotts as cool as AMD 64's (real cool) and does it while making virtually no noise. That big 120mm fan spins slow, so it's quiet.

There are other coolers that do a great job too. I'll just mention a couple I'm familiar with here. 

The Coolermaster Hyper 48 is very good
[http://www.coolermaster-usa.com/Products.aspx?pid=912](http://www.coolermaster-usa.com/Products.aspx?pid=912)

Zalman has some very good coolers. Their big round CNPS7700-Cu "flower" cooler is good, and very quiet, but has clearance problems on some boards.

And, as mentioned before, it could be just gobs of dust or a failing/failed fan.

---

