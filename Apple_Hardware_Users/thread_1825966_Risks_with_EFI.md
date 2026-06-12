---
title: "Risks with EFI"
date: 2011-08-16
forum: Apple Hardware Users
---

### Post by Jaxilian on 2011-08-16
Hi
I was thinking on following this guide I found: [http://yoodey.com/full-guide-instalation-ubuntu-natty-1104-macbook-pro-15-inch-single-partition](http://yoodey.com/full-guide-instalation-ubuntu-natty-1104-macbook-pro-15-inch-single-partition)

I wish to shorten the EFI boot time, but NOT use rEFIt.

any risks using the command?: **bless --device /dev/disk0s1 --setBoot --legacy --verbose**

any who tried this and reverted back to MacOS at some time? No matter how much I love Ubuntu I wish to have the possibility still to change to MacOS.

---

### Post by eti.que on 2011-08-16
I just did that with a Mac Mini late 2010. I "blessed" sda (and it boot much faster) and just reinstalled Mac OS X SL without any trouble.

Now I'm trying to install a vanilla Natty on it but that's another story (the Ubuntu installer keeps hanging... not related to the bless though)

---

### Post by Jaxilian on 2011-08-16
thanks! It works! :D

My Macbook boots up at 37 sec. Before "bless" it was at 1 min 10 sec

When I have MacOS on it, it only takes 22 sec though. :(

---

### Post by conundrumx on 2011-08-16
Blessing the partition is just a marker on the disk that EFI checks for.  There's no harm, no risk.

---

