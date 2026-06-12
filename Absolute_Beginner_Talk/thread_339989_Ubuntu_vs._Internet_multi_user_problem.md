---
title: "Ubuntu vs. Internet: multi user problem"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2007-01-16
I work as a tech consultant for my University and we have very little Linux support (although we are trying to improve this). The problem is that the only patch we officially endorse doesn't help all users (ironically including myself). I am working with someone I will be calling back shortly and I was wondering if anyone had thoughts on the following fix:

sudo arp -s (gateway IP address) (gateway mac address)

The problem is that Linux and ResNet (what we use to authenticate users) don't "talk" well, so we need to either make ResNet think that the computer isn't Linux. Routers help occasionally, some enter dhclient when they boot, but any advice will be greatly appreciated.

---

### Post by igknighted on 2007-01-16
> **nonpareilpearl said:**
> I work as a tech consultant for my University and we have very little Linux support (although we are trying to improve this). The problem is that the only patch we officially endorse doesn't help all users (ironically including myself). I am working with someone I will be calling back shortly and I was wondering if anyone had thoughts on the following fix:

sudo arp -s (gateway IP address) (gateway mac address)

The problem is that Linux and ResNet (what we use to authenticate users) don't "talk" well, so we need to either make ResNet think that the computer isn't Linux. Routers help occasionally, some enter dhclient when they boot, but any advice will be greatly appreciated.

I also go to a school using resnet, and I never once had an issue with linux connecting to it.  I am now off campus, but I have linux using friends on campus who haven't had issues either.  I wonder if there is some patch available from the makers of resnet or if there is some other setting that needs to be changed for better linux compatability.

---

### Post by nonpareilpearl on 2007-01-16
> I wonder if there is some patch available from the makers of resnet or if there is some other setting that needs to be changed for better linux compatability.
If you know of what this patch would be, that would be awesome. I know it's not just us, almost all Linux user's on campus experience difficulty of some sort, and it requires different fixes for most (even for the several Edgy users).

---

