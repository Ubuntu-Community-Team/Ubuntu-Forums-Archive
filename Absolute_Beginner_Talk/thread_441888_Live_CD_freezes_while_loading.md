---
title: "Live CD freezes while loading"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2007-05-13
I just got a new HP DV6308NR and I downloaded the ISO for fiesty (64 bit desktop) but now I keep having one of two problems when trying to load the live CD. Either the boot will freeze while Loading hardware drivers or after it says configuring network interfaces it will go to the next line but be blank. Also, when it will get to the network interfaces part it has several errors about having trouble loading hardware drivers. Should I try downloading the alternate CD and use that?

---

### Post by deadgobby on 2007-05-13
Try the 32 bit cd and it should go. There is not a whole lot of support for 64 but kernel. More software with the 32 but kernel. 
 If it hangs try this hit F6 and enter the following paramaters

irqpoll pci=noacpi noapic nolapic acpi=off 

Gobby

---

### Post by mongooseman1128 on 2007-05-13
Okay thanks, I wanted to try asking before I spent the time to download another image. On a side note, I'm usually pretty smart as far as hardware goes. This computer comes with an AMD 64 X2 dual core. Isn't the processor made up of two 64 bit processors or is it just 32 bit processors? Either way though, shouldn't it be seen as a 64 bit system?

---

### Post by deadgobby on 2007-05-13
Yes, it should be seen as a 64 bit. If the live CD does not run either it cannot confiq  the Hardware or a bad ISO. As I said the 64 bit kernel can be a bit buggy. The same with Vista 64 bit kernel too. It could be a lack of 64 but drivers for your hardware. 
Gobby

---

