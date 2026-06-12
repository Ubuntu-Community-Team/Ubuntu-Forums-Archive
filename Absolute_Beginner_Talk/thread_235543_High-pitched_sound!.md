---
title: "High-pitched sound?!"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-08-13
Yeah, this is really weird and it just started today. I booted up Ubuntu and was browsing the net + playing music; all of the sudden this really loud and high-pitched squeaking/scratching sound came from the inside of my computer (the tower?). It's driving me crazy and I think it could be harmful to my PC. I tried unplugging my external HD ('cause sometimes my external HD would do this for a sec), but it didn't work. Shutting down seems to make it stop, and it doesn't start again until I get to the Ubuntu splash screen (and the nVidia splash screen). I unplugged my monitor from my video card in the back, and the inside of my tower seemed to settle down, and the sound stopped. Right now the sound isn't constant, but like every other sec a light, high-pitched, squeak/scratch comes from the tower. How do I fix this?

I also opened up my tower and blew dust of stuff, but I don't think it helped.

This noise is driving me crazy!

---

### Post by em3raldxiii on 2006-08-13
The most common cause of this *by far* is the failure of one of your fans.  There are a couple of things you can try:
 
1.  Unplug your chassis fans one at a time and boot your system to see which fan might be causing the problem.
 
2.  When the system is running and the squeel is audible, gently slow down the CPU fan by touching it's center with a pencil eraser.  Key word is GENTLY.  If you notice a definite change in the sound, you have your culprit.
 
If it is one of the fans, you will be happy to know they are super cheap (less than $5) from your computer retailer (or NCIX.com in Canada), and they are easily replaced.  When a fan fails (and it is super common), you might have over-heating problems occur until you get adequate air-flow into your case/heatsink again.
 
Let us know what the results of this little test are :D

---

### Post by kbsuperstar on 2006-08-13
Hmm.. it seems I can't get access to the two fans inside of my tower.

On the outside, there is a metal cage with little holes that a pencil won't fit through, and on the inside, one has a plastic covering and the other is encaged in metal. I'll take some pictures and post.

[IMG]http://xs104.xs.to/xs104/06320/fans_inside.jpg[/IMG]

[IMG]http://xs104.xs.to/xs104/06320/fans_outside.jpg[/IMG]


Ha... but right now I don't hear the sound anymore :-k If it happens again I'll see if I can stop the fans

---

### Post by em3raldxiii on 2006-08-13
The one near the top is your power supply's fan, and it's not advisable to stick anything in there because of the very high possibility of electric shock, even when powered down. The other one (covered with the green air-duct) is your chassis fan and it will also likely have a fan on top of the CPU heatsink (which should also be under the air-duct). I see that you might be able to slow the chassis fan from the back of the computer (the one in the bottom picture with the grid of small holes) to detect a change in sound. You should also be able to temporarily remove the air-duct, it might just take some figuring to get it off. Could be a couple of screws, but more likely is just a clipping mechanism somewhere. It won't harm the computer to run without the air-duct.
 
Alternatively, you should be able to find a thin 2-wire cable coming from the various fans that you can unplug from the motherboard. If you unplug the CPU fan, it may prevent the computer from booting, depending on your motherboard. It's a safety feature to avoid heat-related failure.
 
With it being intermittant like you are suggesting, it really seems like a fan issue. While it might be other things, I am personally quite convinced of the fan problem. It may occur at certain temperatures or at certain fan-speeds as well, so keep a critical eye on the current system circumstances when the squeel occurs. Ambient temperature, system load, CPU temperature, etc. Anything you can identify might help narrow down the problem.
 
Alternatively, you could just replace the fans and see if that works - they're cheap ;)
 
If you suspect that it's the fan inside the power supply itself, you may want to purchase a new power supply instead of messing around with the unit itself - they are not as easy to work on as the rest of your computer, can be dangerous to work on (because the capacitors can hold a dangerous amount of electrical charge for hours after disconnection from the power outlet), and a new (high quality) power supply could outlast this and your next computer (if you want to buy a new one, get an Enermax or an Antec, but this could be an entirely new thread)

---

### Post by kbsuperstar on 2006-08-13
Wow, thank you so much!

If the problem occurs again, I'll be sure to check out the chassis fan.

---

### Post by kbsuperstar on 2006-08-15
Hey, so I bought a new chassis fan and hooked it up. It seems to have been going good, but this morning when I booted up, the same thing happened again. I tapped on cage over the chassis fan and it stopped after some trying. Any idea why this keeps happening?

