---
title: "Dual booting 2 Linux OS's"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by n3tfury on 2007-04-24
I have Ubuntu on my dekstop and DSL on my laptop.  I would like to install Xubuntu on the laptop along with DSL, but have never set up a dual boot of only Linux OS's (dual-booting Windoze/Linux is a breeze).  

Can I just have one swap partition or do I actually need to set up two?  

Also, I'm a little unclear on reinstalling grub since it's already on the root partition of DSL.  Do I just overwrite it?

---

### Post by LaRoza on 2007-04-24
Dual booting Linux is easier. I imagine, you just make a new partition and install the other distro to that partition.

---

### Post by mijj on 2007-04-24
speaking as a novice ... is there a way to install Ubuntu without installing Grub? ... i.e if i have another preferred method of multibooting?

---

### Post by az on 2007-04-24
> **n3tfury said:**
> 
Can I just have one swap partition or do I actually need to set up two?  

Also, I'm a little unclear on reinstalling grub since it's already on the root partition of DSL.  Do I just overwrite it?

If you do not use suspend-to-disk (hibernation) then you can share a swap.  The swap is where you ram goes when you hibernate.

The grub that was installed by DSL will not be used, the newer one installed with Ubuntu with the updated configuration will be used.

---

### Post by n3tfury on 2007-04-24
thanks for the replies everyone.

AZ:  after installing Ubuntu on the new partition, i'm only faced with Ubuntu in grub but no sign of DSL.  do i need to edit the grub config?

---

### Post by az on 2007-04-24
> **n3tfury said:**
> thanks for the replies everyone.

AZ:  after installing Ubuntu on the new partition, i'm only faced with Ubuntu in grub but no sign of DSL.  do i need to edit the grub config?

That's a bug.  The Ubuntu installer should have autodetected the DSL install.

Yes, you can edit your menu.lst to add the dsl entry.

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
the dsl partition.  

So that means, add the stanza at the very end of the file.

Peek into the menu.lst in the DSL partition and copy the stanza.

---

### Post by n3tfury on 2007-04-24
i appreciate it.  got called into work this morning so will try it when i'm home later. 

thanks again, man.

---

