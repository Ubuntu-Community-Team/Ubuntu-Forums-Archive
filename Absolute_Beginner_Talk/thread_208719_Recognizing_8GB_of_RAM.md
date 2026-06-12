---
title: "Recognizing 8GB of RAM"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by Bob Walsh on 2006-07-04
Anyone with a URL as to how much RAM Ubuntu (desktop and server installs) can recognize? Just got a Dell PE1800 with 8GB RAM; want to know if Ubuntu can do the job...

Thanks in advance!

---

### Post by nanotube on 2006-07-04
you might have to recompile the kernel, because by default the kernel is only set for a max of 4gigs of ram (you would have to set CONFIG_HIGHMEM64G).

other than that, i think it should work... but i haven't tried it myself. :)

---

### Post by bukwirm on 2006-07-04
Some kernel compiling instructions [here]("http://www.linuxplanet.com/linuxplanet/tutorials/202/1/").

---

### Post by vinodis on 2006-07-04
i thought 64-bit versions of ubuntu would recognize so much of memory.

---

