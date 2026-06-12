---
title: "Mounting big NFS shares during boot"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by MrMist on 2007-07-01
I was trying to mount a big NFS-share during boot by editing fstab according to all the instructions online. However, nothing got mounted during boot. After scratching my head and searching around on the net, I accidentally stumbled upon a mount-flag which solved this problem:

server:/shares/myfiles /shares/myfiles     nfs     ro,hard,intr,rsize=8192,wsize=8192,bg

The flag **"bg"** solved the problem. Inspecting the processes running (using *ps -ax*)  right after boot, reveiled that there was a process running to mount these shares, running in the background. After waiting a minute or so, everything was as expected.

---

### Post by waggygee on 2007-07-04
cool! thanks

---

### Post by Jose Catre-Vandis on 2007-09-28
This worked for me too, many thanks. Big shares that had been showing up after boot suddenly started not to show up. I was having to "sudo mount -a" to get them up. The ",bg" added to the end of my share line fixed this. :)

---

