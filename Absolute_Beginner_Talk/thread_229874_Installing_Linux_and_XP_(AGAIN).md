---
title: "Installing Linux and XP (AGAIN)"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by BenWynn on 2006-08-05
Hey Guys,

Just a follow up post. So when i divide my hard drive, I devide the hard drive into the area where there is free space and it wont delete any thing. Its really hard to explain. Ok, it says 34gb free and i divide it into that yeah??

Anyway Ben Absolute NEBIE!!!

---

### Post by Jagot on 2006-08-05
If you have 34GB of free space then you can set up your Ubuntu partitions there, yes.  However, when you say free do you mean unallocated space or just unused space within another partition?

---

### Post by BenWynn on 2006-08-05
> **Jagot said:**
> If you have 34GB of free space then you can set up your Ubuntu partitions there, yes.  However, when you say free do you mean unallocated space or just unused space within another partition?


Yes its unused space in my main partion aka the only one I have

---

### Post by orb9220 on 2006-08-05
Well the free space is only free space for xp. You have to resize the xp partition down to make unallocated space to create a linux partition on.

Example: 60GB C: winxp ntfs drive. During the install do manual config partitions.

Resize the ntfs windowsxp partition to 15GB that leaves a 45GB unallocated.
Then you have to create a ext3 partition let's say 44GB for root with a mount point of / and a 1gb swap partition.

When done you will have a 15GB windows a 44GB linux / partion and 1gb swap

Resize to turn free into unallocated to create partitions on unallocated.

Hpe this helped a bit.

---

### Post by jimmygoon on 2006-08-05
What is your native language?

---

### Post by BenWynn on 2006-08-05
Thanks, I think i can finnaly use Linux!

---

