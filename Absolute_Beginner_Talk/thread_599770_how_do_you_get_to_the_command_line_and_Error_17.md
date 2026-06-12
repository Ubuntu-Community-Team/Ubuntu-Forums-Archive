---
title: "how do you get to the command line? and Error 17"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by AstroBomber on 2007-11-01
A couple days ago, I decided that I would try installing Linux on my old computer. What better way to learn than to do? I decided that it wouldn't matter if I killed the old computer in any way (although I would prefer not to). So, I installed Ubuntu. Everything went fine until I took the Ubuntu CD out. I tried booting up newly installed Ubuntu, and I got GRUB Error 18. So, I stuck the CD back in, restarted and went to the partion manager thing. I changed one of the drives to the Linux file system I believe. I restarted with the CD in, and this time I got GRUB Error 17. Is anyone able to give me a slow, jargon-free, step by step way of getting rid of Error 17 and 18?

My other question is how do I access the command line? Everyone talks about this mystical command line, but I don't see it anywhere. 

I can post my computer's specs if it would be relavent in fixing these problems.

---

### Post by dfreer on 2007-11-01
Commandline can be found at **Applications > Accessories > Terminal**

As for the other question regarding GRUB error, can you tell us how you partitioned your hard drive? Did you manually partition it or did you use the guided partitioner?

---

### Post by AstroBomber on 2007-11-01
> **dfreer said:**
> 
As for the other question regarding GRUB error, can you tell us how you partitioned your hard drive? Did you manually partition it or did you use the guided partitioner?

I used the guided partitioner. I selected the option that said "erase previous contents of hard drive" (I wanted it to be a solely Linux computer) I also only have one hard drive in this particular computer.

I could show you my partitioner screen, how do you take a screenshot in Ubuntu?

---

### Post by Irony on 2007-11-01
> I could show you my partitioner screen, how do you take a screenshot in Ubuntu?

Same as in windows - hit the PrintScreen button or highlight the window and hit Alt+PrintScreen for a shot of the window only.

---

### Post by AstroBomber on 2007-11-01
I have (hopefully successfully) attached a screenshot of my partition editor.

---

### Post by oldos2er on 2007-11-01
There don't appear to be any bootable partitions on this disk--and why do you have a 36GB swap? That's a waste of space.
 What are the specs of this machine? Are there two hard disks?

---

### Post by AstroBomber on 2007-11-01
The specs on the machine are as follows:

Compaq Presario 5000

Disk: Quantum Fireball lct2040

CD Roms: Compaq DVD Rom DVD-116
Phillips CDD4801 CD-R/RW

Network Adapter: Realtek RTL8139 Family PCI Fast Ethernet NIC

Processor: AMD Duron

Sound: SoundMAX Integrated Digital Audio

About the swap file: I'm noobish enough not to know what a swap file does. But I've gone into the Ubuntu IRC channel, and I've been told to delete and reinstall my GRUB

---

### Post by Duck2006 on 2007-11-01
Do a reinstall again and see how it go's this time, it looks like you have two swap partitions and no root partition.

---

### Post by Billy_McBong on 2007-11-01
[COLOR="Blue"]it looks like you should change that huge swap partition to the root partition[/COLOR]

---

### Post by dfreer on 2007-11-01
It also looks like the guided partitioner failed you, it should've created a small swap partition, and then used the rest of the hard drive as 1 partition mounted at /. Sorry it didn't work out the first time, but you can always try again.

So, I'd say go back and reinstall as suggest above, only use the manual partitioner. At the very least you should have 2 partitions, one for swap and one for the root "/" partition. You may also wish to create a /home partition, in case you need to reinstall again you can format the root partition, and just remount the /home so all of your personal data will be intact.

EDIT: In this particular case, deleting GRUB will not help, you need a reinstall.

---

### Post by AstroBomber on 2007-11-02
I did a reinstall, and I have attached the recent screenshot of my partitioner screen.

I beleive I used the guided partitioner again. Which option should I have used? If I have to reinstall again, what exactly should I do? I got Error 18 again after reinstalling.

---

### Post by oldos2er on 2007-11-02
You might need to update the machine's BIOS. See [http://wiki.linuxquestions.org/wiki/GRUB](http://wiki.linuxquestions.org/wiki/GRUB)

---

