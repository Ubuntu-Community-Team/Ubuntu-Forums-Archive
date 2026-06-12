---
title: "[SOLVED] Using ENVY"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by mongoose_za on 2008-01-02
Hi,

I previously installed my ATi card with ENVY but for some reason i remember having to reset my X11 conf. I think that the ATi card is now not using the drivers i installed with ENVY.  I have the Drivers on my machine and my question is,

[LIST=1]
[*]is there a way i can get ENVY to install my drivers but without having to download them from the net? But to instead find the drivers off my HDD then proceed with it's normal instructions?
[/LIST]

thanks

---

### Post by overdrank on 2008-01-02
> **mongoose_za said:**
> Hi,

I previously installed my ATi card with ENVY but for some reason i remember having to reset my X11 conf. I think that the ATi card is now not using the drivers i installed with ENVY.  I have the Drivers on my machine and my question is,

[LIST=1]
[*]is there a way i can get ENVY to install my drivers but without having to download them from the net? But to instead find the drivers off my HDD then proceed with it's normal instructions?
[/LIST]

thanks

HI and I can not actually answer your question but if you use Envy to install the drivers manually you can choose which version of the ati driver that worked best on your system. SO if you know the version of the driver then just choose to install manually. I hope this helps and good luck!

---

### Post by ~LoKe on 2008-01-02
This should work.

```
sudo envy -t
```
Press "5", then press "1", then it'll give you a list of drivers:
1. 7-12
2. 8.40.4
3. 8.28.8

Is that what you were looking for?

---

### Post by mongoose_za on 2008-01-03
almost what i'm looking for.
I've got the new version 8.443.1 and want ENVY to use these drivers..
But i'm going to install the ones that come with ENVY anyway. 8.40.4

Thanks!

---

### Post by mongoose_za on 2008-01-03
thanks for your input..
i did it manually using the [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat712-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat712-inst.html)
which worked fine.

---

