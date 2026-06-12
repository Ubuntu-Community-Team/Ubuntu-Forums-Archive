---
title: "How to revert from gutsy gibbon to feisty fawn?"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by lalji on 2007-11-03
My laptop can no longer wake from suspend now that I've upgraded from feisty fawn to gusty gibbon. Looking at posts on the forum, I'm clearly not the only one, and who knows when it might be sorted out. Comparing my meager tech skills vs the complexity of the problem, I'd like to execute a tactical retreat (run away!) back to feisty fawn ... but I don't know how to do that.

Q: how do I switch from gutsy gibbon to feisty fawn?

Thanks!

---

### Post by Partyboi2 on 2007-11-03
I think you would have to do a clean install of feisty.
Atleast I havent heard of any other way.

---

### Post by natehatewindows on 2007-11-03
yeah i was kinda wondering the same thing. I have a toshiba and it has acpi issues now (no sounds with acpi, sounds when acpi-off) so i kinda want to run too :)

---

### Post by natehatewindows on 2007-11-03
no you can somehow use the feisty kernel,,,,,without doing a complete reinstall.

---

### Post by Sef on 2007-11-03
> no you can somehow use the feisty kernel,,,,,without doing a complete reinstall.

No, you need to do a complete reinstall.  Gutsy's packages will not work with Feisty.

---

### Post by natehatewindows on 2007-11-03
no i pretty sure your wrong, these guys at my bug problem have done it just fine. [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

---

### Post by PmDematagoda on 2007-11-03
> **Sef said:**
> No, you need to do a complete reinstall.  Gutsy's packages will not work with Feisty.

Sadly, I can attest to that, I installed some Gutsy packages on Xubuntu 7.04 which includes the libc6 package and now Ubuntu can't install anything:(. So be careful with what you download from the Ubuntu Packages website and make sure that you download the proper packages for the correct Ubuntu version.

---

### Post by PmDematagoda on 2007-11-03
> **natehatewindows said:**
> no i pretty sure your wrong, these guys at my bug problem have done it just fine. [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

It doesn't apply to all packages, but it would mean a risk as you could damage Ubuntu as well. I faced the real big problem only after I replaced the libc6 package of 7.04 with the one meant for 7.10.

---

### Post by yogo on 2007-11-03
Yeah a clean install of Feisty is what I did and Feisty is better than before,  most likely due to all the trial and error that went on with my original install.  This re-install, I knew  much more to get it up and running right.

---

### Post by Clickbg on 2007-11-03
Well it is not impossible, but it is a hard work. First you need to trackdown all old packages for Feisty, then remove the Gutsy packages. Change the apt-get responsibilities with Feisty ones and install Feisty packages. Sounds easy, well you have to track almost 10000(or 1000 for basic work of Linux) packages so a total reinstall is the best way to save time.

---

### Post by PmDematagoda on 2007-11-03
It also is very risky, you would probably only have a 10% or lower chance of success.

---

### Post by lalji on 2007-11-03
Thanks for your responses. A complete reinstall of feisty seems the way to go.

---

