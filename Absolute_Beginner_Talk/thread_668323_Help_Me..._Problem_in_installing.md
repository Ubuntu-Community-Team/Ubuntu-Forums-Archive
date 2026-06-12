---
title: "Help Me... Problem in installing"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by anuj_inurdreamz on 2008-01-15
Hi i  Anuj..

i hav bought a unbuntu7.10 dvd from my frnd...
when i boot that cd one screen appers and and there is option to install the ubuntu....
when i press enter at it , a black page appears and some problem is written on it in loading it....



[0.42000]..MP-BIOS bug:8254 timer not connected to IO-APIC
[0.42000] Kernel Panic-not syncing:IO-APIC+ timer doesnt work! boot with apic=debug and send a report.
then trying booting with the 'noapic' option.





plzz help me.

---

### Post by mike555 on 2008-01-15
Are you sure you have the right version (32 or 64 ) and have you tried any other distros?   or it might be a graphics card issue, do you have an ATI card? ..........   more info will help us help you ........

---

### Post by anuj_inurdreamz on 2008-01-15
my configuration is

AMD Athlon 64 x2 dual core processor 4400+
1 gb ram
250 gb hdd
ausu motheboard m2n mx se




i dont have any grafic card.. its onboard nvidia dispaly card..

---

### Post by anuj_inurdreamz on 2008-01-15
i dont know is it for 32 or 64.. how to find that...?>??????????

---

### Post by dstew on 2008-01-15
The LiveCD is having trouble with your hardware. The error message suggests a fix. Try this. At the first screen, where you see the choices that include Start or Install Ubunut, press F6. This will enable you to enter a kernel parameter that stops the advanced programmable interrupt controller, which the LiveCD is having trouble with. Add **noapic** to the end of the kernel line, then press enter.

---

### Post by hyper_ch on 2008-01-15
Well, for AMD 64 you can use either, 32- and 64-bit ;)

---

