---
title: "Soldering LED's"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-12-06
Hi there,

This ain't an Ubuntu Question, but I thought I might give it a shot anyway!;) 

I'm setting up 50 wireless access points with a router Board 200 system.

[http://www.routerboard.com/archive.html](http://www.routerboard.com/archive.html)

I need to move 6 LED's off the board and onto an info panel. Can anybody offer some electronics help on extending a LED off the mother board to diffrent location, sort of extanding the wires!

Would the extension cable have any diverse affect on the ohmigde if the system?

Any help will be greatly apreciated!

Thanks,

Rudolf

PS: if it needs any justification - the routerboard runs Linux as an OS.

---

### Post by Titus A Duxass on 2006-12-06
You can make the wires/leads as long as you like within reason.

Under 10 metre would not make any difference, just make sure you get the polarity correct.

---

### Post by RudolfMDLT on 2006-12-06
Thanks,

These are surface mount LED's - do they just have a + and - or do they have a 3rd cable as well, like a transistor. Also, could you maby give me any idea how to remove the current surface mounted LED's?

Your help is really apreciated!

thanks,

Rudolf

---

### Post by Titus A Duxass on 2006-12-06
Surface mounted LEDS are like any other LEDs, they can have the normal two leads (diode meaning two electrodes) or three leads if the encapsulation contains two LEDs.

Removing SM components by desoldering is not an easy task. You have to be able to remove the solder by vacumn and heat both contacts (to keep the solder molten)at the same time as well as being able to pick off the component. Oh yes, you have to be able to do this without frying your component at the same time.

You could try piggy backing the leads directly onto the existing LEDs and using small LEDs on your info panel.  You should get away with that as the impendance and current sink of LEDs is very small.

Are the SM LEDs a pure LED package or are they an LED together with a resistor?  Find any identfying numbers and google them for a product datasheet.

The reason I ask this is that some LEDs require a limiting resistor to prevent damage.

---

### Post by RudolfMDLT on 2006-12-06
the LED's have got resistors in the circuit. The board is layered aswell. By hooking a second LED in Parallel with the current one, how will this affect the current in the system? Do i treat LED's as resistors? Sorry but my circuits knowladge is only first year Level.

THanks a lot for your help!

---

### Post by Chinkostu on 2006-12-06
running it in series shouldn't affect it. you could run wires from after the resistor to after the LED and wire a new one in.

the longer way of doing it is using light resisting pads or whatever they're called and wiring up a seperate circuit so that the LED light activates the other circuit.

---

### Post by Peti29 on 2006-12-06
You don't want to treat LED's as resistors. At least not as a simple one :). In one "direction" (polarity) it's rather like a short circuit (when it actually emits light) while in the opposite "direction" it's rather like a cut (whithin reasonable potential range).

---

### Post by Titus A Duxass on 2006-12-06
Running them in parallel should not be a problem as the LED will only consume a little  amount of current. But you will need a similar amount of resistance in series with the new LED otherwise it may go pop.

A Parallel circuit of two equal resistors means that the total resistance ACROSS the two resistance will be half the value of one resistor.  This because there are two current paths not one.

For example, if you put a half inch (half inch being the amount of resistance) hosepipe into the bottom of a large drum and let water flow out, it will flow at X gallons per minute.  Now if you were to put another half inch hose into the bottom of your drum water would flow at 2 times X gallons per minute because there are two paths.

With your LEDs in parallel you will have two paths one with an amount of resistance and one without any significant amount resistance. This means that the current, because it is lazy like water, will take the path with the least resistance.  This leads to a large current flow through your new LED, which could lead to the LED going pop or even it could damage your board.

By the way, I'm sorry if I'm teaching you to suck eggs.

Peti29 - nobody was treating the LED as a resistor.  We were establishing if a current limiting resistor was present in the SM LED package or not.

---

### Post by RudolfMDLT on 2006-12-06
Thanks guys! you guys rock!

So here's the plan - I cannot remove the LED's, so by soldering another LED in parallel with the current one what should I be looking for? High resitance LED's that will try and keep the current the same as before, but then won't I need more voltage accros the new parallel circuit?

I really have no idea on LED specs!  

Please see the attachment for what I want to do - sorry but I had to do the diagram in MSPaint.

THanks,

Rudolf

---

### Post by RudolfMDLT on 2006-12-06
I guess what I'm asking is, what in your opinion will the board be able to handle? A voltage or a current change because depending on what resitor configuration i choose i will either demandmore voltage or more current?

