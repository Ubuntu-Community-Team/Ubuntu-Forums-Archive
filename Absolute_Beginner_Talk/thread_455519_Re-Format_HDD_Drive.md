---
title: "Re-Format HDD Drive"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Eldar11 on 2007-05-26
I have two boot drives and I need to know how to reformat one to be a slave drive.  I am running feisty on a Pentium III Dell Demention desktop with 512MB RAM.

---

### Post by earobinson on 2007-05-26
you will be able to do this with a gui if you install gparted

---

### Post by oilchangeguy on 2007-05-26
> **Eldar11 said:**
> I have two boot drives and I need to know how to reformat one to be a slave drive.  I am running feisty on a Pentium III Dell Demention desktop with 512MB RAM.

you don't have to reformat a hard drive to make it a slave. you'll have to open the computer and change the jumper setting on the drive in question.

---

### Post by MikeDX on 2007-05-26
You can change your linux os 100 times and never lose a thing if you keep a seperate /home partition.

---

### Post by oilchangeguy on 2007-05-26
> **earobinson said:**
> you will be able to do this with a gui if you install gparted

please explain how gparted can change the jumper settings of a hard drive?????????????

---

### Post by Eldar11 on 2007-05-29
ok, My friend mentioned Gparted, and I downloaded it and made a Live CD, but I havent done it yet, but if that wont do what I'm looking for then what is changing the jumper switch?  and how would you do that?

---

### Post by LaRoza on 2007-05-29
Before doing anything, what kind of drive do you have? If it is a SATA drive, there is no such thing as master and slave, and there are no jumpers.

If you are using (ATA,PATA,Ultra ATA, IDE,EIDE) check the drive for directions or a diagram. All drives are slightly different so I can't say exactly what the drive will say.

-edit the Jumper is a physical switch, not software.

If you are having trouble, post the drive's model and company here.

---

### Post by Mark_in_Hollywood on 2007-05-29
Unplug the power from the computer. 

Open the computer's case. 

If necessary remove the cable and power cord from the hard disk drive.

Determine the name and model of the drive and write that on a piece of paper. If the jumper settings are printed somewhere on the drive, so much the better. If NOT:

Reattach all the drives cables, being cautious with polarity.

Get back online and google: "jumper settings" and the drive name and model number.

The mfg. should have this online.

Some mfgs. are better than others at explaining this.

When the computer is next booted, if you are using GRUB, you will see something like:

hda
hdb


or 

scsi (1)
scsi (2)

and a list of operating systems to boot from.

I can't help you from there. Somebody else will have to tell you how to reformat (low-level format?) the HDD.

---

### Post by LaRoza on 2007-05-29
You do not need to low-level format a hard disk anymore.

---

### Post by Eldar11 on 2007-05-29
well the one I want to make a slave is a Western digital 20.5GB EIDE drive and the current one is... something, i dont feel like opening the box right now, but I've had to take my computer apart and put it back together many at time.

---

### Post by Eldar11 on 2007-05-29
accually looking at the drive the jumper settings are printed right on the drive! wow that was a long run to nowhere for something that is right here

---

