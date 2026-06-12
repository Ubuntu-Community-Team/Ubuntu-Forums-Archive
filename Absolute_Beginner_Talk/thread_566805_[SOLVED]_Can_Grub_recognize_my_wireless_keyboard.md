---
title: "[SOLVED] Can Grub recognize my wireless keyboard?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by svriderpokey on 2007-10-03
Can Grub be configured to recognize (and respond to) my wireless keyboard, or do I have to plug in a wired one to select windows?

Alternately can grub be set to boot windows first until I get my ubuntu glitches worked out?

---

### Post by peabody on 2007-10-03
Grub can be configured to boot windows by default, although I'll admit to being fuzzy on the details, I believe it involves editing the menu.lst file.

As for your wireless keyboard, that depends.  Can you use it to access your BIOS?  If you can, there should be a way to get it to work with grub, otherwise your only option will be to have a wired keyboard around as backup.

---

### Post by Pumalite on 2007-10-03
To answer you 2nd question: edit menu.lst.
Backup first
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back, then
gksudo gedit /boot/grub/menu.lst
Change the line: 'default=0' to 'default=?' depending on the number of your Windows entry, knowing that Grub starts counting from 0
(default=0 corresponds to your first Ubuntu entry)

---

### Post by jw5801 on 2007-10-03
There will be an option in your bios somewhere to "Enable Legacy Support for USB devices" or something along those lines anyway. Assuming that the keyboard is USB? If it's bluetooth then there might be something similar, I'm not so sure on that one.

The issue probably isn't whether it's wired or wireless, just how it plugs in to the computer. USB inputs are generally handled by the OS rather than the bios, but there should be an option to let it handle the input.

---

### Post by svriderpokey on 2007-10-03
wow, you guys are fast.  If I can get Grub to handle my KB I won't need to change boot order, so I'll try that first.  The wireless is USB 2.0 off of a card.  Should I try it off of the USB 1.1 port directly off of the MoBo?  

If I let the BIOS handle the USB, Will it slow down or otherwise affect USB Function?

---

### Post by jw5801 on 2007-10-03
It should run exactly the same. I'm reasonably sure that once the kernel actually boots it still takes over control of the device (someone correct me if I'm wrong), the option in the bios will just let the bios handle it until then. The one off the card should work just as well. I have mine setup like that.

---

### Post by svriderpokey on 2007-10-03
My bios does not say anything about USB other than in boot order.  I'll just have to try to make windows the first boot.  Is there a way to shorten the countdown while I'm at it?

What is the purpose of backing up Grub?  If I wreck it, I wouldn't know how to fix it.  I'd just have to reinstall Ubuntu.

I'm a big noob!  Ignorance is such bliss.  :p

---

### Post by bsharp on 2007-10-03
There is a way to shorten it, I just can't remember the exact phrase but if you look through your menu.lst file then you should find something that will let you change the wait time.  Always back up changes to system files because it is easier to restore a backup than trying to figure out what you did wrong.

---

### Post by svriderpokey on 2007-10-03
> **bsharp said:**
>  it is easier to restore a backup than trying to figure out what you did wrong.

I'd just have to reinstall Ubuntu.  I really have no Idea what I'm doing yet.

---

### Post by svriderpokey on 2007-10-11
My BIOS simply does not have a driver for my (any) USB card (duh).  I just had to plug it into the USB port on the MOBO.  

I generally try not to use those ones, because they are USB 1.1, and the card is 2.0.  

Big 'ol [SIZE="7"]SOLVED![/SIZE]  Thanks for the help guys.  

P.S. I did edit GRUB as well, and that was helpful.  Thank you

---

### Post by Pumalite on 2007-10-11
Good for you! Happy Ubuntuing!

---