The noise is like "eeeeeeeeee"

---

### Post by Frank Golden on 2006-08-15
> **kbsuperstar said:**
> Hey, so I bought a new chassis fan and hooked it up. It seems to have been going good, but this morning when I booted up, the same thing happened again. I tapped on cage over the chassis fan and it stopped after some trying. Any idea why this keeps happening?

The noise is like "eeeeeeeeee"
I bet you have a bad electrolytic capacitor in your Power Supply Unit. They can make noise when going bad. Probably a big filter cap. When you hear again look and listen but don't touch the PSU.
If sound is coming from there and it ain't fan bearing you got a bad cap. Be careful dangerous voltages in PSU.

BTW, post probably belongs in UbuntuForums-Hardware Help.
Don't sound like software related.:)

A new PSU might be in order. Hopefully your tower won't need a
proprietary PSU. Some makers do that to make sure you buy their
high priced parts.

---

### Post by em3raldxiii on 2006-08-16
This is indeed a possibility.  I've personally replaced a number of motherboard capacitors, but I don't think I'd have the brass cahones to change a capacitor in a power supply.  And for the cost of a high-end capacitor, you could probably replace the whole powersupply (LOL).
 
So, as Frank says, if you can verify that it's not the power-supply fan, then you quite possibly have a problem with a bad capacitor.

---

### Post by Frank Golden on 2006-08-16
> **em3raldxiii said:**
> This is indeed a possibility.  I've personally replaced a number of motherboard capacitors, but I don't think I'd have the brass cahones to change a capacitor in a power supply.  And for the cost of a high-end capacitor, you could probably replace the whole powersupply (LOL).
 
So, as Frank says, if you can verify that it's not the power-supply fan, then you quite possibly have a problem with a bad capacitor.As I said earlier hopefully the PSU can be replaced with a standard aftermarket one.
If it can get one with more power than the one you have now. That way in
case you want to update Motherboards, CPU's or Video cards in future
you will have more power already. At the very least make sure it is the same power rating.

---

### Post by em3raldxiii on 2006-08-16
Well, from what I can tell from the images you've posted, it looks like you have a standard ATX power supply, so you shouldn't have too much difficulty getting a replacement.
 
If you do decide to pick up a new one, you have a number of options.  I personally buy quite a bit of hardware from a website called NCIX.COM - they sell both in Canada and in the US.  If you are elsewhere you will have to look it up.
 
As far as power requirements, I recommend looking for something with 400W or higher output; there are a number of other options to cinsider as well - modular cables, fancy lights, and directional fans.  Typically I recommend a PS that pulls air from the bottom of the unit and out the back.  Larger fans are quieter than small ones because they run at lower RPM.
 
If you are interested, I can make a number of recommendations for you, and I am sure that Frank will be willing to weigh in on the matter as well.
 
Cheers!

---

### Post by Cave Dweller on 2006-08-16
It's funny, but my situation is almost the reverse.

I have an older pc running XP, and for about a year now, my cpu fan has been intermittently noisy.  I kept meaning to replace it, but never got around to it.  Eventually the fan won, and I would hardly notice it burring unless somebody mentioned it.

I inherited a second hard drive, and installed Dapper, now I'm dual boot, and giving linux a try.  I rather like it, but I don't know my way around, so I've been browsing quite a lot over the last week, and I've been using Dapper almost exclusively.

Something was bothering me, and it took a couple of days to work it out.  My noisy fan wasn't noisy anymore.  I opened the box up to check, and the fan is working.  I have been actively listening for this for the past 3 or 4 days, and it's still quiet.

So I was wondering if there is some difference between the two operating systems that can explain this, or if it's just a fluke.  I was thinking that maybe it's related to processor temperatures.

More of a curiosity than an issue, but I would appreciate any input.

---

### Post by em3raldxiii on 2006-08-16
hi Cave Dweller - love the username ;)
 
Okay, I am by no means the authority on this subject, but I DO remember reading another thread about this somewhere - though not specifically on this topic.  Basicly the gist of it was that Ubuntu (or perhaps Linux in general) has an advanced way of managing processor usage by issuing a "stop" command to various processes when they are not active, thereby preventing wastage of resources and consequently power.  The positive side-effect would be that if your motherboard has any kind of temperature-initiated fan-speed control, you would naturally expect the fan to either run at lower RPM or perhaps even stop under some circumstances.
 
