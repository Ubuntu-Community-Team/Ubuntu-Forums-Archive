---
title: "How Do I Go About Dual-Booting Ubuntu and another distro?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-06-13
I have dapper installed as my sole os, but i would like to dual-boot it with another linux distribution (i haven't decided on which distro yet, probably fedora core 5 or debian)

You'll find an attachment on the bottom with a picture of my hdd and its current partitions.

Now the next step, I have no clue what to do.  Using gparted from the dapper desktop cd, I guess I could resize my /home partition, and then make some free space of about 15 GB for the other distro.  What do you guys think?

BTW, I'm wondering if the /home partition can be shared by any distro, no matter if its deb-based or rpm-based or anything else?

---

### Post by user1397 on 2006-06-13
A Friendly Bump!

---

### Post by halfvolle melk on 2006-06-13
[QUOTE=erik1397]BTW, I'm wondering if the /home partition can be shared by any distro, no matter if its deb-based or rpm-based or anything else?[/QUOTE]
I've mostly read advises against this so I'd suggest you each distro its own /home. /swap can be shared.

As for installing another distro next to Dapper, I'm sure ones such as Fedora are smart enough to just add themselves to an existing grub.

---

### Post by user1397 on 2006-06-15
I'm dying to try this out! But i need a liitle help...

---

### Post by drtvasudevan on 2006-06-15
oh, go ahead and install another linux.
(ubuntu is basically debian so why debian again?)
what is the problem?
you will get a partition manager which you are used to since you have installed ubuntu already.
use that to create more partitions.

no, home shared causes problems.
dont do it.
swap can be shared. it will be detected automatically and presented to you during install. accept it.

tv

---

### Post by user1397 on 2006-06-15
so if I try to install fedora, i would select an option like "use free space" or something like that? does anyone know what kind of partition manager FC5 brings?

---

