---
title: "A question about Gparted permission"
date: 2008-10-17
forum: Arch and derivatives
---

### Post by Louis de Broglie on 2008-10-17
Is there any chance that installing gparted can change permissions to the disks for normal users ? :) Also I want to know which group the user must belong to to use gparted effectively.

---

### Post by mattze on 2008-10-17
Simply installing gparted should change nothing. 
To run gparted you will need superuser rights (sudo). 
Gparted is a powerfull tool - be sure you know what you are doing before you use it.

edit: it is always a good idea to have all important files as a backup, before making changes to the partitiontable.

---

### Post by Louis de Broglie on 2008-10-17
What about qtparted ? :) I am running kde 4.1 .So I think qtparted will better integrate, right ? :) Does it have the same functionality as gparted ?

---

### Post by handy on 2008-10-18
> **Louis de Broglie said:**
> What about qtparted ? :) I am running kde 4.1 .So I think qtparted will better integrate, right ? :) Does it have the same functionality as gparted ?

They are both great partition managers.  Personally I find booting with a Ubuntu LiveCD & using GParted to be very effective, I can access any partition i.e. /boot / /home or what have you from the LiveCD.

---

