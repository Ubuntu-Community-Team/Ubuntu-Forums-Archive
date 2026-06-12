---
title: "I just bought a new computer"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by sethdotcom on 2007-07-02
I just bought a new pc because my old one's motherboard went dead, Now how can I get the music off of that old hardrive I had in the old pc to my new one? Can I just take the new hardrive out and put my old one in the new computer? Then burn the music to dvd's, or can I have both drives inside it at the same time?, and transfer that way?

---

### Post by Rocket2DMn on 2007-07-02
If it's a desktop computer, you can keep both drives inside using and IDE or SATA connection.  If the old drive is from a windows computer, you will need to install ntfs-3g so you can read/write from/to the drive.
If it's a laptop, you can buy an external case for your old harddrive, they run anywhere from 20 bucks to 40 or 50, but you tend to get what you pay for.

---

### Post by sethdotcom on 2007-07-02
> **Rocket2DMn said:**
> If it's a desktop computer, you can keep both drives inside using and IDE or SATA connection.  If the old drive is from a windows computer, you will need to install ntfs-3g so you can read/write from/to the drive.
If it's a laptop, you can buy an external case for your old harddrive, they run anywhere from 20 bucks to 40 or 50, but you tend to get what you pay for.

should there be enough cables in the new computer to hook-up both? and does the computer detect both instantly? and it is a new IBM desktop

---

### Post by koshari on 2007-07-02
all MoBos have differing sata/pata configurations depending on their age.

if your hard drive is out of an old machine it would almost certainly be a pata hard drive, you can tell this as then have a 4cm flat connector as opposed to a sata which has a 1 cm wide cable.

if your PC has a spare pata connector on the mObO it will be fine to connect the older drive.

---

### Post by mysticrider92 on 2007-07-02
It all depends on how your new computer is set up. You should be able to use whatever data cable is in the old computer and plug it in to your new motherboard. Just leave the new computers drives plugged in and connect the old hard drive to it in a different port (or cable positon if there are no slots on the motherboard). 

The new computer should detect the old drive and give it a letter (if you are on Windows), or show an icon on the desktop (in Ubuntu). From there, you can move your files to the new hard drive.

---

### Post by regomodo on 2007-07-02
it won't detect instantly like a usb device. at least the last time i had to do soehting like this, in edgy, it didn't for me.

you are going to either a. edit the fstab if you intend on leaving the drives in or b. mount the partitions to a suitable directory

---

### Post by SoloSalsa on 2007-07-02
Not likely.  Most manufacturers just give you the bare minimum of cables, but some do have extra ends.  Unless, if it is SATA.  SATA motherboards almost always have extra jacks, whereas there are usually two PATA, which are usually filled.

There are a bunch of things we could do to help.  The fastest thing would be to tell us the model numbers of the new and old computers.  Then, we could find out all of the necessary information on-line.

---

### Post by mlentink on 2007-07-02
> **sethdotcom said:**
> and it is a new IBM desktop

Does IBM still sell under their own brand? I thought it was all Lenovo since about a year or so?

---

### Post by Jem00 on 2007-07-02
You could always buy an external casing for your hard drive and hook it up through USB as an external.

---

### Post by regomodo on 2007-07-02
> **Jem00 said:**
> You could always buy an external casing for your hard drive and hook it up through USB as an external.

yep. and ubuntu will mount automagically

---

