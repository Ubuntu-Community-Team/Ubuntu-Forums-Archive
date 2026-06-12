---
title: "Ubuntu won't boot when new updates were installed!"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by zero13 on 2007-06-24
I just installed ubuntu on my laptop today and everything went well. I booted up Ubuntu and it said 69 updates were available. I installed them and rebooted my laptop. While booting (when the list of things come up) my computer gets stuck at this message: "[     300.204000] bcm43xx: Error: Microcode 'bcm43xx_microcode4.fw' not available or load failed." 
How do I fix this????? Ubuntu was working perfectly until I installed those updates!! someone help! :(

---

### Post by Nekiruhs on 2007-06-24
Can you post your menu.lst? Or atleast the options it gives you at the boot menu? I have a hunch it has to do with the .16 kernel in the updates. It killed my machine too. See if booting to the .15 kernel works. Sounds like it is having issues with your broadcom card restricted modules.

---

### Post by zero13 on 2007-06-25
> **Nekiruhs said:**
> Can you post your menu.lst? Or atleast the options it gives you at the boot menu? I have a hunch it has to do with the .16 kernel in the updates. It killed my machine too. See if booting to the .15 kernel works. Sounds like it is having issues with your broadcom card restricted modules.

i fixed it. I just formatted my HDD and installed ubuntu again. I then tried installing the new updates again and they worked! Someone can lock/delete this thread! :)

---

