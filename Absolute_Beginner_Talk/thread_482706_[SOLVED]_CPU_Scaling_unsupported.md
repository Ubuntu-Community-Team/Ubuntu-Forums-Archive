---
title: "[SOLVED] CPU Scaling unsupported"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Webby_s on 2007-06-24
Ok I have searched high and low in the forums and have not found a similar problem...

I have an old Gateway that I am trying to install some Xubuntu action on .... I had gotten all the way through the install and even with the 65% anthy problem, made it through that. But now when I boot up from the HDD it comes down to the part (where I believe) it is checking the CPU. It then says something to the effect that the CPU doesn't support scaling .... something with Powernowd but says ok on the right of the screen. It then continues to do about 5 more checks (all with ok's) and then the whole computer turns off. I have read about this powernowd and how to unistall it from the terminal but I can't get to a terminal to change things since it is not booting up. Any ideas of what I may be able to do? If anything? I hope I can.

Thanks   -Webby

---

### Post by Webby_s on 2007-06-24
God I hate to do this but I seem to be so close, I am inches away from getting to my first experience with ubuntu. But here it goes.... Bump.

---

### Post by shae on 2007-06-24
Would you happen to know what is inside your laptop?  A model would be ok, but the components would be great.  One possible thing you could try is to boot the kernel without acpi.  I would say we should try to see if anyone else has had a similar problem on the same laptop.

---

### Post by Webby_s on 2007-06-24
This is a gateway desktop that has a lntel Celeron (peice of crap). It originaly had Win ME. I am hoping that it has at least 128mb of ram but my guess is it probably doesn't. I loaded XP on it awhile back and it ran SLOWWWWW, I also added a CD-RW drive to it awhile back (this was all for my parents). Model number? ... boy I don't know ....It says that it was manufatured on 6-30-00. There is a aluminum heat sinc over the processor so I can't take a look at that.

Just tell me to go build my own rig with a new case and power supply and a celoron core 2 cuo processor.... oh wait my wedding is coming up and if I buy one more thing for myslef she will cut my jewels off.

---

### Post by Webby_s on 2007-06-24
Anybody? Any thoughts? Sorry to bump but just want to maybe get this to work. Thanks again guys/gals.

---

### Post by Webby_s on 2007-06-25
Sorry... Bump

---

### Post by shae on 2007-06-25
I would say try booting it with acpi=off in the kernel parameters.  To do this, go to the grub boot menu.  Then press e to edit the parameters temporarily.  Go down to the kernel like and add ```
acpi=off
``` to the end.   Then press enter then b.  Report back if that will get it to allow you to boot or not.

---

### Post by Webby_s on 2007-06-26
Thanks for the reply. I did as stated (went in and added acpi=off) and it happened again. I am starting to beleive that it is not a CPU problem. (what it is I don't know) So I may give up on Xubuntu (unless I have others with ideas) and just focus on building a new rig and installing Ubuntu. Thank again all and See you back when I have a new setup!

---

