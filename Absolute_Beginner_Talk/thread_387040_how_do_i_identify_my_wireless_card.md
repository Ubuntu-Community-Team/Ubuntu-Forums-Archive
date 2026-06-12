---
title: "how do i identify my wireless card?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by thejones on 2007-03-17
can anyone tell me how to find out what model of wireless card i have?

i have the dreaded broadcom card, and i tried using ndiswrapper on my driver. but it keeps telling me that it is invalid.

i think it might help if i try an alternat driver, but i cant go looking for one if i dont know my model number. see where i am coming from? 

i know its a 43xx, thats what the driver says, but isnt there a number that should go in the x's?

or maybe im doing the whole damned thing wrong. who knows....... 

thanks,
jones

---

### Post by overdrank on 2007-03-17
> **thejones said:**
> can anyone tell me how to find out what model of wireless card i have?

i have the dreaded broadcom card, and i tried using ndiswrapper on my driver. but it keeps telling me that it is invalid.

i think it might help if i try an alternat driver, but i cant go looking for one if i dont know my model number. see where i am coming from? 

i know its a 43xx, thats what the driver says, but isnt there a number that should go in the x's?

or maybe im doing the whole damned thing wrong. who knows....... 

thanks,
jones

Hi if you go to terminal and type in lspci that will tell you the type of card. good luck

---

### Post by thejones on 2007-03-17
thank for the tip. i found out that i have a 4311. now, does anyone know if there is an alternate driver that i can use instead of the generic 43xx driver?

---

### Post by Bachstelze on 2007-03-17
No. As you have a Broadcom chip, your only options are bcm43xx and ndiswrapper.

---

### Post by thejones on 2007-03-17
hmmm.

well then, do you have any idea why ndiswrapper 1.38 would repeatedly tell me that the driver is bad? should i try to download it from a different source?

---

### Post by SactoBob on 2007-03-17
You can try some more drivers, and search the hardware compat. lists. but a number of Broadcom chips will not work, or will work only with more time invested than you may want to invest.  The fellow who wrote the Ub untu Bible talks about how he spent a summer trying to make one work.   Broadcom is maybe public enemy number 1 in not helping Linux by making info available.

It is not a happy sign that ndiswrapper does not like your driver.

---

### Post by Ozor Mox on 2007-03-17
I have a Broadcom BCM4309 chipset and ndiswrapper did not work for me. However, bcm43xx-fwcutter worked perfectly. You probably need to run it on the bcmwl5.sys file, as I did.

---

