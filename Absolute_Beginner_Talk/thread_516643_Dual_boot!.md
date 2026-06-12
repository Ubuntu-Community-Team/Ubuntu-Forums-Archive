---
title: "Dual boot!"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by mozeruk on 2007-08-03
Hello Guys,

Im looking to install Ubuntu on my laptop

My set up is as follows:

**1 hard drive**
[LIST]
[*]PARTITION 1 - WINDOWS XP AND DATA
[*]PARTITION 2 - RECOVERY
[*]PARTITION 3 - FREE FOR UBUNTU (93GB)
[/LIST]
Could somebody explain the partition section of the install so that i leave my windows and data, and my recovery partition intact, thus using the 3rd "preset" partition?

Hope this makes sense?

Thanks in advance!

---

### Post by ev5unleash1 on 2007-08-03
Ok, when you boot from the live CD open the partition manager and use that free space for an Ubuntu Partition and make sure you have a linux-swap that will be needed for the installation and make Ubuntu run faster.

---

### Post by PriceChild on 2007-08-03
See [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

You will want to choose "Manual partitioning" when given the option, and make the appropriate partition mount at "/" (no "s)

---

### Post by mozeruk on 2007-08-03
> **ev5unleash1 said:**
> Ok, when you boot from the live CD open the partition manager and use that free space for an Ubuntu Partition and make sure you have a linux-swap that will be needed for the installation and make Ubuntu run faster.

How do i do the linux swap?

---

### Post by mozeruk on 2007-08-03
> **PriceChild said:**
> See [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

You will want to choose "Manual partitioning" when given the option, and make the appropriate partition mount at "/" (no "s)


what do you mena by:

appropriate partition mount at "/" (no "s)

is it a text box i can edit or something? 

Thanks for replying, Mark

---

### Post by PriceChild on 2007-08-03
Firstly make sure you make backups on removable media of any important data.

Its really easy and once you get to it I'm sure you'll fly through.

Basically you will want to resize a partition (right click and edit it then move a slider) then create a new partition at the end (right click empty space on graph and create new partition)

You'll want to format the main partition as ext3 and the swap partition as swap.

when you right click and edit the partitions, you can change their "mount path". Change the main partition your'e installing to, to /

---

### Post by thefoolisme on 2007-08-03
And definitely read the link that was provided.  That one and this one should give you enough information to make you an informed installed.  [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

