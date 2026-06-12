---
title: "[SOLVED] cannot unmount volume to format drive"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by jmate24 on 2007-09-13
when i try to unmount my internal drives i get this error file:///home/oem/Desktop/Screenshot.png
how can i unmount my drives i have already tried deleting the the entries in /etc/fstab and loged off and restarted X session do i need to restart my computer?

---

### Post by jmate24 on 2007-09-13
cannot unmount volume:

Details:
     Cannot open /media/.hal-mtab
i do not know how to post screen shots yet:(

---

### Post by Paul133 on 2007-09-13
try 'sudo umount /path/to/drive' and see what happens.

---

### Post by jmate24 on 2007-09-13
i fixed it, i had to restart my computer. thank you; but i do not have unmount and i cannot get unmount from apt. also i need to make my formatted hard drives available with rw access, can you post how i may accomplish this, and i will print it off. so that i can save it for future reference.

Thank you,
jmate24:)

---

### Post by jmate24 on 2007-09-13
ps it is for my 7.04 box and i am still trying to get the hang of ubuntu 7.x after converting from Windoze

---

### Post by jmate24 on 2008-02-04
solved!

---

