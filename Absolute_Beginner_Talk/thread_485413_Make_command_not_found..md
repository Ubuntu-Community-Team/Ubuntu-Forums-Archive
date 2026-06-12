---
title: "Make command not found."
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Skycloud on 2007-06-26
I was getting an error saying the make command was not found, then I searched it up and downloaded build-essential, and rebooted my computer, but make command still isn't found, what did I do wrong?

---

### Post by charles.g.moore on 2007-06-26
if you already installed build-essential it should work but you could try this:

start a terminal alt+f2 gnome-terminal
sudo aptitude update
sudo aptitude install make

You don't have to reboot after 99% of application installations, that is a winblows thing...

Try that

---

