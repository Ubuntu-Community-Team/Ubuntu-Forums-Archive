---
title: "Kernel Issue i386 / generic"
date: 2007-10-28
forum: Apple Intel Users
---

### Post by cworley420 on 2007-10-28
Had problems back when i upgraded to Feisty and had to drop back to the old generic kernel i had.

I have a dual core intel power book..  I upgraded to gutsy and am having similar problems.

With Feisty and with the Gutsy upgrade the i386 does not recognize the 2 cores in my cpu.  when i look at gnome-monitor i only see one cpu.  If i use the generic i get both

The Gutsy the i386 configuration gets the compiz effects working . awesome!!!  But, the generic does not

The i386 does not have my sound working but the generic does

The wirless works automatically with i386, not with generic.  With feisty i did some things i found on a form and got it to work.

dual cpy    i386:no     generic:yes
xgl      i386:yes       generic:no
sound i386:no         generic:yes
wireles   i386:yes     gneric:no

What I would like to know is home can  i compare the configuration used to compile these two kernel binaries.  Second, what steps do I take on ubunut to do this.

With slackware i would just download the kernel from kernel.org and do it.  But, i want to use the one provided by ubunut so i get whatever patches ubuntu has made to it. 

Also, if there is any other info anyone can add to this i would appreciate it.

thanks 

-chris worley

---

### Post by cyberdork33 on 2007-10-28
you should be using generic. it is a meta package that selects the real kernel that is best for your system.

Things work for the i386 kernel because you downloaded other things that are required that go with that kernel, you should do the same for the new generic kernel... linux-restricted-modules-generic, and the like. different kernels mean different modules.

XGL is NOT compiz. Your XGL is likely working fine, your compiz is not (probably need to reconfigure fglrx for the correct kernel.)

same for your wireless.

Why did you choose a kernel other than the default?

---

### Post by cworley420 on 2007-10-28
The 386 is what i set as the default after the upgrade.  I believe during the upgrade I might have selected that.  I cant really remember what options i was given.

okay, i'll put the generic as the default.  and then figure what i need to do for the xgl and wireless.

---

### Post by cworley420 on 2007-10-28
okay, i changed it to boot with generic and the xgl is working with the card's accelerator.  Also, the wirless device was recongnized. 

After I upgraded the other day neither of those worked when i used the generic.  Maybe i chose one of the older generic kernels still in the mnu.lst file.  --or maybe between then and now i ended up installing whatever it needed.

problem solved

thanks.

---

