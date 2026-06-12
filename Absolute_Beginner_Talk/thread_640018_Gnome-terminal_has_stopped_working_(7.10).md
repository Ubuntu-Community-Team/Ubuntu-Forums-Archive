---
title: "Gnome-terminal has stopped working (7.10)"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by jck99nz on 2007-12-13
Hi,
Clicking Applications|Accessories|Terminal no longer opens a terminal. I get a 'starting terminal' icon along task bar, but it disappears after a few seconds. I used Alt-F2 to open xterm, and ran 'gnome-terminal'. I got a message "Bus error (core dumped)". I tried reinstalling gnome-terminal via synaptic manager, but it didn't fix it. 
Any advice on where to look or what to do to get it going again?
 (I think the problem began when I was accepting recommended updates - while this was happening, I used firefox, and clicked to download a recommended plugin. Seemed to interfere with the update - I got a "dpkg: parse error" which I managed to fix by editing the dpkg file - last section ended in mid-line, like it had been cut off).
Jeff

---

### Post by Dr Small on 2007-12-13
Have you tried rebooting, or restarting X ?

---

### Post by jck99nz on 2007-12-13
Yes, the computer's been closed down and restarted a couple of times since the problem occurred. I also restarted after reinstalling gnome-terminal. Still get same error message in xterm when trying to start gnome-terminal.

---

### Post by jck99nz on 2007-12-13
I found some similar problems (bus error, core dumped) in bug reports - one with Evolution was fixed by reinstalling lib6. I did this, rebooted, and gnome-terminal now seems to work fine.
Jeff

---

