---
title: "Installer Hangs on &quot;mounting root file system&quot;"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by jfred1989 on 2007-01-04
I know this problem has been addressed before so sorry to bother you but I'm getting frustrated finding a solution. When loading the live CD (6.06) i get the error 

```
1717905.55600 Hdc: timeout waiting for DMA
```
 and 
```
Hdc: drive not ready for command
``` 

when attempting to mount root file system.  I tried installation with the alternate install cd which succeeds but does not load x.  I don't too much else to give you other than the specs of my system. 

The HD is wiped clean. Intel 845 chipset and celeron processor. 256 mg ram. integrated intel extreme graphics. 40 gig hard drive. 

Also i checked the cd's for errors and they come back clean. 

Thankyou for your help. I will gladly do my own research if someone gives me a direction to look in.

---

### Post by jfred1989 on 2007-01-07
I don't know what to do. I'm getting the same errors on 6.10. I have also tried playing with various BIOS settings including disabling plug and play OS.  Any hints or suggestions are welcomed. 

thank you

---

### Post by adam0509 on 2007-01-27
F6 + irqpoll

Thanks to answer if it works for you

---

### Post by e_james on 2007-01-27
The following might help. It worked for me. (ubuntu 6.06)

At the initial menu press the escape key and exit the menu. Then type "live noapic nolapic acpi=off" for the "live" CD or "install noapic nolapic acpi=off" for the "alternate install" CD.

If the install works, these settings will be incorporated into the normal startup but not into the recovery startup. You will need to edit the grub menu if you need them for recovery.

---

### Post by abstrakt on 2007-02-03
> **adam0509 said:**
> F6 + irqpoll

Thanks to answer if it works for you

Hey this worked for me, even though I wasn't the original poster I thought I'd let you know.

I was having problems installing 6.10.  Here's a link to the entire post: [http://www.ubuntuforums.org/showthread.php?t=352435](http://www.ubuntuforums.org/showthread.php?t=352435)

Thank you for this bit of information!

---

### Post by e_james on 2007-02-04
abstrakt

Thanks for the info. You're welcome. I picked it up in the same way from someone else.

---

### Post by zek725 on 2007-04-10
I solved the problem by changing the installCD and it worked!

---

