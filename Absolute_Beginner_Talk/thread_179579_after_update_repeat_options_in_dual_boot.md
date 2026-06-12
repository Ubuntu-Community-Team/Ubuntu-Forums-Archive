---
title: "after update repeat options in dual boot"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by peterj on 2006-05-20
HI im a complete noob, 
least im trying!
after I download updates for ubuntu, when I restart the box there are the dual boot options.
Instead of havin 1 ubuntu, 1 ubuntu recovery and 1 windows, theres 2 ubuntu and 2 ubuntu recoverys...every time I download updates I get another one!
its probably really simple but as I said, least im trying!
thanks

---

### Post by Kimm on 2006-05-20
hm... sounds strange... but perhaps the update installed a new kernel? that would cause such behaviour.

Next time you reboot, check and see if all the ubuntu ones are exactly the same.

---

### Post by peterj on 2006-05-20
wahey my first real problem....I shouldnt really be glad should I?
least im fitting in!
ye they're the exact same. I can enter a command prompt by hitting c but none of the help options jump out as problem solvers

---

### Post by Kimm on 2006-05-20
Hm... strange, neighter grub nor apt-get/dpkg should be doing that...

You could allways edit the grub menu manually (but I dont do that... so you'll have to talk to somebody else)

---

### Post by peterj on 2006-05-21
Ye thanks was able to find another thread on editing the grub menu and remove the lines myself...ill just have to do that every time I update but sure still better than windows

---

