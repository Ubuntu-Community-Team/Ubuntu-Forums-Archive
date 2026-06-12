---
title: "messed up partitoning"
date: 2012-04-07
forum: Apple Hardware Users
---

### Post by derxen on 2012-04-07
After a botched job of trying to install ubuntu (12.04 beta) on a G5, I have a partitioning table that looks like this:
sda1 Apple partitioning map
sda2 Apple bootstrap
sda3 Apple HFS
sda4 Apple HFS
sda5 Apple bootstrap
sda6 Apple unix
sda7 Apple unix (swap)
sda8 Apple free
sda9 Apple free

sda5 to 7 is where ubuntu was installed. Ubuntu does not boot, and when I run it from usb it gives me an error: 'bootstrap partition type is wrong. Apple HFS should be Apple-bootstrap.'

Can anyone help? Is there a way to repair this? Mac OSX still boots fine, btw, and I need to keep it that way.

thanks
derxen

---

### Post by derxen on 2012-04-09
I solved it. I removed sda5, installed yaboot into sda2 (running yabootconfig from usb with the target option to direct it at sda2), edited yaboot.config, ran ybin -v (again directing it at sda2). It's a bit tricky, took much of the day.

---

