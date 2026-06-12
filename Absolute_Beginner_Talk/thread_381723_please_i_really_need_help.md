---
title: "please i really need help"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by TheD0ct0r on 2007-03-11
Hi, i'm trying to install Ubuntu Edgy Eft 6.10 on my windows xp computer. I burnt ubuntu onto a CD from the Ubuntu website. Once the ubuntu sart up screen comes on, i press enter on "Start or Install Ubuntu", then a loading screen comes up. After that, some white data appears on the screen, then the screen goes black. I can hear the disk running in the hard drive, then it goes quiet. How do i resolve this??

---

### Post by Kateikyoushi on 2007-03-11
What is your video card ?

---

### Post by overdrank on 2007-03-11
> **TheD0ct0r said:**
> Hi, i'm trying to install Ubuntu Edgy Eft 6.10 on my windows xp computer. I burnt ubuntu onto a CD from the Ubuntu website. Once the ubuntu sart up screen comes on, i press enter on "Start or Install Ubuntu", then a loading screen comes up. After that, some white data appears on the screen, then the screen goes black. I can hear the disk running in the hard drive, then it goes quiet. How do i resolve this??

Hi did you follow the instruction on the how to burn,
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
If so you may have to burn at the slowest possible speed.
If you can give us some specs on the machine you are installing on.

---

### Post by TheD0ct0r on 2007-03-11
The video card is an "Intel(R) 82810E Graphics Controller (Microsoft Corporation)"
If it helps, the model of the computer is a "DELL Dimension L733R"

---

### Post by fuzZzball on 2007-03-11
Hi, I had the same problem with CD's. Try to burn it on a DVD, worked for me ;)

---

### Post by Kateikyoushi on 2007-03-11
I think that video card is the problem.

Boot from the cd at the menu press F6 then press E to edit the startupline and add add these options to the end of the line.

noapic
nolapic
pci=irqroute
pci=noacpi
acpi=off
pci=acpi
nolapic
framebuffer=false
linux irqpoll

I can not recall which helps with that video adapter but if nothing works try the alternate install cd which runs in text mode.

---

### Post by localuser on 2007-03-11
You can also try the alternate install cd to see if that helps.

---

### Post by TheD0ct0r on 2007-03-11
okay thanks a lot guys, i appreciate it.

---

### Post by Delvien on 2007-03-11
It might not be the CD, what kind of computer are you trying to run the Live CD with?

---

### Post by TheD0ct0r on 2007-03-11
DELL Dimension, Windows XP

---

### Post by rusty4r on 2007-03-11
I would make sure to follow these instructions to download and to burn the cd
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

---

