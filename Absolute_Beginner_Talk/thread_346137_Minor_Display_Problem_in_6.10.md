---
title: "Minor Display Problem in 6.10"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by jonandrews on 2007-01-25
Has anyone seen (& hpoefully solved) this issue?

When installing, and later updating, Ubuntu the progress bar displays the '% complete' at various points.

In 6.06 this displays correctly throughout the installation, but with 6.10 the '% complete' field becomes unreadable after a short time. (on the same hardware).  

Some marks are visible in the bar, but it appears 'whited out' and illegible.  This problem appears to apply to any progress bar that displays for a long period.

This has been observed on all 3 of my installations of 6.10.

Hardware involved is the on-board graphics of an E-Machines 520 Base unit & an Acer AL1916 flatscreen.

---

### Post by jonandrews on 2007-09-18
OK, problem solved. (by the way, the bug is also present in 7.04)

I found this in the forum, which has now fixed the problem on 4 installations:

That thread also credits the bug listed here:
[https://launchpad.net/ubuntu/+source/xorg/+bug/67443](https://launchpad.net/ubuntu/+source/xorg/+bug/67443)
Quote:
To fix it:1 - Edit /etc/X11/xorg.conf, and change display DefaultDepth from 24 to 16.2 - Log out.3 - ctrl-alt-backspace to restart X 
Being a damn n00b to linux, the case-sensitivity of the file path threw me for a while (x11 versus X11). So, for other n00bs, I'll elaborate a little bit on that fix:

1. Open a new terminal window (Applications > Accessories > Terminal)
2. Type: sudo gedit /etc/X11/xorg.conf
[sudo gives you root access (write privileges), gedit is the editor you use to open the file at that path.]
3. Under Section "Screen", change DefaultDepth from 24 to 16.
4. Save the file.
5. I rebooted instead of restarting X but it did the trick for me.

I hope that helps other people!

---

