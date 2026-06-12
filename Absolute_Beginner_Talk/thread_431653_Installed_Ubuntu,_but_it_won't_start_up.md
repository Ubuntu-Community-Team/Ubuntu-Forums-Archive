---
title: "Installed Ubuntu, but it won't start up"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by dmorand on 2007-05-03
I got Ubuntu installed on my Presario V6000 laptop, but when it boots up the Ubuntu screen appears with the progress bar, but it just sits there at 3 bars loading and never does anything.  Has anyone else experienced this issue?  

I installed Ubuntu in Safe Graphics mode and had to change the quiet splash argument to noapic.  I'm a linux newbie big time.  I don't even know what the noapic did, but I read it on the forums when I had trouble installing, and I am now able to install.  

Any help would be greatly appreciated.

---

### Post by Cypher on 2007-05-03
If the "noapic" option worked for you to install Ubuntu, perhaps you need it to boot up as well. On a reboot, in the GRUB menu, choose to 'E'dit the command line and add the "noapic" option and see if you get farther..

---

### Post by dmorand on 2007-05-03
> **Cypher said:**
> If the "noapic" option worked for you to install Ubuntu, perhaps you need it to boot up as well. On a reboot, in the GRUB menu, choose to 'E'dit the command line and add the "noapic" option and see if you get farther..

How do I get into the GRUB menu?

---

### Post by Cypher on 2007-05-03
It's the first boot menu you should've gotten when you rebooted your machine. You will see a couple of Kernel options (Recovery mode, memtest) and possibly Windows XP if you have that instaled as well.

If you didn't see the menu, you should have seen a line saying "Press ESC" for the menu or something???

---

### Post by dmorand on 2007-05-03
O yeah I saw that.  I tried loading into another option in that menu to see if that would at least load it up.  I'll modify the command line and see how that works, thanks!

---

