---
title: "Installation Keeps Freezing"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by kevin626 on 2007-02-26
First off, when i run it off the cd, it is extremely slow.  It takes minutes for one thing to load.  Secondly, i can't seem to get through the installation process, i usually get to the partition part and it freezes.  My computer aint great but it does have the 256 mb of ram required and a fast enough processor.  Any help would be greatly appreciated.

---

### Post by Kateikyoushi on 2007-02-26
Could you  be a bit more specific about your hardware ?
Which version of ubuntu do you try to install ? Check the CD for errors.

I would try the following.

Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by energiya on 2007-02-26
This is the order I would choose to do things:
1) Check CD for errors.
2) Burn CD at 4x
3) Try Alternate CD

---

### Post by Terry of Astoria on 2007-02-26
I have had similar problems (can't get past the partitioning stage) on two or three different PCs that exceeded the recommended specs. I found that using the alternate cd works. Or, try this: use another linux live CD to create a swap partition on the hard drive. I did that and then magically the 6.06 cd ran a LOT faster and made it all the way through the install successfully.
 And do run memtest.

---

### Post by kevin626 on 2007-02-27
So i burned a new cd at 4x and checked the cd and everything was good.  I did the memory test and I still have a problem with the install freezing.  

My computer has and AMD sempron 1.6 mhz processor, 256 mb ram.

I'm not really sure how to put those commands in either btw.

---

### Post by webofunni on 2007-02-27
I think you need to get the safe graphic mode to install without freezing problem

---

### Post by kevin626 on 2007-02-27
I've done the safe graphics mode as well and still froze.  I want to try those commands.  Do i just hit f6 at the start up and then type for example, boot: linux noapic.  Do i do them all at once? or try one at a time?

---

### Post by chuckyp on 2007-02-27
You hit F6 and then type them in at the end of the line.  The other thing to try would be the alternate iso availible at the same place you downloaded the desktop iso.  This will save you a lot of overhead.  That way the live cd isn't loaded and its a text based installer.

---

### Post by ddom87 on 2007-02-27
Just make sure if you are partitioning to make a swap partition. I would say about 1 gig. And when its actually creating the partitions it can take quite some times sometimes. When i created the partitions for the dual boot on my laptop it took about 5-10 minutes with nothing on the screen so i just went to get something to eat came back and it was done.

---

### Post by kevin626 on 2007-02-27
I'm going to probablly have to do the alternate cd.  It's weird, i was able to open like solitaire and firefox and they worked preety good.  But i just can't get through this installation.

---

