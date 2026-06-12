---
title: "Proper Partition Setup"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by czd2002 on 2008-03-04
I have tried to install ubuntu  3 times now and all i get is a bunch of errors then it hangs.

plz help

---

### Post by Presto123 on 2008-03-04
Are you attempting to do a dual-boot or single boot Ubuntu only machine?

---

### Post by Sinkingships7 on 2008-03-04
can you be a little more specifc?

where does it hang? after you do what? how far did you get?

---

### Post by jrusso2 on 2008-03-04
Your title doesn't seem to match the body of you message.

What errors are you experiencing?

Usually partitions can vary

but standard is 

/  which is the root partition which contains the operating system and files.

and /swap which is the swap / virutal memory file

Many users also use a /home which is used for data and configuration files.

But this is not required

File system types include the standard ext 3

and you can also use jfs, xfs and resier.

some users make a small /boot which is used for the kernels.

This is often used when using a files system type which requires a /boot of ext3

---

### Post by czd2002 on 2008-03-04
I get all the way through the setup to the first boot then it hangs at Running local boot scripts (/etc/rc.local)

Single OS Ubuntu 7.10 w/ LAMP

Buffer I/O Error like 12 of them they go to fast to read

I am totally new to ANY of this. I was a hardcore windows person. But i want to lean linux and use it for a CSS dedicated server.

---

### Post by czd2002 on 2008-03-04
I think i found my problem i downloaded the server edition.

Can you still use LAMP with desktop edition???

---

