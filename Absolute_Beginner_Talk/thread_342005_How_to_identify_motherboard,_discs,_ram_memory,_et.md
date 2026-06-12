---
title: "How to identify motherboard, discs, ram memory, etc"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2007-01-19
I have searched and cannot locate the command that list all my hardware, I want info on my motherboard, bios, ram memory, usb hubs, like that.
Peter

---

### Post by po0f on 2007-01-19
kindafunnylookin,

System->Administration->Device Manager.

---

### Post by kindafunnylookin on 2007-01-19
> **po0f said:**
> kindafunnylookin,

System->Administration->Device Manager.

that's it. thannk you

---

### Post by tonyr1988 on 2007-01-19
You can also use the Terminal command:

> lspci

To show a list of all your PCI devices. lspci -v gives you more info, and lspci -vv gives you even more info about them. You may have to sudo lspci -vv to get all possible information (about capabilities and such).

Oops - I'm a tad late. My bad.

---

### Post by depele on 2007-01-20
> motherboard, bios, ram memory,

==> device manager tells me a bit but I wan't to upgrade my ram memory I I don't know which one it is.

Can I find out?


grtz...

(no manual of mobo, computer without papers)

---

### Post by insane_alien on 2007-01-20
'sudo lshw' will list all your hardware with as much detail as possible including serial numbers, capacity, current status etc. etc.

---

### Post by depele on 2007-01-20
bump

---

