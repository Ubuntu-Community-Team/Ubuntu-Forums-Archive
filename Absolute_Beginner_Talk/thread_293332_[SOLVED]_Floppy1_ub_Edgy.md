---
title: "[SOLVED] Floppy1 ub Edgy"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by locky28 on 2006-11-05
I ran dapper for a couple of months just playing around with it and decided I'd give 6.10 a burl. 

All is running smooth except in Places>Computer I have an additional icon called floppy1 which I cant seem to get rid of now that there is no disk manager (that I'm aware of). I have one floppy drive installed and it is device floppy0. The floppy1 drive is not listed in fstab, and in properties is detected as a 7.9 gigabyte device. I have no USB devices plugged into my computer how ever I used my mouse on the USB port at first to get it working but it is now on PS/2. Any Ideas how I can get rid of this?

---

### Post by locky28 on 2006-11-05
Bump. 

When i view the properties of 'floppy1' the device name is '/dev/   ', yes thats intentionally blank because theres nothing there. any ideas?

---

### Post by steve.horsley on 2006-11-05
I've got one too. I guess everyone has. It doesn't bite though.

---

### Post by locky28 on 2006-11-05
Yeah it bugs the sh*t out of me though. Thanks for the reply, let me know if you find a way to remove it.

---

### Post by steve.horsley on 2006-11-05
Looks like not everyone has one. My laptop (which has no floppy drive) doesn't have any floppy icons. Not that that helps get rid of unwanted icons.

---

### Post by deanjm1963 on 2006-11-05
to fix that floppy problem, open up a terminal and type sudo gedit /etc/fstab hit enter, your passwd etc.

look for the line (should be the last one) that says

/dev /media/floppy0 auto rw,user,noauto 0 0

and change it to

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

save, exit and restart... that should fix it

---

### Post by steve.horsley on 2006-11-05
Excellent, thank you. It worked for me. Actually, I just commented the line out. But I didn't need to restart - just close nautilus and open a new nautilus window.

---

### Post by locky28 on 2006-11-06
You sir dean, are a god among men :P

Haha thanks mate that worked beautifully ;)

---

### Post by jpyanowski on 2006-11-16
> **deanjm1963 said:**
> to fix that floppy problem, open up a terminal and type sudo gedit /etc/fstab hit enter, your passwd etc.

look for the line (should be the last one) that says

/dev /media/floppy0 auto rw,user,noauto 0 0

and change it to

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

save, exit and restart... that should fix it

Thanks for this info, the extra non-existant floppy was driving me crazy. ](*,)

---

### Post by twrock on 2006-12-03
Thanks from me too. Problem solved. (And if I'm not mistaken, the initial floppy seek now takes somewhat less than the half-day it used to take.)

---

### Post by trackrat on 2006-12-09
jpyanowski, thanks from me too, as I had the same problem.

---

### Post by rws on 2007-02-18
Thank you. It solved this issue for me.

---

### Post by Hakimio on 2007-02-28
Thanks :)

---

### Post by odysseusjak on 2007-10-25
Thanks.

---

