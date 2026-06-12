---
title: "wireless card dissabled"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by c0nfusedami on 2008-03-09
i am new to linux and  finally got it installed on an old computer i am trying to get on to my wireless network and i followed the steps from the help menu that tells me to check if the wireless card is disabled. i found out it is but it said nothing about how to enable it just that if it was enabled go on to the next step does anyone know how to turn on a wireless card with ubuntu

---

### Post by glennric on 2008-03-09
It may be disabled by hardware.  I know on the old laptop I have there is a switch to turn the wireless card on or off.  Check if you have something like that.  It could also be disabled in the bios.

---

### Post by handydan918 on 2008-03-09
It's also kinda hard to tell what kind of card you have. Maybe you could post the output of ```
lspci
``` and maybe then we can help.

---

### Post by c0nfusedami on 2008-03-09
it is a linksys wireless-g model no. WMP54Gs and there is no switch on the card itself to turn it on or off

---

### Post by handydan918 on 2008-03-10
Maybe you could post the output of
Code:

lspci

and maybe then we can help.

---

### Post by anewguy on 2008-03-10
Please do follow the advice above and go to a terminal window and type lspci and press enter, then post that output back here.

I suspect your chipset is Broadcom 4306, but we need to see that output before we can advise you further.  

:)

---

### Post by c0nfusedami on 2008-03-11
i ran the lspci code in my terminal and it came up as broadcom corporation BCM4306

---

### Post by anewguy on 2008-03-14
Sorry I didn't get back here until now.  Did you get your wireless working following any of the many Broadcom 43xx posts (including the restricted drivers) or do you still need help getting it going?

:)

---

