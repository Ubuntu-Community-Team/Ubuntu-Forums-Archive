---
title: "HP laptop and Ubuntu"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by DaemonLee on 2008-02-27
Hey, 

I have a DV6353US model from HP, that includes the following; 

160gb
2gb RAM 
LightScribe DVDRW drive. 
2.0ghz AMD Turion x2
Broadcomm 802.11g WiFi
And then 10/100/1000 Ethernet

Here's the problem, I try to install. It freezes at networking on LiveCD boot. 

Any ideas? Anything?

I've tried the Alternate-Installer, the AMD 64-bit CD, and the regular 32-bit CD. All freeze.

---

### Post by jeffus_il on 2008-02-27
Did the alternate installer give you any text to indicate an error or as to what was running when it froze? Could you do <ctrl><alt><f1> in the regular 32 bit install to see some console output?

---

### Post by koen plessers on 2008-02-27
Hello

Have you tried the NOAPIC option at boot (APIC is the replacement for the old PIC chip that used to come imbedded on motherboards that allowed you to setup interrupts for your soundcard, ide controllers, ect.)?

Bye

Koen Plessers

---

### Post by ErusGuleilmus on 2008-02-27
I used to have a similiar issue. I got around it by adding "vga=792" and "noapic" to the kernel boot parameters.

---

### Post by stchman on 2008-02-27
> **DaemonLee said:**
> Hey, 

I have a DV6353US model from HP, that includes the following; 

160gb
2gb RAM 
LightScribe DVDRW drive. 
2.0ghz AMD Turion x2
Broadcomm 802.11g WiFi
And then 10/100/1000 Ethernet

Here's the problem, I try to install. It freezes at networking on LiveCD boot. 

Any ideas? Anything?

I've tried the Alternate-Installer, the AMD 64-bit CD, and the regular 32-bit CD. All freeze.

Did you try the safe graphics mode?

---

### Post by DaemonLee on 2008-03-11
> **ErusGuleilmus said:**
> I used to have a similiar issue. I got around it by adding "vga=792" and "noapic" to the kernel boot parameters.


Works on install, by doing F6 and then typing in the above.

Problem: My onboard wifi works, but only on B networks, and only allows 1mb transfer speeds. 

It is a Broadcomm chipset...Any way to make this better or not?

---

