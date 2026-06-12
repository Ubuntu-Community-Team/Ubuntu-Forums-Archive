---
title: "how to make it go back to 386"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by beezyoh on 2006-06-25
ok when i first installed ubuntu, everything was working great when it was linux 2.6.15-25-386.... now its 2.6.15-25-686 and its giving me some issues, how do i make it go back to 386?

---

### Post by nemtudod on 2006-06-25
sudo apt-get install linux-386

or boot select the 386 kernel and remove the 686

---

### Post by PingunZ on 2006-06-25
look for it in synaptic, search for loinux and scroll to the kernel you want ;)

Grtz PingunZ

---

### Post by Kimm on 2006-06-25
sudo apt-get remove linux-image-686 linux-image-2.6.15-21-686 

That should fix it...

You'll want to boot into the i386 kernel first though (press Escape when you get to the Grup loader, and chose kernel)

---

### Post by beezyoh on 2006-06-25
thanks for the quick replies, u guys are great!

---

