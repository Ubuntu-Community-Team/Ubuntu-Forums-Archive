---
title: "Restarting Gnome"
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by SteveF on 2006-01-23
Recently I had to modify xorg.conf.  After doing that, in order to pick up changes I had to top X.  To do this, I did CTRL-ALT-BACKSPACE and then did startx to get back in.  I have since tried (after doing CTRL-ALT-BACKSPACE):
sudo /etc/init.d/gdm restart
and that was better.  But, I had to kill the gdm process to do it.

But is this the correct way to do this?  Should I run the gdm restart just in a terminal window instead of killing X?

What should be the technique?

Thanks,

Steve

---

### Post by dueY on 2006-01-23
I like killing the gdm process.  If I ctrl+alt+backspace then startx it logs me in as root.

---

