---
title: "Dialup modem"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Linux&amp;Lizards on 2007-02-26
Hey guys!

My friend has made the leap from window$ to ubuntu!
Unfortunately his internal modem doesn't work with linux :(
I had an extra one lying around and we gave that a shot.
We were all happy until we discovered that the driver used an obsolete kernel.

We have come to the conclusion that it is best just to buy a new internal modem.

our budget is $20-$30 
Any suggestions for an internal modem that works well with ubuntu?
all suggestions are welcome!

---

### Post by rccharles on 2007-02-26
> **Linux&Lizards said:**
> Hey guys!

My friend has made the leap from window$ to ubuntu!
Unfortunately his internal modem doesn't work with linux :(
I had an extra one lying around and we gave that a shot.
We were all happy until we discovered that the driver used an obsolete kernel.

We have come to the conclusion that it is best just to buy a new internal modem.

our budget is $20-$30 
Any suggestions for an internal modem that works well with ubuntu?
all suggestions are welcome!

I would suggest an external modem.  This way you will avoid the dreaded winmodems.

See:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

...............

Could you can post the make and model number of the internal modem here.  Perhaps someone knows of a solution.

Robert

---

### Post by Mark_in_Hollywood on 2007-02-26
I CANNOT too highly recommend NOT using an internal modem, unless you are sure, before purchase that the COM ports (in Linux /ttyS#s) and the Interrupt Requests are adjustable on the modem, NOT repeat NOT in software.

After nearly a year of pains asking here there and everywhere for help, solutions, etc., I gave up and got an external 56K modem.

I had ActionTec's PM560LKi, which is a controller based modem, but the damn thing could not be properly set up by wvdial.

For those who don't remember Windows 98 and prior, the Microsoft COM ports were 1 to 4, until they found too many serial devices and the modem mfgs. moved their modems up to COM 5. Ubuntu from Hoary to Breezy to Dapper has never been able to be config-ed to work with that 560 internal modem. Sometimes the OS "sees" the device and sometimes it "sees" it and then can't find it a few minutes later.

For references to this problem, see posts under my Mark_in_Hollywood and modem as keyword searches.

---

### Post by DoctorX on 2007-03-05
[COLOR="YellowGreen"]well buddies,

i don't think that is the real solution, though i am also suffering with it...with my new internal modem...
the key is to make it work anyhow, n not giving it up to buy, i repeat "buy" another "external" modem... lets go for the solution, i hope this way both of our problems can be solved...

if u have anything new. pls post it...


DoctorX
medical student
NEPAL[/COLOR]

---

### Post by Linux&amp;Lizards on 2007-03-06
I don't have anything new to add sry guys.

Bestbuy has a external modem but I would like to get this one working.
The interna one was purchased was purchased at compusa and we all know what a pain in the @$$ they can be to work with.
No offense I have bought some god stuff at compusa and  gotten great survice as well I just don't think that they're the easiest to work with.

---

