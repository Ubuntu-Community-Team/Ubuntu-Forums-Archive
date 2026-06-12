---
title: "grub settings"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by MiCovran on 2006-09-10
Anyone knows how to change grub settings? The default is wait 10s to boot Ubuntu. How can I change the time and OS to boot?

---

### Post by Najand on 2006-09-10
Edit /boot/grub/menu.list using vim or gedit or something similar. Don't forget sudo as it needs root previlege.

---

### Post by jordanmthomas on 2006-09-10
Also, try searching the forums for GrubEd.  It provides an easy way of editing menu.lst
If you're comfortable editing files, though menu.lst is well documented.

Oh, and Najand,
it's not menu.list, it's menu.lst     ;)

**edit**

You'll be looking for the timeout option

---

### Post by bulldog on 2006-09-10
To shorten the time look for this

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

---

### Post by shoot2kill on 2006-09-10
i have a similar problem, which the above answers dont solve...

i get a message saying LOADING GRUP, PLEASE WAIT....

now, on my laptop, this message lasts a split second before the menu comes up, and on this PC, i have to wait about 1-2 mins before the menu comes up..

any ideas

---

