---
title: "dpkg error"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by fridayxiii on 2006-06-18
I was trying to install amarok from terminal using *sudo apt-get install amarok* & got the error "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

I did try to search the forums w/this error but didn't see any obvious results.  Ideas on how to fix?

---

### Post by catlett on 2006-06-18
You have to run that command in the terminal ```
dpkg --configure -a
``` I don't remember if you have to run it as root. If it says permission denied or cannot open, etc then run it as ```
sudo dpkg --configure -a
``` That should clear it up. If not there is something more wrong. Run the commands and then post if there is an error again.

Good luck, Jason

---

### Post by xXx 0wn3d xXx on 2006-06-18
Run:
> sudo dpkg --configure -a
to fix this problem.

---

### Post by fridayxiii on 2006-06-18
Thanks guys that seems to have done the trick.  

Cheers!

---

