---
title: "Software index is broken!"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by parts-man73 on 2007-06-16
I just tried to install Java and some other misc packages using the command

sudo apt-get install ubuntu-restricted-extras

in the terminal. Everything run fine until I got to the software license agreement. I scrolled to the bottom of the agreement, then tried to hit "enter" nothing happens, tried clicking "OK" still no joy. So I exited the terminal. 

Now when I run Update Manager, I get an error "Software index is broken", please run "sudo apt-get install -f to fix this issue first"

I tried that, and get this error "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

I do that and it starts to install Java again, and gets stuck on the license agreement.

HELP!!! 

Brian

---

### Post by canadianwriterman on 2007-06-16
I had a similar issue. Have you TABBED to the OK button, then pressed enter? That should work.

---

### Post by parts-man73 on 2007-06-16
that did the trick, thank you!

---

### Post by canadianwriterman on 2007-06-16
Glad to help, parts-man.

---

