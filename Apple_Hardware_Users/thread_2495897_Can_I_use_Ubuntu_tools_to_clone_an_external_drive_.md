---
title: "Can I use Ubuntu tools to clone an external drive that contains MACOS (High Sierra)?"
date: 2024-03-06
forum: Apple Hardware Users
---

### Post by wb0gaz on 2024-03-06
This is not specifically about ubuntu running on mac hardware, but thinking someone managing multi-boot environment might have run into a similar need/solution...

I wish to clone (onto a larger device) the startup drive removed from a MAC OS system (High Sierra) which contains Apple's HFS+ filesystems.

I tried dd to duplicate the drive's contents onto another one, then gparted to relocate the third (small, "recovery") partition to the end of the larger drive, however, gparted does not appear to have HFS+ filesystem support (needed to expand the second/root filesystem to take up the available space between end of the existing root/main filesystem and start of the newly relocated third/recovery filesystem).

Can this task be done with command-line (or GUI) tools available in the Ubuntu/Linux environment?

I do not wish to use a commercial product for this (one-time) task.

Thank you, and happy to provide any needed clarifying information.

---

### Post by QIII on 2024-03-06
Duplicate of [https://ubuntuforums.org/showthread.php?t=2495896](https://ubuntuforums.org/showthread.php?t=2495896)

Closed

---

