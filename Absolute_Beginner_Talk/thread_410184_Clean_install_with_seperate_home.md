---
title: "Clean install with seperate /home"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by RideP2 on 2007-04-15
Ok, so I'm probly going to install a clean install of Feisty when it releases, but I've got one question.

Right now I'm running Edgy with a separate /home partition. When I go to install Feisty, will it let me keep using this /home partition? If yes how do you do this?

Thanks.

---

### Post by taurus on 2007-04-15
Yes, you can keep your /home.  Just tell the installer to mount that partition to /home BUT do not format it or all your personal settings will be gone.

---

### Post by RideP2 on 2007-04-15
Will it be clear if it's going to format it or not. Like is there an option?

---

### Post by zvacet on 2007-04-15
If you want to save your data option is not to format existing home partition.Exactly what taurus told you.

---

### Post by old_geekster on 2007-04-15
The solution to your question is, do a dist-upgrade (sudo update-manager -c -d).  If all of your hardware is good in Edgy, an upgrade should work fine.

My drive is partiotioned as follows:

/ (root)
swap
/home

I am in the process of upgrading as I type.:D

---

### Post by freebird54 on 2007-04-15
To more directly answer your question (:) ) - there is a box beside each partition's listing at the point where you assign them to their future uses.  If the box is CHECKED, it will be formatted, if not, not.  There is a heading so you know if's the right box.  You will need to set the swap and root partitions for formatting - no others need to be.

Hope that helps!

---