Now you've piqued my curiosity and I'm going to have to see if I can get more info about this.  It is my understanding that Windows doesn't do this, but perhaps Vista will.  The new 65 nm core Intel processors would probably really display super-low power usage under Linux I suspect.  When AMD finally comes out with a 65 nm core I'd be willing to bet we'll see an even more dramatic effect.  Combined with a high-end motherboard (such as those by Asus) that has heat-pipes and advanced temperature controls ... consumer-level computers might become silent without any extreme financial outlay.  Bla bla bla ... there I go again. ;)

---

### Post by kbsuperstar on 2006-08-16
Hey, thanks for tipping me off about the PSU, but how can I check to see if it is actually the PSU making the sound? Also, how do I replace it safely and preferrably affordably :)

You said you had recommendations? I'd love to here 'em! :

THANKS!

---

### Post by Frank Golden on 2006-08-16
> **em3raldxiii said:**
> hi Cave Dweller - love the username ;)
 
Okay, I am by no means the authority on this subject, but I DO remember reading another thread about this somewhere - though not specifically on this topic.  Basicly the gist of it was that Ubuntu (or perhaps Linux in general) has an advanced way of managing processor usage by issuing a "stop" command to various processes when they are not active, thereby preventing wastage of resources and consequently power.  The positive side-effect would be that if your motherboard has any kind of temperature-initiated fan-speed control, you would naturally expect the fan to either run at lower RPM or perhaps even stop under some circumstances.
 
Now you've piqued my curiosity and I'm going to have to see if I can get more info about this.  It is my understanding that Windows doesn't do this, but perhaps Vista will.  The new 65 nm core Intel processors would probably really display super-low power usage under Linux I suspect.  When AMD finally comes out with a 65 nm core I'd be willing to bet we'll see an even more dramatic effect.  Combined with a high-end motherboard (such as those by Asus) that has heat-pipes and advanced temperature controls ... consumer-level computers might become silent without any extreme financial outlay.  Bla bla bla ... there I go again. ;)
There is a huge thread about the Acer Aspire 5672WLMi notebook
started about 7 months ago by member gmc. It is on these forums (Laptop Support).

[http://ubuntuforums.org/showthread.php?t=121125](http://ubuntuforums.org/showthread.php?t=121125)


It basically
has become a clearing house for Ubuntu related issues with this model notebook. Somewhere in there is a discussion of high pitched whines coming from this notebook at certain times when running on battery. It is related to power management settings.
Maybe that is what you are refering to. I watch this thread because I use the same notebook.

---

### Post by Frank Golden on 2006-08-16
:) > **kbsuperstar said:**
> Hey, thanks for tipping me off about the PSU, but how can I check to see if it is actually the PSU making the sound? Also, how do I replace it safely and preferrably affordably :)

You said you had recommendations? I'd love to here 'em! :

