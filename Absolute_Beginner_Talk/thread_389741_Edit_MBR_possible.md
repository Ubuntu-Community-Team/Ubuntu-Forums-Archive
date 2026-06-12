---
title: "Edit MBR possible?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-03-21
I have done something completely silly, in one of my tinkering moods I turned a fully functioning laptop into a useless pile of plastic and metal.

I had Edgy as my sole OS on my laptop, then I decided I might want to install XP too in order to use Photoshop. I made a partition, installed XP but because I wasn't really paying attention I have now ended up with two instances of XP in the windows bootloader even there is only 1 installation.

So my question is, how can I wipe the mbr clean and then start completely fresh with the entire HDD (I intend to install xp first and then edgy).

Thanks! :)

Edit: Basically what I am asking is: can I wipe the entire hdd clean including any mbr data?

---

### Post by freebird54 on 2007-03-21
I don't think you have a problem as such from your description.  Just boot into the one that works (one of them probably will). and edit the file  boot.ini  that is found in your root (hidden file - so you have to enable seeing it in the view menu of explorer).

Just remove the one that is NOT the one you booted with, and the 'problem' will be gone...

---

### Post by jvc26 on 2007-03-21
Were you to re-install Edgy, it would wipe both the HDD and MBR if you told it to and put GRUB back on the MBR. I should think (and seem to remember from my XP days) that reinstalling Windows will also wipe the MBR and put a new copy of the windows bootloader in there. However if freebird's solution works that may save you part of the effort.
Il

---

### Post by PartisanEntity on 2007-03-21
okay thanks to the both of you, ill give it a try tonight, i can't believe i have actually gotten a bit rusty with windows.

---

### Post by freebird54 on 2007-03-21
> **PartisanEntity said:**
> okay thanks to the both of you, ill give it a try tonight, i can't believe i have actually gotten a bit rusty with windows.

I thought rust was inevitable - cheap Windows are bound to leak.....

Anyway - I'm still pretty sure you didn't do anything to the MBR - at one point (with copies of Win on 2 different drives) I had 6 entries for Win XP Pro... only 1 worked, and the edit 'fixed' the confusion.  I had to boot the Live CD to check the partitions, though - to be sure which one was actually working!)

---

