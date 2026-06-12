---
title: "I need help..."
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Listener008 on 2007-07-19
Ok I keep getting an error that says... "Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

Then I run the "sudo apt-get install -f" and get "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. " 

When I run the "dpkg --configure -a" it says "dpkg: requested operation requires superuser privilege"

What do I need to do?

---

### Post by ddrichardson on 2007-07-19
sudo dpkg --configure -a :-)

---

### Post by corevette on 2007-07-19
If it ever asks something along the lines of "requires superuser privilege," always try putting sudo before the command you are attempgin

---

### Post by Listener008 on 2007-07-19
Ok thanks a bunch guys, I did it and it worked

---