THANKS!
I don't have any experience with replacing PSU's (I'm a laptop guy). Here's a link to some helpful info though.

 [http://www.hardwaresecrets.com/article/362](http://www.hardwaresecrets.com/article/362)

I got this by googling "replacing computer PSU". First hit.
You probably don't need any fancy lights or other bells and whistle's. Just a well made PSU from an established company.
400 watts is a good starting point. You need to know your computer's form factor. As em3raldiii noted it looks like you have an ATX tower. Google your make/model and see if you can come up with info on your case. 
Check out this site for more info.

[http://www.directron.com/psu.html](http://www.directron.com/psu.html)

Be careful, unplug power cord before working on your computer.
The PSU itself converts 110v A/C or if in Europe 220v A/C
houshold power to various D/C voltages your computer needs/uses.
The input voltages can be lethal. 
If you feel like you are over your head on this take it to a repair center. Don't know where you live but if the U.S. there should be a Best Buy near you.

Personally I would feel quite comfortable doing something like this. It is well within the skills of most people, provided
you can follow instruction and know which end of a screwdriver to hold.:D

---

### Post by em3raldxiii on 2006-08-16
First off, if you have a "standard" case (one that isn't shaped oddly or particularly small), you won't have any difficulty.  If you have a "small" case - they often refer to these as MicroATX or MATX (common among entry level HP and Compaqs) - you might have to get a PSU that is fitted for MATX, but most MATX cases still take standard PSU's so you should be okay.  

As to whether it is "truly" making the sound or not, you'r going to have to watch and observe quite a bit.  Listen carefully to where the sound is emanating from; tap the computer when it happens (gently) to see how that affects it; try slowing the fans as mentioned before; try cooling it by opening the side to let in fresh air ... all of these things will help you figure out where it's coming from.  I personally have a number of spare PSUs laying around that I can use to test my own equipment ... maybe you have a friend or someone else who does as well?

Actually, changing the PSU in your computer should be very easy.

1.  Power down the machine, unplug all power and move your computer to a handy location such as a table, and let it cool for a few minutes.

2.  Ground yourself to the case prior to work.  Basically, just keeping your opposite hand somewhere on the chassis while you are working is sufficient.

3.  Carefully unplug all of your devices.  Nearly all devices have "particular" plug-in connectors, so you shouldn't have to memorize which power goes where.  Still, it's a great idea to sort-of familiarize yourself with the components.  The large connector that affixes to your motherboard will likely have a small tab or locking clip that you will have to depress in order to pull the plug off.  When pulling the connectors out of your IDE hard drives or CDRoms (called Molex connectors), be careful not to be too agressive; they can stick and be a little frustrating so just take your time and don't get rough.  Your floppy drive power connector may also have a locking clip.

4.  Once all is disconnected, using a **non**-magnetized screwdriver, remove the four screws from the back of the chassis that affix your existing power supply.  Be careful when removing the last screw to support the PSU with your hand, just in case there is nothing else holding it there.  There may also be a screw or some kind of locking mechanism that holds it in place *inside* the case (common among HP computers).

5.  Carefully slide the PSU out of it's position, being extra careful not to jar any of the capacitors or other components on your motherboard.  If it is particularly tight, you MAY have to remove your RAM or your heat sink - if this is your situation, you'd be much better off having someone familiar with computer hardware help you just in case.

6.  Again being careful, position the new PSU, noting the angle and position of the various screws.  Drive in the screws until they are snug - don't overtighten or you will strip the metal.

7.  Re-connect all your devices.  Start with the main power to your motherboard.  There may be more than one connector for your motherboard, depending on the make and model.  You may also have a number of new connectors that you don't need.  Then do your peripherals - some video cards also require an additional molex connector.

8.  Do a quick scan to ensure you haven't missed any devices.  Then you can re-connect it to your desktop and fire it up.


Now, recommended powersupplies.  I typically recommend quite high-end PSUs, but I will include some relatively safe cheap models too.  I am REALLY going to push you toward some of the good ones, though.  There are a couple of things to consider:  Rated wattage is not a very safe indication of power because this is referred to as "peak" output.  So, you could have a really crappy 500W PSU put out less reliable power than a really good 350W.  Also, as mentioned, your PSU divides power into several voltages that have to be within an acceptable range for the various delicate components.  Higher-end PSUs put out very precisely modulated voltages, whereas cheapies may have a greater range of error.  More error = shorter computer life, and potentially unstable computer performance.  One notorious problem is spontaneous shut-downs, and computer hanging during high-load (such as video encoding or gaming).

Okay, ANYTHING by Enermax is going to be relatively safe.  They do have a few dud models, so do some review searching.  Nearly everything by Antec is also good.

Mmm ... I gotta go have dinner, but I will come post about specific Power supplies afterward.  For a price, you should aim between $50 and $90 Canadian.  That would be probably $40 to $70 USD, or perhaps $30 to $60 British pounds.  Those are only guesses (I am in Canada, so exchange rates may vary).

Kay, back in a coupla hours or so.

---

### Post by Frank Golden on 2006-08-16
> **em3raldxiii said:**
> First off, if you have a "standard" case (one that isn't shaped oddly or particularly small), you won't have any difficulty.  If you have a "small" case - they often refer to these as MicroATX or MATX (common among entry level HP and Compaqs) - you might have to get a PSU that is fitted for MATX, but most MATX cases still take standard PSU's so you should be okay.  

As to whether it is "truly" making the sound or not, you'r going to have to watch and observe quite a bit.  Listen carefully to where the sound is emanating from; tap the computer when it happens (gently) to see how that affects it; try slowing the fans as mentioned before; try cooling it by opening the side to let in fresh air ... all of these things will help you figure out where it's coming from.  I personally have a number of spare PSUs laying around that I can use to test my own equipment ... maybe you have a friend or someone else who does as well?

Actually, changing the PSU in your computer should be very easy.

1.  Power down the machine, unplug all power and move your computer to a handy location such as a table, and let it cool for a few minutes.

2.  Ground yourself to the case prior to work.  Basically, just keeping your opposite hand somewhere on the chassis while you are working is sufficient.

3.  Carefully unplug all of your devices.  Nearly all devices have "particular" plug-in connectors, so you shouldn't have to memorize which power goes where.  Still, it's a great idea to sort-of familiarize yourself with the components.  The large connector that affixes to your motherboard will likely have a small tab or locking clip that you will have to depress in order to pull the plug off.  When pulling the connectors out of your IDE hard drives or CDRoms (called Molex connectors), be careful not to be too agressive; they can stick and be a little frustrating so just take your time and don't get rough.  Your floppy drive power connector may also have a locking clip.

4.  Once all is disconnected, using a **non**-magnetized screwdriver, remove the four screws from the back of the chassis that affix your existing power supply.  Be careful when removing the last screw to support the PSU with your hand, just in case there is nothing else holding it there.  There may also be a screw or some kind of locking mechanism that holds it in place *inside* the case (common among HP computers).

5.  Carefully slide the PSU out of it's position, being extra careful not to jar any of the capacitors or other components on your motherboard.  If it is particularly tight, you MAY have to remove your RAM or your heat sink - if this is your situation, you'd be much better off having someone familiar with computer hardware help you just in case.

6.  Again being careful, position the new PSU, noting the angle and position of the various screws.  Drive in the screws until they are snug - don't overtighten or you will strip the metal.

7.  Re-connect all your devices.  Start with the main power to your motherboard.  There may be more than one connector for your motherboard, depending on the make and model.  You may also have a number of new connectors that you don't need.  Then do your peripherals - some video cards also require an additional molex connector.

8.  Do a quick scan to ensure you haven't missed any devices.  Then you can re-connect it to your desktop and fire it up.


Now, recommended powersupplies.  I typically recommend quite high-end PSUs, but I will include some relatively safe cheap models too.  I am REALLY going to push you toward some of the good ones, though.  There are a couple of things to consider:  Rated wattage is not a very safe indication of power because this is referred to as "peak" output.  So, you could have a really crappy 500W PSU put out less reliable power than a really good 350W.  Also, as mentioned, your PSU divides power into several voltages that have to be within an acceptable range for the various delicate components.  Higher-end PSUs put out very precisely modulated voltages, whereas cheapies may have a greater range of error.  More error = shorter computer life, and potentially unstable computer performance.  One notorious problem is spontaneous shut-downs, and computer hanging during high-load (such as video encoding or gaming).

Okay, ANYTHING by Enermax is going to be relatively safe.  They do have a few dud models, so do some review searching.  Nearly everything by Antec is also good.

Mmm ... I gotta go have dinner, but I will come post about specific Power supplies afterward.  For a price, you should aim between $50 and $90 Canadian.  That would be probably $40 to $70 USD, or perhaps $30 to $60 British pounds.  Those are only guesses (I am in Canada, so exchange rates may vary).

Kay, back in a coupla hours or so.
One of the things that make a good PSU is the components used in
construction. The better ones will have higher quality parts.
The electrolytic capacitor(s) that could be your problem is part
of the circuit that filters and smooths out any A/C noise
on your D/C voltage output. The better makers pay attention to this as well as other aspects. It is one of the specs that
are important to choosing a PSU as well as output power etc.

---

### Post by em3raldxiii on 2006-08-16
Okay, some suggestions.

Cheapie:  
[http://www.ncix.com/products/index.php?sku=17076&vpn=ATX-400-PN-B&manufacture=Fortron%20Source](http://www.ncix.com/products/index.php?sku=17076&vpn=ATX-400-PN-B&manufacture=Fortron%20Source) :  This one has relatively good ratings and has a fairly decent track record.  It's not a particularly high quality one, but it would likely do the job.

[http://www.ncix.com/products/index.php?sku=14025&vpn=RS-430-PMSR&manufacture=COOLERMASTER](http://www.ncix.com/products/index.php?sku=14025&vpn=RS-430-PMSR&manufacture=COOLERMASTER) :  This is a lightly better brand than Fortron, but I don't like the ventillation quite as much.

Good quality:
ENERMAX P SERIES EG365P-VE ATX-FMA 24/20PIN 350W POWER SUPPLY W/ MANUAL FAN SPEED CONTROL :  This is an excellent quality power supply, and is a great example of a 350W PSU that has enough guts and is made with high quality components.  It competes very well with the cheaper 400 - 450 Watt PSUs.

Top Quality:

[http://www.ncix.com/products/index.php?sku=17503&vpn=ELT400AWT&manufacture=ENERMAX](http://www.ncix.com/products/index.php?sku=17503&vpn=ELT400AWT&manufacture=ENERMAX) :  This is the one I would buy in your situation.  It's just about $100 Canadian which is the least expensive of the high-performance PSUs.  It has modular cables (means fewer cables dangling about inside), and comes with a handy cable-case.

[http://www.ncix.com/products/index.php?sku=17504&vpn=ELT500AWT&manufacture=ENERMAX](http://www.ncix.com/products/index.php?sku=17504&vpn=ELT500AWT&manufacture=ENERMAX) :  This one will knock your socks off.  It's more pricey (130 CAD), but it's got tons of head room for future upgrades, super steady voltages, and has all the same benefits of the 400W modular.

For more, look here [http://www.ncix.com/products/index.php?majorcatid=100&minorcatid=1066](http://www.ncix.com/products/index.php?majorcatid=100&minorcatid=1066) or your local computer stores.  I typically advise against going to the big stores (such as futureshop, Compusmart, Walmart, or Bestbuy) because it's hard to get "honest and knowledgeable" support.  See if there is a small custom computer shop near you, and you'll likely get better support.  Other brands to consider are Thermalright and OCZ.  I recommend AGAINST most other brands.

---

### Post by dillbertdabomb on 2006-08-16
some times my screen does that if your wondering...

HP Pavilion mx704?

---

### Post by Cave Dweller on 2006-08-16
Thanks Em3raldxiii.  Actually, I'd like to say thankyou to everyone on these fora.  So much helpful and interesting information.  I really appreciate it.

It is interesting, I might see if I can get cpu temperatures and fan speeds displayed on both.  I doubt that I can get a true correlation between the displays, but it might be fun to see how they each change with activity.

---

### Post by saxofoner on 2006-08-16
Ooooh, ouch!  Hardware probs on a Dell.  I feel your pain, man.  That is a Dell, right?

---

### Post by em3raldxiii on 2006-08-17
> **dillbertdabomb said:**
> some times my screen does that if your wondering...

HP Pavilion mx704?

Yeah, I've actually heard of that before myself, though never encountered.  I believe the other case I am aware of involved an LCD screen.  I would be willing to bet that it was capacitors causing the troubles.  There was actually a HUGE international problem with capacitors a few years back (and perhaps still).  I'll see if I can find some links, but basically the premise was that poorly-executed industrial espionage lead to an incomplete electrolyte formula being used in millions upon millions of capacitors by several different companies.  The result was early capacitor death.  Bulging, splitting, leaking, melting ... all of these things have happened.  I myself have changed the capacitors on several motherboards due to this leaking problem.  A few of the boards were Soltek, as were a couple of the video cards I did.  I just cannibalized some other hardware and replaced the caps where I needed to.  Ugh ... there I go ... babbling again.

Anyhoo ... yup, squeeling electronics sucks.  But it's a great reason to "dive-in" to the world of computer hardware :D

Ooh, here's that link:  [http://badcaps.net/](http://badcaps.net/)

---

### Post by Frank Golden on 2006-08-17
> **em3raldxiii said:**
> Yeah, I've actually heard of that before myself, though never encountered.  I believe the other case I am aware of involved an LCD screen.  I would be willing to bet that it was capacitors causing the troubles.  There was actually a HUGE international problem with capacitors a few years back (and perhaps still).  I'll see if I can find some links, but basically the premise was that poorly-executed industrial espionage lead to an incomplete electrolyte formula being used in millions upon millions of capacitors by several different companies.  The result was early capacitor death.  Bulging, splitting, leaking, melting ... all of these things have happened.  I myself have changed the capacitors on several motherboards due to this leaking problem.  A few of the boards were Soltek, as were a couple of the video cards I did.  I just cannibalized some other hardware and replaced the caps where I needed to.  Ugh ... there I go ... babbling again.

Anyhoo ... yup, squeeling electronics sucks.  But it's a great reason to "dive-in" to the world of computer hardware :D

Ooh, here's that link:  [http://badcaps.net/](http://badcaps.net/)
Unless it is the squealing a camera xenon flash caps make while recharging between flashes.

---

