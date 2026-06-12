---
title: "Kubuntu 7.10 crash after updates"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by riksia on 2008-02-17
I'm using Kubuntu 7.10. My OS  crash after updates. When I restart system, my monitor is black after kubuntu logo. How fix it? :popcorn: sorry for my english

---

### Post by jan de beuker on 2008-02-17
Hello riksia

While booting press the escape button to enter the grub menu
Select the second option (recovery mode) and let the systeem boot
I hope you get the root terminal.

Then tyry this command

dpkg --configure -a

Greetings
Jan

---

### Post by riksia on 2008-02-17
Works :) but this deleted updates :(

---

### Post by jan de beuker on 2008-02-17
Ok
Then try updating with the terminal
When something is wrong it most likely will point you in direction were to look for the solution 

open terminal and type

sudo apt-get update



jan

---

