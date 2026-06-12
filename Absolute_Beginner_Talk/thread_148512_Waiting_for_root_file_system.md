---
title: "Waiting for root file system"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by KAMoore on 2006-03-22
This morning the Dapper computer stuck on start up at the point "Waiting for root file system" it stayed there for about 3 to 4 minutes then booted OK

I checked system log and there were mentions of unable to mount partition

Anyone have any ideas what is going on

thanks

---

### Post by localzuk on 2006-03-22
It could be a hardware issue? I have had similar problems and found it to be my hard disk slowly dying.

---

### Post by KAMoore on 2006-03-22
No I don't think so... however it remains a possibility

What makes me think it is software related is that I had problems booting dapper on another computer (reasonably new) and I had to reinstall the mbr and went back to windows on that machine.

---

### Post by inklingx on 2006-03-22
Same problem here after yesterday's kernel update.
FYI: /boot is on hda1 and / is on a software raid 0 (sda3 and sbd3).

---

### Post by Luffield on 2006-03-23
Same problem here. I didn't wait for 3-4 minutes though, I just restarted and tried to boot kernel 2.6.15-16 that I still have installed, and it boots normally.

---

### Post by KAMoore on 2006-03-23
I'm wondering if it's anything to do with LVM; I used this installation method has the new kernel messed this up???

---

### Post by jvolkman on 2006-03-23
Both my laptop and desktop have the same problem.  They're both using LVM.  Definitely seems to be LVM-related.

---

### Post by KAMoore on 2006-03-23
I've reverted back to the previous kernel and that has solved the problem

So I guess it's a LVM / Kernel set up issue about which I have no idea how to solve

---

### Post by Mustard on 2006-05-15
Interesting to read this thread, as its confirming in my mind that its a kernel version problem.  I'm going to try switching back to an older kernel version myself, once I work out how to do that when i can't even boot into the machine. :)

---

