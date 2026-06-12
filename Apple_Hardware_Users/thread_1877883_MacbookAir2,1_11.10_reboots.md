---
title: "MacbookAir2,1 11.10 reboots"
date: 2011-11-08
forum: Apple Hardware Users
---

### Post by shivathreya on 2011-11-08
Hi,

I was able to successfully install 11.10 from livecd on MacbookAir 2,1.

However, it doesn't boot. It shows the grub screen and when I select the appropriate line it just reboots.

I have tried with various options like noacpi, acpi=noirq, pnpacpi=off...

Sometimes it boots and works OK. Otherwise most of the time it konks.

I also tried booting through OSX and then back to Linux. It doesn't help.

Any answer would be great.

Shiva

---

### Post by shivathreya on 2011-11-11
Well.. Thanks for the help (I didn't get any).

Found out that I should not boot from refit. I hold ALT key while booting and select the windows HDD. When the grub is loaded i just choose the following kernel option ..... noacpi=off.

It boots fine and both the cpu's work.

Only thing not working properly is fan which always runs at 6200 rpm.

Shiva

---

