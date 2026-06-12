---
title: "MacBook Pro 5,1 b43/bcm43xx with broadcom 4322"
date: 2008-11-02
forum: Apple Hardware Users
---

### Post by mxweas on 2008-11-02
I have one of the new macbook pro's (5.1) I've finally got ubuntu booting correctly. Anyway, I can't seem to get the b43 driver working, I've tried compiling and using apt-get to install it. iwconfig does not show the wireless card. I've heard reports of b43 not working with the 4322 cards, but from what I've found the only thing b43 does not support is the wireless N functionality which is fine with me. I have been successful in getting broadcoms wl driver working, but it does not provide the same functionality as the b43 driver. Is there something I must do to load the b43 driver once installed? Has anyone had success with this driver on one of the new macbook pros?

Thanks,
Max

PS: Please don't suggest ndiswrapper, it does not provide the functionality I need (Monitor mode).

---

### Post by cyberdork33 on 2008-11-02
as far as I know, b43 does not work at all. You can try it, but you have to get the firmware for it to work. I think you need b43-fwcutter to do that.

---

### Post by mxweas on 2008-11-03
I used b43-fwcutter like it said in the tutorials but it still does not work... :( Do you know of a way to get monitor mode working with broadcoms wl driver?

Thanks,
Max

---

### Post by cyberdork33 on 2008-11-03
> **mxweas said:**
> I used b43-fwcutter like it said in the tutorials but it still does not work... :( Do you know of a way to get monitor mode working with broadcoms wl driver?

Thanks,
MaxNo, it is relatively new, so if there is a way it may not be known yet, and your other thread in networking & wireless probably has a better chance of getting that answered.

---

