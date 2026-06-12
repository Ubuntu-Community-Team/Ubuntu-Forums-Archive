---
title: "No idea where to post this but........."
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Tristicus on 2007-12-23
I am having a problem!


Whlst getting ready to build my new Ubuntu build, I am transferring my stuff to a different case.
Everything worked right before I switched components.

Computer boots, but will not display anything, and will also not beep when turned on.

Help please!

---

### Post by CCNA_student on 2007-12-23
So you are saying that you switched out components and now it does not work? Please clarify.

         Sin Cere,

         CCNA

---

### Post by Wiebelhaus on 2007-12-23
This means your not reaching the POST (Power on self test) basically I would reseat everything and double check everything , if it still doesn't work , then you need to start by removing all unnecessary componets like the NIC , Sound , Modem , Readers etc. until you achive POST , you get the point , once you drill down which componet is causing problems you can then replace it this is called "The process of Elimination" But most importantly you need to reseat the processor , ram , power supply and the HDD.

Don't unplug or plug anything in with the power on.....I know I know , but I've seen people do this , also you protected the compnets from ESD (Electro-static Discharge) correct?

Good luck.

---

### Post by Tristicus on 2007-12-23
Sorry for the unclear post, I am nervous and rushing.

I switched all the parts over from my old case to the new case. Everything is plugged in correctly and fastened. Even the front speaker, reset, power, and USB ports. 

The AGP video card is plugged in, and when I turn the system on, everything powers up, but the system does NOT beep and nothing is displayed on screen. Tried a different graphics card and same. removed RAM halfway and same thing. Removed IDE HDD and same thing.

I really need this working.

---

### Post by Wiebelhaus on 2007-12-23
> **Tristicus said:**
> Sorry for the unclear post, I am nervous and rushing.

I switched all the parts over from my old case to the new case. Everything is plugged in correctly and fastened. Even the front speaker, reset, power, and USB ports. 

The AGP video card is plugged in, and when I turn the system on, everything powers up, but the system does NOT beep and nothing is displayed on screen. Tried a different graphics card and same. removed RAM halfway and same thing. Removed IDE HDD and same thing.

I really need this working.

Removed ram half way? what do you mean by this? Reseating the processor will almost always fix this type of thing if all components are functional , back in the day they would shift constantly , this was a daily occurrence.

---

### Post by CCNA_student on 2007-12-23
Is your monitor working? Would you be able to try using a different motherboard or processor? My guess is that it is one of those things. 

      Sin Cere,

      CCNA

---

### Post by Tristicus on 2007-12-23
> **sx66gns said:**
> 
Don't unplug or plug anything in with the power on.....I know I know , but I've seen people do this , also you protected the compnets from ESD (Electro-static Discharge) correct?

Good luck.

I don't know. I just picked up the mobo from the case and put it in the other.

---

### Post by Tristicus on 2007-12-23
> **sx66gns said:**
> Removed ram half way? what do you mean by this?

I just pressed the buttons (little white strips) on one side, not the other.

Yes, monitor works, and when VGA cable isnt connected it displays the warning that it isnt or w/e,

I know a lot about PCs, but right now I am in sorta panic mode, as I am tired and such, so probably utttering on, so bear with me./

---

### Post by CCNA_student on 2007-12-23
The only other things I can think of that are not working are the motherboard or processor.

---

### Post by Dngrsone on 2007-12-23
Does the motherboard power up?  Watch the CPU fan (and any others that are visible) and see if hitting the power switch causes movement.

If there is a slight movement only, then there may be a short-- make sure the case is not contacting the motherboard anywhere except where it's supposed to be.

If there is no movement at all, then your power supply isn't turning on at all... it could be a bad switch, loose plug or connector, or a bad power supply.

---

### Post by branx503 on 2007-12-23
Do the case/cpu fans whir up when you hit the power button. If not, check the power connections to ensure they're seated.

Otherwise, do as suggested above and remove non essential components until you can at least post. Essential: cpu, ram, power. Video isn't technically essential but it would be a good starting point.

---

### Post by Tristicus on 2007-12-23
I am going to try to reseat the processor right now first. lets see how this goes.

---

