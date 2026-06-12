---
title: "Globally setting input method to SCIM"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2008-01-09
Since I installed SCIM and anthy for input, I find that it's interfering with mythtv. I find that if I right-click a text-area in the window and set the Input Method from X Input Method to SCIM Input Method, my problems are solved.

There are too many windows available, however, that require this, and on top of that some that require this have no text boxes.

So my question is this: How can I globally set the Input Method to SCIM Input Method?

---

### Post by wana10 on 2008-01-09
[help page](https://help.ubuntu.com/community/SCIM) has the answer.
you need to install scim-bridge and then modify /etc/X11/xinit/xinput.d/scim
everywhere it says xim replace it with "scim-bridge" (with the quotes). then save it, delete the .scim and .xinput folders in your home folder, cross your fingers, and reboot!

---

### Post by pteri498 on 2008-01-09
Oh thanks a lot! Guess I wasn't looking hard enough for the answer.

---

