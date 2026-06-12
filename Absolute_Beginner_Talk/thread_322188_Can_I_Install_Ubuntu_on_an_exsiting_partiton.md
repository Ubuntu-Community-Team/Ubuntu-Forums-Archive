---
title: "Can I Install Ubuntu on an exsiting partiton?"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by Asafus on 2006-12-20
Hello,
I'm new... I just want to install Ubuntu on my computer.

I have four partitions in my computer and one of them is empty,
I want to install Ubuntu there.

But When I'm in the installation i don't now how
to configure the right thing...

in the Partitioner... what do i need to define in each partition? 
can i install Ubunto without formating my disks?

thank's
Asaf

---

### Post by jvc26 on 2006-12-20
Yes you can install ubuntu without formatting your disks entirely, but I'm pretty sure you will need to format the partition that you want to install ubuntu to especially if that partition you want to install it to is NTFS. In the partitioner you want to select the partition that has nothing in it and then install ubuntu to that partition. In doing so you will format that partition probably to ext3 filesystem (the fairly standard linux filesystem) and you'll also need to create a small /swap file (also done in the run through on the partitioner) out of a bit of that partition. Hope that helps, am afraid I'm not sure where the links for the install of ubuntu are- I'm sure someone will be able to give you more specific instructions :)
Il

---

### Post by Sef on 2006-12-20
Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/").  It is for the alternate cd, but it has a link for installing with the Live CD.

---

### Post by Asafus on 2006-12-20
What about that menu that asks me to specified the
properties of each partition?

it's like:

choose: swap, boot, usr, var, home. (for each partition i have)

I guess for the partition i want to install the ubuntu on i need to check : Boot.
and what about the partitions that i don't want to do nothing with?

thank's
Asaf

---

### Post by scrooge_74 on 2006-12-20
For those other partitions don¿t do nothing, don't check any of them when it ask for formatting.

Ubuntu will make a system on that partition including a swap partition.  Just read all information and give the answers it needs

---

