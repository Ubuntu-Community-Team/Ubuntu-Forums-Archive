---
title: "UUID - tutorial, explanation ..."
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-07-06
I note the use of UUID strings in /etc/mtab and /etc/fstab in lieu of say /dev/sda1, etc.  Why is this and what is the purpose?  UUID's seem to make things more ambiguous than useful.

Carl

---

### Post by BillDozer on 2007-07-06
Whithout really knowing it, I would say: "to keep better track of your drives". 

If you add an extra disk to your array of disks, the /dev/sda1 could suddenly be something else for the specified disk. I guess UUID is a unique identifier generated out of some drive parameters and this way when adding a new disk the UUID still is your /home partition instead of the newly added disk which has taken /dev/sda1 place...

---

### Post by az on 2007-07-06
> **cwmoser said:**
> I note the use of UUID strings in /etc/mtab and /etc/fstab in lieu of say /dev/sda1, etc.  Why is this and what is the purpose?  UUID's seem to make things more ambiguous than useful.

Carl

If you move your drives around, the appropriate filesystem will still get mounted in the appropriate spot.  Thirty years ago, your fstab never had to change - all your hardware stayed in the same spot from the time the machine was built to the time it stopped working.  Computers are much different today.  The old way of doing things does not really work anymore.

You can still use the device name if you want...

---

### Post by Jucato on 2007-07-06
UUID means "Universally Unique ID". It's a unique label/name that is assigned to a specific partition. Each partition has a unique UUID, and if you delete then recreate that partition, it will have a different UUID, too. Basically, UUID is just a label (the same as LABEL, which you can also use instead of UUID or /dev) except that it's not so arbitrary and can't be changed on a whim.

The biggest practical benefit of using UUID's is that changing the arrangement/connections of your drives won't affect the system. For example, your / partition is on /dev/hdb2, which would be the 2nd (2) partition of the primary IDE slave (hdb). Now, suppose you change the connections and it became the secondary IDE slave (hdd). If your fstab used /dev to mount partitions, you'd have to edit fstab to reflect that change. Of course, you wouldn't be able to normally boot into your system because of the change, so you'd have to do it from, say, a Live CD. By using UUID, the system identifies the partition through that ID, not where the device is located. So switching drives around won't be a problem.

(Hope that helps a bit...)

---

