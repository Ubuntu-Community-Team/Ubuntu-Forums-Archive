---
title: "LiveCD Freezes on Ubuntu Startup"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by fresch1 on 2007-02-21
Hi.

I recently decided i wanted to try out ubuntu, and thanks for the great help on this forum so far.

I just got to the point where i wanted to start out by downloading Ubuntu 6.10, and burn it to a disc (The slowest i could burn was 8x).

When i insert the disc, turn on my computer, the pc boots from the disc, and i get a Menu with a Big ubuntu logo.

Now, when i select the "Start Ubuntu" option, the ubuntu logo appears, with a progress bar..
It runs for at minute or so, and then it freezez.
The progress bar dosent move or anything..

GREAT Ubuntu.... :confused: 

My Pc is up to date, and every hardware part works as it should.
My system is

* AMD Athlon 64 3500+
* 1 GB Ram
* MSI K8N Neo4 Mainboard
* Ati Radeon x1950 pro

My Harddrives are sat up this way if that has anything to do with it:

Harddrive 1 - Seagate IDE 80 Gb.
                              Partition 1 - 20 gb: Windows Vista System
                              Partition 2 - 60 gb: Empty (Want to use this for Ubuntu)

Harddrive 2 - Seagate SATA 300 Gb
                              Partition 1 - 200 gb: Storage
                              Partition 2 - 100 gb: Storage

Harddrive 3 - Seagate SATA 300 Gb
                              Partition 1 - 300 gb: Storage


I hope you can help, as this really annoys me.. :/
Other people are having the same problem but noone seems to have a solution.
This is so wierd.
I Also tried to check the disc from the menu, and the dics was fine.
Safe Graphics mode did the same freeze as the normal startup.

---

### Post by fresch1 on 2007-02-21
I just tried booting by pressing F6, and removing the text "quiet splash".
This is the place where it freezes. 

[IMG]http://frip.dk/helious/Ubuntu.jpg[/IMG]

---

### Post by rsambuca on 2007-02-21
At the main menu, press F6 to enter boot options.  In front of the "--" at the end of the line, try adding```
irqpoll pci=noacpi noapic nolapic acpi=off
```before the dashes and make sure you leave a space before the dashes.  Then see if it boots.  If that doesn't work, you can instead try "ide=nodma" as a boot option.

Let us know how it goes.

---

### Post by fresch1 on 2007-02-21
> **rsambuca said:**
> At the main menu, press F6 to enter boot options.  In front of the "--" at the end of the line, try adding```
irqpoll pci=noacpi noapic nolapic acpi=off
```before the dashes and make sure you leave a space before the dashes.  Then see if it boots.  If that doesn't work, you can instead try "ide=nodma" as a boot option.

Let us know how it goes.

ide=nodma didnt change anything.

But    irqpoll pci=noacpi noapic nolapic acpi=off   
Gave me the samme message as above, but without all the Level Low IRQ, and PCI interuption stuff..

So i guess thats progress. But it still freezes..

---

### Post by fresch1 on 2007-02-21
After using  irqpoll pci=noacpi noapic nolapic acpi=off 
the boot freeze here:

[IMG]http://frip.dk/helious/Ubuntu2.jpg[/IMG]

---

### Post by fresch1 on 2007-02-22
I Just got the DVD version downloaded, and it did the same, but it also had the option to do a OEM installation, and that worked.

After the install it does the same though when i start up Ubuntu.

PLEASE! It cant be true that NOONE can help me with this problem.
I have a normal PC, and im just trying to install Ubuntu.

---

### Post by ramjet_1953 on 2007-02-22
I know it's a pain, but try downloading the alternate CD and install with that.

Unfortunately, not all systems want to play with the live CD.

The alternate CD is not a graphical installer, but is still quite intuative and you should be able to understand it OK.

ps, Try to burn the iso at 4 X, as anything faster can be a problem for ANY iso.
Also, don't use cheap media. It has a habit of dying very quickly.

Regards,
Roger :cool:

---

### Post by fresch1 on 2007-02-22
> **ramjet_1953 said:**
> I know it's a pain, but try downloading the alternate CD and install with that.

Unfortunately, not all systems want to play with the live CD.

The alternate CD is not a graphical installer, but is still quite intuative and you should be able to understand it OK.

ps, Try to burn the iso at 4 X, as anything faster can be a problem for ANY iso.
Also, don't use cheap media. It has a habit of dying very quickly.

Regards,
Roger :cool:

The DVD version includes the "DosLike" installer, and as i posted before, it installs perfectly, but still gives me a freeze when i start up Ubuntu afterwards.
Im using good DVDs, and im burning with the lowest speed possible.
I dont think thats the problem

If you look at the point where it freezes it looks like something with my hardware?

---

