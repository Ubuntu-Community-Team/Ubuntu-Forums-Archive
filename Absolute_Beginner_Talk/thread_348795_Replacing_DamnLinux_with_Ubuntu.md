---
title: "Replacing DamnLinux with Ubuntu"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by purplearcanist on 2007-01-29
I have DamnLinux installed on a computer, within Windows.
How do you make it so when DamnLinux boots up, it boots Ubuntu instead of DamnLinux?

---

### Post by kerry_s on 2007-01-29
What? Do you mean you have damn small linux installed in a virtual system in windows? Do you have ubuntu installed?

---

### Post by Pobega on 2007-01-29
To install Ubuntu, you'd have to overwrite "DamnLinux" with it. You can boot into the Ubuntu LiveCD and tell it to install to whichever partition you want (i.e. your DamnLinux partition) and it will over write DSL with it. You will lose all of your data from DSL, so it's usually a smart idea to create a /home partition so you can save the data you want by putting it in your /home folder.

---

### Post by purplearcanist on 2007-01-29
Wait... is there a way to install Ubuntu within DamnLinux?

---

### Post by irish_flu on 2007-01-29
Can I assume you mean that you have Damn Small Linux installed as a VMWare "Virtual Machine" within Windows?

You *could* probably run a Virtual Ubuntu machine within your virtual Damn Small Linux machine, but I sure wouldn't recommend it; I'm not sure what would happen running two-vm-deep.

If you are indeed running Damn Small Linux within a virtual machine with VMWare, then get yourself a VMWare Ubuntu build and you can just run them side-by-side.

Even if you could run Ubuntu within Damn Small Linux, that would be like running Windows XP within another copy of Windows XP; both Damn Small Linux and Ubuntu Linux are complete Operating Systems.

---

