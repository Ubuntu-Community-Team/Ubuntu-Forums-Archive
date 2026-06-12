---
title: "Slackware to ubuntu problem"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Nebzoroneeleven on 2008-02-23
Well i decided to switch from slack ware to ubuntu because well im a complete comp newb but i wanted to stay with a linux OS.

Anyway i am currently using slackware (dont know which version my dad put it on) and i tried burning ubuntu to a CD but it seems to have screwed up on my somehow.

I used K3b to try and burn it. Evrything looked fine untill i went to restart with the CD in and it went right back to slackware.

Now do i have to get rid of slackware and then restart or did i burn it wrong? i am pretty lost here lol.

---

### Post by finer recliner on 2008-02-23
make sure you are booting from the CD ROM drive.

this can done by editting the boot order in your computer's BIOS.

---

### Post by uberlube on 2008-02-23
If you are having problems with the live CD, I suggest getting the alternate download CD and burn that.

---

### Post by Nebzoroneeleven on 2008-02-23
> **finer recliner said:**
> make sure you are booting from the CD ROM drive.

this can done by editting the boot order in your computer's BIOS.

Ya i pretty much know nothing about computers so youll have to tell me how to edit the boot order and where and what BIOS is lol

---

### Post by Nebzoroneeleven on 2008-02-23
is there anyway to get it to boot from disk from non-root user?

---

### Post by taurus on 2008-02-23
When you first turn on your computer, you will see a message or logo for the motherboard and either at the bottom or upper right side, there is a quick message saying something like press F2 (or whatever the magic key is) to access the BIOS (or Setup).  You need to press that key fast or it will just boot from your harddrive.  So, turn on your computer and start pressing F2 until you get into the BIOS menu.  In there, there should be an option on the top saying something like BOOT.  Navigate to that with the arrow keys and make sure you move CDROM to the top of the list, before harddrive.

Save it and reboot.  Now, if you burnt the ISO image properly, it should boot your machine from the CD.

---

