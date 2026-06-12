---
title: "[SOLVED] Dual booting two harddrives Linux on first"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by Tierial on 2007-09-21
I know theres numerous posts on how to dual boot and everything with different harddrives.. and I understand them --however.

I already have Linux installed on my first (SATA II) 80gb HD. and then hooked up my 320gb HD after (as 0 on the boot order on the motherboard) and installed XP on that HD...

I have both plugged in, Linux as 0, XP as 1. But of course, linux's GRUB doesn't see my Windows XP Professional..

Almost every guide I've read says to put XP on the first drive, then install linux after and it does it for you? But both are already setup, and I don't want to have to reinstall XP or Linux.

Is it possible for me to do this?
I go to the boot part at the bottom of the menu.lst in GRUB and it shows the title, root, kernel, etc etc for the different ways to boot into Ubuntu 7.04 Feisty...

And I don't exactly understand how to add XP to it.

---

### Post by wolfen69 on 2007-09-21
i know alot of people may not do it this way, but here's how i do it: pull the power from one drive while installing on the other drive. then i have a quick boot option at restart.(F12) and pick which drive to boot to. that way, xp's MBR doesnt get borked or ubuntu's grub is not needed. works perfect every time.

---

### Post by alienexplorers on 2007-09-21
Your going to need to setup drive 1 with your xp on it like so:
> Title Microsoft Windows XP Professional
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
savedefault
makeactive
chainloader +1

---

### Post by Tierial on 2007-09-21
That code won't make it boot to xp first or anything, will it?

I tried the F12 thing, and it asks me only if I want to boot to an Onboard SATA drive, then goes straight to Linux's GRUB loader.


EDIT: Another question worth adding...
Does it need to be tabbed out like linux has the list? or can I literally copy paste that.

---

### Post by alienexplorers on 2007-09-21
No the boot option is set in your menu.lst file near the top.  If set to 0 it should boot ubuntu first.

---

### Post by Tierial on 2007-09-21
sweet- Awesome. Thanks for the help!
I'm trying it right now.

---

### Post by alienexplorers on 2007-09-21
Is the system working OK?

---

