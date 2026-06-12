---
title: "no keyboard?"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by pfnork on 2008-01-14
Have two seperate CD's of Ubuntu.   Trying to install in a new HP puter that came with Vista.

My problem is that Ubuntu does not recognize my keyboard.  Even tried two different keyboards and two different CD's of the software.

The mouse works fine.

---

### Post by crjackson on 2008-01-14
Do you mean that is sees NO keyboard at all?

Is this a USB keyboard?

---

### Post by pfnork on 2008-01-14
It is not a USB keyboard.  Tried two different ones.

The keyboard works normal in Vista.

The keyboard does not work in Ubuntu.  No response to any keys.

Thanks for any help.

---

### Post by Rocket2DMn on 2008-01-14
Can you boot into recovery mode and use the KB?  If so, you may need to reconfigure Xorg to recognize your KB, which requires you to run the following command.  This command typically requires "sudo" to start with but at the recovery mode terminal you are logged in as root
```
dpkg-reconfigure xserver-xorg
```
You will be asked questions about your hardware (refer to your new computer's manuals and order details if necessary).  You will have a chance to select a KB type, you will probably want 105 key generic US layout.  You will also be asked about video card and monitor, do your best (use TAB to move around and SPACEBAR to select).  Choose your monitor's highest resolution and everything less.  When asked about drivers, use "nv" if your card is an nvidia and "ati" if your card is an ATI card.

---

