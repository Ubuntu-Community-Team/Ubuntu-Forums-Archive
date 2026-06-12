---
title: "Gparted Live CD need advice, please."
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-12-20
I have a Gparted Live CD with which I have been trying to set up a partition in a 4GB Pen Drive (aka flash drive, memory stick, etc)

For my application I need at least a 750MB #1 partition.  After several tries and also using another 4GB Pen Drive, I have been unable to get Gparted to allow me to have this partition larger than 722MB.

Trying with Fat 16, or Fat 32, doesn't have any effect on the 722MB limit.

Do you have any idea what else I can do?

TIA

---

### Post by LinuxGuy1234 on 2007-12-20
> **L Campbell said:**
> I have a Gparted Live CD with which I have been trying to set up a partition in a 4GB Pen Drive (aka flash drive, memory stick, etc)

For my application I need at least a 750MB #1 partition.  After several tries and also using another 4GB Pen Drive, I have been unable to get Gparted to allow me to have this partition larger than 722MB.

Trying with Fat 16, or Fat 32, doesn't have any effect on the 722MB limit.

Do you have any idea what else I can do?

TIA

Use cfdisk to partition it and use a mkfs command. Example (assuming you use /dev/sda1 as the pen drive):
```

cfdisk # Do this first
mkfs.ext3 /dev/sda1
```

---

### Post by L Campbell on 2007-12-20
> **LinuxGuy1234 said:**
> Use cfdisk to partition it and use a mkfs command. Example (assuming you use /dev/sda1 as the pen drive):
```

cfdisk # Do this first
mkfs.ext3 /dev/sda1
```

Ok, I went to Terminal and typed ' cfdisk '.  It returned, ' Fatal error, can not open disk drive '

Also I tried it with ' sudo ', same result.

Obviously I'm doing something wrong.

---

### Post by L Campbell on 2007-12-20
> **L Campbell said:**
> Ok, I went to Terminal and typed ' cfdisk '.  It returned, ' Fatal error, can not open disk drive '

Also I tried it with ' sudo ', same result.

Obviously I'm doing something wrong.

Hello .....

I'm really hoping that someone can help me here, please.

TIA

---

