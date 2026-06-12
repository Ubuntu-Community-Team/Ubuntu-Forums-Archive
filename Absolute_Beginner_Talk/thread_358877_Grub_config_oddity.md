---
title: "Grub config oddity"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Seteo-Bloke on 2007-02-11
I apologise in advance if this is a simple answer but I've just started getting my head into Ubuntu.

I've got a dual boot setup with FC6 & Ubuntu installed on seperate partitions. FC6 installed first.

So I've a small issue with Grab since I installed Ubuntu. The "other operating systems" (or whatever it says I forget now) section on boot is showing Ubuntu boot options as well as showing Ubuntu boot options in the default choices above it.

So I guess something didn't work out too well during the Ubuntu installation with Grub? Ok, so I took a look in /boot/grub/menu.lst but the file config looks fine. FC6 options are there at the bottom of the file so it looks like the Ubuntu install did update the file ok but for some reason the inital boot grub screen isn't showing that FC info.

Any idea's? Many thanks in advance.

---

### Post by Ocxic on 2007-02-11
can you post your /boot/grub/menu.1st file?

---

### Post by geek_Man on 2007-02-12
Actually that's "/boot/grub/menu.lst". Like a list file, not the 1st one.

---

