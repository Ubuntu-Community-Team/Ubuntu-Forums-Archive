---
title: "Loading a New Distro - Two Questions"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Lowtech on 2007-02-09
When I originally installed Ubuntu I did the install on a new, separate HDD from Windoze on my lab-rat PC.  I left about half of the 250GB HDD's  capacity unformatted.  

When I decide to install another flavor of Linux I was planning to once again unplug the Windoze HDD during this process but I am still left with two questions:

1) Will GRUB automatically detect the additional OS?
2) Will the other OS create a swap partition or will the generous 6GB swap partition Ubuntu created serve both OSs?

Thanks in advance, great forums.

---

### Post by louieb on 2007-02-09
2) Will the other OS create a swap partition or will the generous 6GB swap partition Ubuntu created serve both OSs?
Every distro I have installed (dozen or so different ones) will see the swap partition and use it. So yes sharing of the swap should be automatic.

1) Will GRUB automatically detect the additional OS?
The new distro will want to install its own copy of GRUB. And if your lucky the Installer will detect Ubuntu and place an entry in its GRUB menu.

There are lots of ways to install and use GRUB. See the Dual Boot link in my signature for more information and a few ideas.

---

### Post by Lowtech on 2007-02-09
Thanks.

I have the dual boot link bookmarked, I guess I need to look it over a little closer.  I seem to have missed the answers to my questions.

---