---

### Post by Peti29 on 2006-12-06
Titus A Duxass:
RudolfMDLT wrote "Do i treat LED's as resistors?". I answered to that. Sorry if I was ambiguous.

RudolfMDLT:
Your diagram seems OK to me - however I must mention I've never done sg like this myself.
For LEDs have very low resistance soldering them paralelly should have negligible effect on current (the resistor is to limit current). Since you bind them paralelly the voltage will be the same on both of them.

Only problem is if your SM component has a built in resistor in it. In this case you might unintentionally create the following circuit (hopefully on the diagram ;))

[ATTACH]20644[/ATTACH]

This leads to the situation Titus was writing about: "a large current flow through your new LED, which could lead to the LED going pop or even it could damage your board"
I think you should get a measuring device and check the resistance of the LED's SM component. If thats very low (about the same as the resistance of your new LED that you want to add) you can assume that there is no built in resistor :).

---

### Post by Titus A Duxass on 2006-12-06
Start off with a very high resister about 1Kohm and if the LED does not light up then it is too high.

If you have a wide range potentiometer you could use that to find the optimum  level.

If you google LED current limiting resistor you will find loads of information, but you need the datasheet for your existing  LED and your new LED.

This site [http://www.kpsec.freeuk.com/components/led.htm](http://www.kpsec.freeuk.com/components/led.htm) recommends a 1Kohm resistor is suitable for testing.

By the way, you will need a fine pointed soldering iron of not more than 700watts and a steady hand, so lay off the booze before you start:-))

---

### Post by geekygreen on 2006-12-06
LED's have different operating voltages...just putting them in parallel could result in two dim LED's, or only one that works...

I like the idea of a "Light Repeater", by placing a photo detector infront of the LED, to detect when teh LED is on, and turn on a remote LED.  THis would have the advantage of not screwing with surface mount soldering....which can be easy to mess up unless you have lots of practice!

By the way, I wouldnt use more than a 70W iron, not 700 Watts!  Preferrable, to do this you would have a variable heat soldering station...just dial up what you want.  The simple pin point soldering iron from Radio shack is probably too large for this, even...

Good luck!

---

### Post by thejerryguy on 2006-12-06
Most LED's require a resistor to limit the current. One would assume that a few ohms added to the circuit from the cable would not present a problem. As long as your cable is large enough to supply the total current for LED's.

---

### Post by RudolfMDLT on 2006-12-06
Hi guys! Thanks for all the great replies and I will consider them all, just a new idea I would like to run past you guys.

Fiber optic? Will it be possible to glue a peace of fiber optic cable to the led and transmit the light to where I want the status panel.

[http://www.phy.davidson.edu/StuHome/blreynolds/images/fiberoptic2.jpg](http://www.phy.davidson.edu/StuHome/blreynolds/images/fiberoptic2.jpg)

I know this is totally off the mark but I think it might be the most risk free option?

---

### Post by Iowan on 2006-12-06
As if you needed another option...
You might consider running fiberoptic cable (a light pipe) from the existing LED's to the new location - no soldering, no calculating current draw, etc.  Several of the computers I have use a light pipe (though not cable) to direct light from board-mounted LED's to front panels.

I'm also of the opinion that adding LED's in parallel *may* tax the driver circuit - resulting in dim display (or no display if/when the driver smokes).

Whoa... how'd I miss your last post???  Anyway, I agree, that'd be the low-risk way.

---

### Post by RudolfMDLT on 2006-12-07
Thanks Iowan! Light pipe, i'll look into it! 

nAnd thanks to everyone else who helped!:)

---

### Post by Titus A Duxass on 2006-12-07
> nAnd thanks to everyone else who helped! - you're welcome.  It was nice to kickstart the old grey matter by trying to remember something a learnt 25years ago (way before SMD, in fact before LEDs).

---

### Post by Duck2006 on 2006-12-07
The led will not pop as some one said but the limitting resistor may get a bit hot depenning on what wattage it is, and ohmage it is, so your have to look up the specs of the led to work out if the limerting resistor needs to be changed, for the corect voltage drop across the leds. round 1.2V

---

### Post by Titus A Duxass on 2006-12-07
Duck 2006 - if you let enough current flow through a LED the junction will overheat and burn out, okay it won't go "pop" in any audible manner, but it won't be very happy.

---

