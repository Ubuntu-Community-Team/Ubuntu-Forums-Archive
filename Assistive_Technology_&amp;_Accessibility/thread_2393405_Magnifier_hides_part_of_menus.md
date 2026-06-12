---
title: "Magnifier hides part of menus"
date: 2018-06-03
forum: Assistive Technology &amp; Accessibility
---

### Post by leona on 2018-06-03
Hi
I have 2 machines, my desktop currently running Mint 18.3 and my laptop (acer switch alpha 12) running Ubuntu 18.04
I have a sight impairment so I use the magnification assist tool.
I have noticed that, on the laptop, if I zoom in, I loose parts of the system menus, so if I click an icon in the the top right panel, only a small part of that menu is displayed, makes it very hard to read.
This doesn't happen in Mint (different desktop cinemon not gnome).
I had used previous versions of Gnome before and saw this happening before, I was hoping this issued would be fixed by now.
So are the developers aware of this issue, and is it being worked on?
Thanks
Leona.

---

### Post by PaulW2U on 2018-06-03
> **leona said:**
> I had used previous versions of Gnome before and saw this happening before, I was hoping this issued would be fixed by now.
So are the developers aware of this issue, and is it being worked on?

Does the bug report [universal access zoom unusable]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1769299") describe your issue? There are a couple of screenshots that illustrate exactly what is being reported. 

If the bug report has been created correctly then the developers might be aware of the bug but whether they are working on it is another matter. If that bug report is relevant to you and you have a Launchpad account then you should use the button at the top of the screen to say that it affects you too. That will then change the bug status to "Confirmed" and perhaps raise the chances of the bug being fixed.

---

### Post by bryce4 on 2019-01-02
I also have that issue. The screenshots are exactly as I have witnessed on my system, and others have reproduced it under virtualized conditions as well. A patch is available according to the status page for [bug #1767648]("https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1767648"), however there are upstream issues which prevent its proper implementation right now (if my understanding of the bug tracker is correct). We'll have to wait a little while longer before the issue is resolved, but any users marking the bug-tracker that the issue affects them will increase the chance that other developers will assist those already working on the issue in both Ubuntu and the Gnome project.

---

