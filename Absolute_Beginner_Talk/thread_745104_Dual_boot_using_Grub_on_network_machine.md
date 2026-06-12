---
title: "Dual boot using Grub on network machine"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Daniel Foligie on 2008-04-04
Hi everyone

I'm hoping to install Ubuntu on my machine at work (currently running WinXP), and set up a dual-boot system using grub or something similar.  The hassle is that the IT guys for the company I work for are terrified of any "non-standard" software and when I mentioned Linux they said "Yes, we've heard of it" i.e. they are strictly MS guys at present.  

I initially wanted to install C-code programming software in the WinXP environment, to be able to use after hours to program microcontrollers, but there's no chance the IT guys are going to allow that.  So, I'm now considering installing Linux myself and working away quietly on that, as what I'm doing is in no way malicious.  As far as I know, avrgcc and avrdude will be perfect for my needs, using only the workstation.

Questions:

Firstly, does anyone know if avrgcc and avrdude are easy to install on Ubuntu? 

Secondly, if I install Ubuntu with grub, does anyone know if there'll be a way for the network guys to pick this up?  I'm thinking not, as grub kicks in before Windows starts booting up.  However, I'm just concerned that if an administrator tries to switch my machine on remotely (e.g. for some routine check or network update), that grub will prevent this from happening.

Any thoughts on the matter?

Cheers, 

Daniel

---

### Post by Het Irv on 2008-04-04
Second point:
Grub's default is Ubuntu, in your situation, what you may want to do is:
Set Xp as default in GRUB
Set GRUB so that you have to press ESC to show the menu.

That way if an IT guy does boot your computer (remote or local), it will take them to XP automatically.

Sorry, but I don't know the steps that you need to accopmlish this.  But, I know it can be done.

---