### Post by Wiebelhaus on 2007-12-23
> **Tristicus said:**
> I just pressed the buttons (little white strips) on one side, not the other.

Yes, monitor works, and when VGA cable isnt connected it displays the warning that it isnt or w/e,

I know a lot about PCs, but right now I am in sorta panic mode, as I am tired and such, so probably utttering on, so bear with me./

When you did this you essentially were causing a ram fault , if you didn't do it WITH the power on then it should not have damaged anything , BUT if you didn't get a ram fault error then it's one of two things , you need to reseat the processor as it's not performing the the very first test in the POST which is testing the Power wire , if you remove the ram and everything else besides the processor and then reseat the processor then plug the power supply in and turn it on , see if you get error codes , normally tripple beeps , if this doesn't happen then you killed the board with ESD my friend.

These types of things should not be done on the kitchen table without anti-electro static protection of some kind.

---

### Post by Wiebelhaus on 2007-12-23
> **Tristicus said:**
> I am going to try to reseat the processor right now first. lets see how this goes.

Don't be cheap with the thermal grease but not messy , make sure that the heatsink is seated properly and that the fan is plugged in , good luck.

---

### Post by Tristicus on 2007-12-23
Uhh, is the porcessor suppsed tro be stuck to the heat sink lol?

How do I GENTLY pry it off?

---

### Post by Wiebelhaus on 2007-12-23
> **Tristicus said:**
> Uhh, is the porcessor suppsed tro be stuck to the heat sink lol?

How do I GENTLY pry it off?

stupid p4's , I hate those heat sinks , it's probably a 478 huh? yea , do it with a flat tip , very carefully.

---

### Post by CCNA_student on 2007-12-23
The processor is really stuck to the heat sink?! If you know how that happened please explain. Did you overclock your processor or something like that? I have only heard of that happening once when a fan died on one of the servers at the high school I go to.

---

### Post by Tristicus on 2007-12-23
> **sx66gns said:**
> stupid p4's , I hate those heat sinks , it's probably a 478 huh? yea , do it with a flat tip , very carefully.
Yep 478 P4 3.4ghz HT with a Thermaltake heatsink. sopmeone said to blow dry it to make the thermal paste more liquidy then gently get it off. 
> **CCNA_student said:**
> The processor is really stuck to the heat sink?! If you know how that happened please explain. Did you overclock your processor or something like that? I have only heard of that happening once when a fan died on one of the servers at the high school I go to.

No. Just stuck up there...

---

### Post by Wiebelhaus on 2007-12-23
> **CCNA_student said:**
> The processor is really stuck to the heat sink?! If you know how that happened please explain. Did you overclock your processor or something like that? I have only heard of that happening once when a fan died on one of the servers at the high school I go to.


Happens on the socket 478's every time , that's why they were redesigned.

---

### Post by Wiebelhaus on 2007-12-23
> **Tristicus said:**
> Yep 478 P4 3.4ghz HT with a Thermaltake heatsink. sopmeone said to blow dry it to make the thermal paste more liquidy then gently get it off. 


No. Just stuck up there...

Lol , I knew it , pieces of crap they are , not the processors they are work horses but the ZIF (Zero force insertion) design was pure crap.

---

### Post by Tristicus on 2007-12-23
> Remove the fan from the heatsink, and put a hair dryer blowing into the fins on the sink (not the cpu!)for about 15secs.

Gonna try this for a minute.

I need upgrades badly./

---

### Post by CCNA_student on 2007-12-23
I have never worked on a P IV before. I have mainly worked on Celeron(socket, I think it was 378) and AMD boards(mine is socket 939), and some really old systems in my computer repair class. A lot of annoying HP's and Compaq's from the late 90's. Is the P IV that annoying to work on? 

      Sin Cere,

      CCNA

---

### Post by Tristicus on 2007-12-23
haridryed for 10secs and twisted it off....gonna re-apply grease and re-seat now

---

### Post by Wiebelhaus on 2007-12-23
> **CCNA_student said:**
> I have never worked on a P IV before. I have mainly worked on Celeron(socket, I think it was 378) and AMD boards(mine is socket 939), and some really old systems in my computer repair class. A lot of annoying HP's and Compaq's from the late 90's. Is the P IV that annoying to work on? 

      Sin Cere,

      CCNA

