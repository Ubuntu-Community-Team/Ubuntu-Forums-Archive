---
title: "The infinite loop"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-02-05
Interesting, I have an integrated x1300 in a laptop.  I installed the envy drivers, and rebooted, bingo, 3d works, compiz works, YEA! but wait I only have 1024x768, so I scour the forum and find a way to change my xorg file, I reconfigure, to 1280x1024, reboot, YEA! it works, but wait compiz doesn't.  hmmm, reinstall envy, and poof 1024x768 redo the xorg file and no compiz.  

Any ideas? on how to fix it to where I can have compiz and 1280x1024?

Thanks

---

### Post by pieisgood4589 on 2008-02-05
In my experience, you can't, probably because your computer is too low on RAM.

Try resetting xorg.

---

### Post by emarkd on 2008-02-05
> **pieisgood4589 said:**
> In my experience, you can't.

No, I've got Ubuntu running on three machines with GUI's - One 1280x1024, one 1680x1050, one 1400x900, so you can certainly do it.  When you were editing your xorg file to reset your resolution, did you change your driver?  Also, did you edit the file by hand or did you do a dpkg-reconfigure?  You may have to make a backup of a working copy, do the reconfigure or the envy install, then compare the two files and put the appropriate parts together manually.

---

