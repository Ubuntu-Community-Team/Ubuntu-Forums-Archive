---
title: "Error at mounting volume"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by zenguitar on 2006-10-21
I'm super new to ubuntu, like today to be exact :) I've been around computers forever but always been a windows guy and just need to experiment with something new for a change and I hit a wall right off.

I downloaded the Intel x86 desktop of ubuntu, I can boot from the CD fine and I begin the start or install choice and it dies at mounting the volume. It hangs there for quite a while and then a bunch of repeating text mentioning IRQ 100 something, I can't remember the exact number but it just goes on forever and I have to power off the computer.

I'm using a P4 3.0ghz, Asus P4C800 Deluxe MB, 1.5gb memory, the hard drive is on the sata controller and a ATI 9800 Pro video card. 

I can boot my laptop into ubuntu with the same cd just fine if that means anything.

---

### Post by jorn on 2006-10-21
I would try the alternate-cd. There might be problems with some hardware using live-cd. Some people has encountered issues with sata,though I havn't.

---

### Post by zenguitar on 2006-10-21
Ok, I'll give that a try and see how it goes...

---

### Post by tuxrtfm on 2006-10-21
Also try setting "Plug in Play OS" to NO in your bios if it is not already.
Ubuntu hung on my Asus K8N until I changed that setting.

---

### Post by zenguitar on 2006-10-21
I'm trying the alternate cd right now and it goes farther into the setup but fails to mount the cd-rom. I already have the plug and play OS set to no. I'll try again in a moment with it set to yes.

---

### Post by zenguitar on 2006-10-21
hdd: cdrom_pc_intr: the drive appears confused
irq 185: nobody card try booting with the irqpoll option

That message comes up right after choosing to boot in text mode. Almost exactly the same message I was getting with the first CD I made.

With plug and play OS set to yes, it takes longer to continue and still fails to mount the cd-rom

---

### Post by zenguitar on 2006-10-21
Anyone got any ideas? Is is the CD-Rom? I have two and tried booting from both of them, same problem. 

I can see that the error message tells me to try booting with the irqpoll option, but I don't know how to do that.

---

### Post by jorn on 2006-10-22
I,m not sure of this how to boot into irqpoll:
Press F6 for other options. At the end of the bootoptins showing up type  irqpoll.Someone please correct me if I'm wrong.

To eliminate things you could replace your cd-drive and maybe the sata disk one by one to see where the problem is. I don't think it's the .iso.

---

### Post by zenguitar on 2006-10-22
I agree, I don't think its the .iso either. Certainly because it did install perfectly fine on my laptop.

I do have an IDE drive in my closet that I can toss in there and see what happens. I'm sure I have another cd drive as well, have to check. I have two cd drives installed right now, I could give just using one a whirl.

I'll do this stuff in the morning and post back what happens.

---

### Post by jorn on 2006-10-22
I would appreciate that.

---

