---
title: "Reduce Swap Partition Size"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by AnotherMuggle on 2007-07-31
Hi,

I recently installed a triple OS system with the inclusion of Feisty Fawn.  I mistakenly created a 3GB swap partition for the installation (don't know what I was thinking).  I now want to reduce the size of the partition to 2GB to match the amount of installed RAM in the system.

Is there a straightforward method to go about this? Can I simply resize the swap partition and expand the "/" parition using gparted from within Ubuntu?

Experienced Windows user but a "proper" noob when it comes to Linux, so please handle with care lol. 

Thanks in advance,
Tom Kear.

---

### Post by FleetAdmiral74 on 2007-07-31
You will need to do it from a LiveCD, not while running Ub off the HD, but yes, it should be that simple.

---

### Post by mikewhatever on 2007-07-31
You should be able to resize the swap or any other partition with gparted live cd.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
A version of gparted is on Ubuntu live cd too and can be found under System>Admin>Gnome Partition Editor.
That said, you may not need to bother resizing, unless there is a grave space shortage. If your hdd is 100 BG or more, think again whether you really miss that 1 gb so much.

---

### Post by AnotherMuggle on 2007-07-31
Thanks for all the input.

I used the LiveCD and successfully resized the partitions.

\\:D/

---

### Post by remali on 2008-03-22
Greetings fellow ubuntists..
I recently (today) installed ubuntu..
I made a small mistake.  I made the swap partition 20 Gb. :-({|= :-({|= Could anyone please tell me the steps how to reduce it with live cd.???
Thanks :guitar:

---

