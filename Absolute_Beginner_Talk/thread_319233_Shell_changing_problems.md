---
title: "Shell changing problems"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-15
I have downloaded and installed CSH shell on my ubuntu . 
I have changed the shell from Bash to C-shell using the chsh command too
But now when i do "echo $SHELL" it says that the shell is "/bin/bash".
But when i do "finger -l"  i get the shell as "/bin/csh"

Is there any discrepancy.

---

### Post by Ragazzo on 2006-12-15
It seems you need to restart the GNOME session for it to take effect in gnome-terminal. Try typing  Ctrl-X Ctrl-V . If your shell is Bash, that key combination will print the Bash version.

---

### Post by taurus on 2006-12-15
If you change your shell from a terminal, you need to log out and back in again so the new shell will be in effect!!!

---

