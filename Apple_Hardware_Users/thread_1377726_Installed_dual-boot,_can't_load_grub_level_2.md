---
title: "Installed dual-boot, can't load grub level 2"
date: 2010-01-10
forum: Apple Hardware Users
---

### Post by Aybara on 2010-01-10
I've installed Ubuntu many times on my MBP 5.1 in a dual-boot configuration, but removed it because of the heat issues. Since this reportedly has improved, I thought I'd try again. I followed the guides like before, and the install seemed to go well, but no.

When I boot rEFIt shows me 3 options. Mac OS, Linux and "Legacy OS". If I try the two last ones, it says its loading Grub stage 2, and then gives me the prompt "grub>". When I try to use the Partition editor in rEFIt it gives an error message about something non-standard, and says it won't touch anything.

I'm not sure, but I think this started when I installed Snow Leopard. At first it would not install, due to changes rEFIt had done. I had to re-bless <something> to make it work again.

So, any ideas for fixing/troubleshooting?

---

### Post by linuxopjemac on 2010-01-11
I would reinstall Grub first and then sync the partition tables. From the live CD, go to a shell and perform the following:

```
grub-install /dev/sda
```

(sda is your hard drive containing Linux, check that)

Then boot into rEFIt and sync the partition table with the Partition tool.

If that still does not solve your problem, look here:
[http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

---

### Post by Aybara on 2010-01-11
Thanks for the info. I followed the instructions from the link without any error messages reported. When I rebooted Mac OS and "Legacy OS" were the only choices. I tried the partitioning tool, and it still says "gptsync: GPT partition of type 'Unknown' found, will not touch this disk".

If I try to boot the so-called "Legacy OS", the screen just goes black. Mac OS still boots.

---

### Post by Aybara on 2010-01-11
I take it back :)

For some reason I had to boot 2 times before it started working...

---

### Post by linuxopjemac on 2010-01-11
happy to hear, welcome back to the Ubuntu club :D Now stay with us ;)

---

### Post by Aybara on 2010-01-11
Heh. Thanks. I`ve actually been running Ubuntu since Dapper :)

New problem now. I did an apt-get update && apt-get dist-upgrade. When it upgraded grub I chose to keep the installed version of my config file. When I try to boot Ubuntu now it just prints `GRUB GRUB GRUB GRUB` until it fills my screen. I`ll try to redo the instructions from before and see how that works out.

---

### Post by Aybara on 2010-01-11
That did the trick, and never have everything worked so smooth out of the box :D

---

### Post by linuxopjemac on 2010-01-12
great to hear again....

---

