---
title: "Difficulty installing a new HD - mainly the IDE ribbon"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Henaro on 2007-11-25
Hello everyone~

I recently got my hands on a little 40 gig HD.  I was going to install it when I realized my IDE ribbon only had the master and mobo female connectors.  So I went to radioshack and picked up a new one that had master, slave and mobo female connectors.  

I've tried installing my new little HD and it just came up to the compaq start up screen and just stayed there.

I tried using the new ribbon and my old HD and the same thing happened.

Right now I'm using my old HD and old ribbon.  Could the IDE ribbon be bugged?  I hope not because this was the only one they were carrying.  

My mother board is, I believe, an ASUS but I'm not too sure.  It's kind of old, about 3 to 4 years.  It can only support AGP and two gigs of RAM so I'm wondering if it can only support one HD.  My power supply seems like it has enough power for a second HD, it's a 250W.  

Right now I'm assuming that it's the ribbon as it won't work on my new HD.  


**TL;DR version: I'm trying to install a new HD but the ribbon isn't working :(.**

---

### Post by jken146 on 2007-11-25
Check that the jumpers are set correctly on your drives (i.e. for master or slave or cable select--where the plug on the cable you use decides for you).  Make your original drive the master on the IDE0 channel (in BIOS, this is probably known as primary master).  Check your BIOS settings too.

---

### Post by mistergq on 2007-11-25
do you have each hard drive pin set to either cable select, or one hard drive as master and the other one as slave?

second, did you have the master portion of the cable plugged into master part of the cable and slave hard drive as slave?

---

### Post by Pumalite on 2007-11-25
Could be a matter of the right ribbon. Or a matter of jumpers. Take a look at the instructions in the hard drive and install the jumper according to the position you are assigning to the hard drive.

---

### Post by jken146 on 2007-11-25
It's not surprising you can't boot to anywhere with your new drive if there is nothing on it.  Plug it in and use a live cd if you have one to have a look if it's there (use e.g. gparted).

---

### Post by overdrank on 2007-11-25
> **Henaro said:**
> Hello everyone~

I recently got my hands on a little 40 gig HD.  I was going to install it when I realized my IDE ribbon only had the master and mobo female connectors.  So I went to radioshack and picked up a new one that had master, slave and mobo female connectors.  

I've tried installing my new little HD and it just came up to the compaq start up screen and just stayed there.

I tried using the new ribbon and my old HD and the same thing happened.

Right now I'm using my old HD and old ribbon.  Could the IDE ribbon be bugged?  I hope not because this was the only one they were carrying.  

My mother board is, I believe, an ASUS but I'm not too sure.  It's kind of old, about 3 to 4 years.  It can only support AGP and two gigs of RAM so I'm wondering if it can only support one HD.  My power supply seems like it has enough power for a second HD, it's a 250W.  

Right now I'm assuming that it's the ribbon as it won't work on my new HD.  


**TL;DR version: I'm trying to install a new HD but the ribbon isn't working :(.**

HI did you change the jumpers on the hard drives? Some drives are pre set for single drive only and you have to move the jumper to enable the master with slave and the the second drive set the jumpers to slave.
Edit man I type to slow :)

---

### Post by mgmiller on 2007-11-25
Since this is IDE, you need to make sure the jumpers are set correctly on both the drives.  
If the original drive is a Western Digital, you need to remove the jumper or set it sideways instead of vertical to disable it to use it as a stand alone master.  

If it is any other brand, the stand alone master and master with slave is the same, set to master.

Once you add a second drive, you must change the jumpers so one drive is master and the other is slave.  I assume you are using the original drive as your master and the new small drive should be set as slave.  

Check the jumper positions, they often are set as cable select, which I don't trust.  Make one master and the other slave and you should be ok.

Edit:
Wow! everyone responded at the same time with pretty much the same answer!  :lolflag:

---

### Post by Henaro on 2007-11-25
Wow so many responses :o!

Which part is the jumper?  Is it the part to the right of the IDE slot with the little black thing in it?  

Also I'm kind of unsure how to check the BIOS...

And even if the jumpers weren't set to allow multiple drives then wouldn't the new ribbon be working with the old drive either way?

---

### Post by Pumalite on 2007-11-25
I think the jumper we are all talking about is the little plastic one that you set differently if you are going to install as master or slave.

---

### Post by overdrank on 2007-11-25
> **Henaro said:**
> Wow so many responses :o!

Which part is the jumper?  Is it the part to the right of the IDE slot with the little black thing in it?  

Also I'm kind of unsure how to check the BIOS...

And even if the jumpers weren't set to allow multiple drives then wouldn't the new ribbon be working with the old drive either way?

HI and this link has some photo's 
[http://lifehacker.com/software/feature/how-to-install-a-hard-drive-137179.php](http://lifehacker.com/software/feature/how-to-install-a-hard-drive-137179.php)

---

### Post by Pumalite on 2007-11-25
Great link.

---

### Post by Henaro on 2007-11-25
Thanks for the link.  It's a great help.  But it still doesn't answer my question about the ribbon.  

Forget about the new HD for a sec, my new ribbon isn't working with my old HD.  The old HD is set to MA and I'm sure I have the ribbon hooked in properly.  


This is what it looks like:

MOBO+-------------------------+Slave connector+----+Master connector


The slave one is unused and it isn't working.

---

### Post by the-edmeister on 2007-11-25
Do you have the correct type of ribbon cable for your drives? 
ATA 33 - 40 wire ribbon is usually a very light grey color with 3 black connectors vs. ATA 66 - 80 wire ribbon cables are usually a darker shade of grey - OEM ATA 66 cables usually have a black connector for the mobo, and two grey or blue connectors for the IDE drives
 
Don't assume that Radio Shack sold you the correct cable - I worked for them (health insurance for part-time employees while I was struggling with starting a new business) and  long after the ATA 66 cables became the standard RS still didn't sell the new type when I left in 2004, heck they didn't even have the old cables labeled as ATA 33, just ATA.

Is the correct end of the cable plugged into the mobo? 
your diagram indicates you have it correct, but it bears asking


Ed

---

### Post by Bigbird999 on 2007-11-25
If the old drive doesn't work with the new cable, it is a bad cable, (or the cable is not properly connected to the mobo or HDD).  Since it is Radio Shack, I would bet it is either a broken or very old cable.  You should be able to get a proper cable at any computer shop/ or big box store for a couple of bucks.  
Not to miss the obvious, you are plugging in the power plug to each drive, right?  It is easy to miss this step, I know cuz I have done it!!

BB

---

### Post by Henaro on 2007-11-25
Okay guys here's the scoop.  


Something is seriously going wrong.  


I believe that radioshack has sold me the wrong cable, mainly because the cable I bought and the old cable do not match.

The old cable is dark gray with smaller wires with a blue piece for the mobo and the black for the HD.  The one I bought is light grey with thicker wires and black connectors.  

Another serious problem has occurred.  When trying to take the old cable out of my HD, it seems as though the connector blew up I guess and half of it was stuck in my HD's connector.  I  finally got it out, but now it definitely won't work.  

And now my old HD and my old cable won't even work.  I'm with out a hard drive right now.   :(

This... is not good.  :(

PS-I'm on my laptop which has a terrible keyboard.

---

### Post by Pumalite on 2007-11-25
Get the right cable and you are back in the saddle.

---

### Post by Henaro on 2007-11-25
Just confirmed the worst, my old HD, the one with all of my important things is now 6 feet under.  gparted says it's unallocated space.


Also, I should be getting a ATA 66 correct?

---

