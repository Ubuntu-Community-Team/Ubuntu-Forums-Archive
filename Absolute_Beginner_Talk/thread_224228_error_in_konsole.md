---
title: "error in konsole"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by GQed76 on 2006-07-27
i am getting this error whenever i do anything in konsole similar to this

nathan@compaq:~$ kdesu apt-get install build-essential
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by T700 on 2006-07-27
If you do ```
kdesu kate
``` does it open, even with the errors?  Have you tried logging out and logging back in?  I've had the same thing happen and for reasons known only to the Linux gods, restarting the session cleared it up.

Paul

---

### Post by GQed76 on 2006-07-27
yeah i get errors across reboots :-/ Fresh install too

---

### Post by T700 on 2006-07-27
> **GQed76 said:**
> yeah i get errors across reboots :-/ Fresh install too

But do the applications still open and work, errors aside?

Paul

---

### Post by GQed76 on 2006-07-27
adept isnt working right.
 it cant find one thing to update.  My gnome install found like 200 to update.

i cant install ndiswrapper, it says it will break something.

I cant find any of the build essential tools either.

---

### Post by T700 on 2006-07-27
Are you sure you have all the repositories enabled?

Paul

---