Just the 478's , this type of recognition I have comes from years on the bench , you'll get there unless those G pc's take over the world , then we'll be out of a job. no worries they'll need someone to ensure the networks are communicating properly considering everything from your bank ATM to your phone systems and cable TV are transferring data over a network.

---

### Post by Wiebelhaus on 2007-12-23
> **Tristicus said:**
> haridryed for 10secs and twisted it off....gonna re-apply grease and re-seat now


Good luck mate.

---

### Post by CCNA_student on 2007-12-23
sx66gns, may I ask you something? I was wondering if you have or are studying for the A+ exam like me. If so, what is the test like. I am currently studying Cisco's IT Essentials curriculum. I know that this is off topic but I was just curious. 

        Sin Cere,

        CCNA

---

### Post by Tristicus on 2007-12-23
Alright. Re-seated, re-applied grease, put sink back on, started up, no beep and no display.

Pissing me off.

---

### Post by CCNA_student on 2007-12-23
Try a different motherboard. That is the only thing you have not changed yet right?

---

### Post by Wiebelhaus on 2007-12-23
> **CCNA_student said:**
> sx66gns, may I ask you something? I was wondering if you have or are studying for the A+ exam like me. If so, what is the test like. I am currently studying Cisco's IT Essentials curriculum. I know that this is off topic but I was just curious. 

        Sin Cere,

        CCNA

It's easy , asks allot of Multiple choice questions , it's timed and numbered , A secret is if your doing really good you'll have to answer less questions , if your missing them then you'll have to ask more , you only have to get like 78% (loose number) of them right , so if you get all 78 questions right the computer will cut off and your done , if your missing some then you'll have to answer more , there are some really odd old world tech type questions you'll need to know all those little things like the design flaws with the 478 for example.

Or "How many devices, a 16 bit SCSI-2 can support?"

It's obvious what the answer is , but if your not or weren't paying attention you'll get it wrong and probably have to answer a harder rarer question later on , also the company that hosts the test is a real class act POS , I won't explain why because it will sound negative but after you deal with them you'll see , not comp TIA but the contracted test monitor people , may be different in your area.

---

### Post by CCNA_student on 2007-12-23
How does the A+ compare to the CCNA exam I took? I got an 87% on that one.

---

### Post by Tristicus on 2007-12-23
> **CCNA_student said:**
> Try a different motherboard. That is the only thing you have not changed yet right?
I have no mobo compatible with chip and memory and such, and I know it isnt the psu

---

### Post by Wiebelhaus on 2007-12-23
> **Tristicus said:**
> Alright. Re-seated, re-applied grease, put sink back on, started up, no beep and no display.

Pissing me off.

Yea man , do you have a shop in the area , they would run diagnostics for about 30 bucks , not best buy though man...

But 30 bucks is halfway to a new Mainboard / Cpu combo like this one:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3425852&Sku=MBM-K9MMV-3500A](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3425852&Sku=MBM-K9MMV-3500A)

or 

[http://www.tigerdirect.com/applications/category/category_slc.asp?CatId=1619](http://www.tigerdirect.com/applications/category/category_slc.asp?CatId=1619)

Sorry man , we tried to help but honestly it sounds like you killed it somehow.

---

### Post by Tristicus on 2007-12-23
Damnit this is sucking very bad right now. I have absolutely NO CASH at all and no computer.

Damn it, this always has to happen to me.

---

### Post by Tristicus on 2007-12-24
ALRIGHT!

AOPEN ax4sg-un motherboard

I cannot find the problem. I have removed everything, reaseated processor, booted 1 by 1, and still no beep. Weird thing is, HDDs still power up and so does video card and fans, so I DON'T KNOW what is wrong.

Well, this means I need another board. I CANNOT find my board anywhere to buy, so I need a board that takes DDR PC2700 (I THINK....can't run CPU-Z to find out) and have an AGP slot or a PCI-E

---

### Post by Tristicus on 2007-12-24
Solved! Motherboard Was Grounded!! Yeah!!!!

---

