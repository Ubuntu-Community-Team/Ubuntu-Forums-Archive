---
title: "Dual Boot Mounting Problem"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by scottsanpedro on 2006-12-08
Hi,
I am dual booting XP with Ubuntu. Version 6.06. I have 40gb drive
So far I have loaded XP on a partion.
Now I am currently installing Ubuntu. I have resized the XP partion to 19gb, have set up a new partion (hda2) of 18gb for hopeful ubuntu installation, and 1gb for swap file.
I have created them ok and now on the screen 'Prepared mount points'
I want to add '/' for the 18gb hda2 partion, swap for 1gb hda3 BUT want to leave the hda1 partion for windows. 
My question is what mount point do I choose??
Many thanks for anyones time..Scott

---

### Post by scottsanpedro on 2006-12-08
ignore me..I have just missed out the windows partion and gone for hda1 and hda2 ONLY

---

### Post by lemonsCC on 2006-12-08
Ignore you?  Why would we do that?  Please keep in mind that many, **many**, **MANY** of our users are from the US and it is only 6:22am on the East Coast and 3:22am on the West Coast.  This is why your question was not promptly answered.

On the Prepare Mount Points "page" it should say manually edit partition tables.  This is the option you are looking for.  Highlight it > press enter and then select hda2 and make it /  then make hda3 swap.

Sidenote:  It is much easier to make a dual boot system by:
[LIST=a]
[*]Creating your partitions first (using GParted found on the Ubuntu liveCD)
[*]Installing Windows XP
[*]Then, install Ubuntu
[/LIST]

EDIT:  Were you starting from a blank harddrive?

---

