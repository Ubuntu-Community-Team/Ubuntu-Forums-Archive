---
title: "[SOLVED] recent batch of updates."
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by terry_gardener on 2007-11-14
I just have 2 quick questions 

1. why is it when doing updates and it updates the kernel even if it keeps the same name it brakes the nvidia driver install. 

2. after the recent batch of updates it even changed the keyboard settings to US from UK. 

I have fixed the 2 problems above 1. by uninstalling and reinstalling the driver using envy and 2. editing the xorg.conf file since updating the keyboard preference for some reason didn't work. 

if you have any ideas please enlighten me. 

ps question 3. is there any way to stop what happens in question 1 from happening 

thanks

---

### Post by Nano Geek on 2007-11-14
> **terry_gardener said:**
> I just have 2 quick questions 

1. why is it when doing updates and it updates the kernel even if it keeps the same name it brakes the nvidia driver install. 

2. after the recent batch of updates it even changed the keyboard settings to US from UK. 

I have fixed the 2 problems above 1. by uninstalling and reinstalling the driver using envy and 2. editing the xorg.conf file since updating the keyboard preference for some reason didn't work. 

if you have any ideas please enlighten me. 

ps question 3. is there any way to stop what happens in question 1 from happening 

thanksDo you remember what kind of updates they were?

---

### Post by terry_gardener on 2007-11-14
sadly i cant remember the updates but it did 16 all at the same time. 

i remember seeing the image .22.14 generic being installed but cant remember the other updates didn't really take that much notice just installed them since the where updates for the system. 

sorry i cant give a better answer.

---

### Post by Steveway on 2007-11-14
Did you use a non-standard way to install your drivers?
For example envy or did you use nvidia's installer?
If so then remove this and install the driver with the restricted-driver-manager or through Synaptic.
It will then be updated together with the rest and shouldn't break.

---

