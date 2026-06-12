---
title: "Installing PaintShop Pro in wine"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Ganimede on 2008-01-01
I'm very new to Ubuntu but I've managed to install wine and attempted to install PaintShop Pro 7 following the instructions [here]("https://help.ubuntu.com/community/Wine").  The installer started fine and it said it was installing into Program Files/Jasc Software Inc/Paint Shop Pro 7.  When it finished, there was no error message but neither was there any completed kind of message.  The Jasc Software folder doesn't seem to exist in .wine/Program Files so I presume it didn't install properly and I can't uninstall it either.  If I try to install PaintShop now, I get:

err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr (nil)

Help!  What's gone wrong and how do I fix it?

Edited to add: In response to some comments I have had, I would like to clarify that I am not interested in using the GIMP; I have tried it and find it hard to navigate, plus it yields poorer-quality results, especially when I use it to make animated graphics which I do a lot.

---

### Post by jken146 on 2008-01-01
Check out winehq.org to see if someone has successfully run this program in wine before.

Or better still, use the GIMP.

---

### Post by Ganimede on 2008-01-01
According to winehq.org, PaintShop Pro 7 works "flawlessly with some special configuration" although I can't find anywhere what that is.  

I don't like The GIMP.  I find it awkward and it doesn't do what I want.

---

### Post by Ganimede on 2008-01-02
*bump*

---

### Post by t0p on 2008-01-02
I realize this probably isn't what you want to hear: but why bother trying to get Paintshop Pro to run when you have the GIMP?  You said the GIMP "is awkward" and doesn't do what you want it to do... but that's simply a matter of getting used to a different program.  As a user of both packages, please let me assure you, the GIMP does *everything* Paintshop Pro can do, *and more*.

All you need to do is google for some GIMP beginner's tutorials - you'll soon see that the GIMP is far more featureful than Paintshop Pro.

Also, please remember that **Paintshop Pro is not a Linux program**.  Wine will allow you to run some Windows progs in Linux, but it isn't a foolproof, 100% solution.  Personally, I don't think Wine is a good idea at all.  If you want to run Windows programs, run them in Windows.

---

### Post by candtalan on 2008-01-02
As t0p says, running paint shop pro in linux under wine is likely to be a less than perfect experience. I have a paid for copy of psp here and I happened to stop using it when I moved to linux. It *was* inconvenient to 'loose' it. As you know, psp has some convenient stuff. Not only that, but it took me some weeks to get to learn that stuff originally! I have used gimp since, not psp, mostly on principle, because I was determined to move away from windows, and if a product was stuck in windows, then I was no longer going to stay stuck.

However, if psp had been more necessary then I would have used it in dual boot machines. We did keep dual boot machines for a long time, just in case, anyway.

---

### Post by Rocket2DMn on 2008-01-02
I would have to agree with the OP that GIMP is a little awkward to use, and I especially don't like the interface that doesn't allow you to have all its subwindows in it's own window.  However, wine is a nice tool for some things, but it rarely seems to work with large programs.  I use PSP in windows, so if you're really serious about using PSP, you should set up a dual boot system, otherwise you should probably learn GIMP.

---

### Post by crjackson on 2008-01-02
> **Ganimede said:**
> I'm very new to Ubuntu but I've managed to install wine and attempted to install PaintShop Pro 7 following the instructions [here]("https://help.ubuntu.com/community/Wine").  The installer started fine and it said it was installing into Program Files/Jasc Software Inc/Paint Shop Pro 7.  When it finished, there was no error message but neither was there any completed kind of message.  The Jasc Software folder doesn't seem to exist in .wine/Program Files so I presume it didn't install properly and I can't uninstall it either.  If I try to install PaintShop now, I get:

err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr (nil)

Help!  What's gone wrong and how do I fix it?

Edited to add: In response to some comments I have had, I would like to clarify that I am not interested in using the GIMP; I have tried it and find it hard to navigate, plus it yields poorer-quality results, especially when I use it to make animated graphics which I do a lot.

You can install vBox and run a windows install under Ubuntu.  Install PSP there and you won't have to physically reboot your system to use it.

---

### Post by kellemes on 2008-01-02
> **crjackson said:**
> You can install vBox and run a windows install under Ubuntu.  Install PSP there and you won't have to physically reboot your system to use it.


This is your best bet indeed.
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by Ganimede on 2008-01-04
> **crjackson said:**
> You can install vBox and run a windows install under Ubuntu.  Install PSP there and you won't have to physically reboot your system to use it.
What is vBox? I have no idea what that does or what it's for.

---

### Post by phil90 on 2008-01-30
Vbox is a virtualization software. With this software you can run another operating system into Ubuntu. 

For example you could run Windows Xp in Ubuntu and then run the software in windows which is running in linux.

---

