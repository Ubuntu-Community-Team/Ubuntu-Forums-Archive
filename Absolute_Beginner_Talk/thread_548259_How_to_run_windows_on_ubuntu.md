---
title: "How to run windows on ubuntu"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by LynchStreet on 2007-09-11
I am really new to Ubuntu but I like it alot, I am running it on one hard drive (D) and Windows is on a different hard drive (C) I need to be able to run windows in a shell so I can stay booted to ubuntu. If anyone can give me an idea that would be great!  Thanks

---

### Post by jclmusic on 2007-09-11
i think ur best bet would be to run a virtual machine in ubuntu. try vmware or virtualbox.

---

### Post by lisati on 2007-09-11
It is possible to run some Windows programs with Ubuntu using a Windows emulator. The one I have on my computer with the name "Wine".

---

### Post by derjames on 2007-09-11
You can install Windows in a virtual machine (for example VMware) so both operating systems coexist at the same time...

There are many articles about VMware (or any other virtual machine)  in this forum...

cheers

---

### Post by BrendanM on 2007-09-11
<OCD>
Wine is technically not an emulator, but rather a compatibility layer. (WINE actually stands for "Wine Is Not an Emulator") That means that programs in Wine run at full speed, whereas programs under emulation typically run much slower.
</OCD>

---

### Post by mlentink on 2007-09-11
> **LynchStreet said:**
> I need to be able to run windows in a shell so I can stay booted to ubuntu.
Why? What would you like to achieve? 

Two options have already been given by previous posters. Keep in mind that running Windows in a virtual machine means that you will need enough memory to run both Ubunu and Windows, and that Windows  memory demands are higher than Ubuntu. Programs in a virtual machine will run about at half their native speed, which is not too much of a problem if you have fast hardware. Wine will run some programs, but certainly not all of them, and a lot may have to bee tweaked before they run.

But theres a third alternative: For most tasks, you dont need Windows at all, because for most Windows programs there are Linux alternatives that are as good, or even better.

Edit: are you really still using 4.10? Upgrade. Youll like it!

---

