---
title: "[SOLVED] How do I make grub stop and wait for OS choice at boot?"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by ocean223 on 2007-09-07
Grub used to wait for me to choose which OS to boot. The last two times I installed Ubuntu, Grub just gives me brief time to hit esc key to get to the OS list. Do I have to modify menue.lst or something?

---

### Post by philinux on 2007-09-07
Your correct in menu.lst there is an entry for the countdown in seconds.

 gksudo gedit /boot/grub/menu.lst

---

### Post by Lord Illidan on 2007-09-07
Yes, if you want to post your /boot/grub/menu.lst here, we can tell you what to change.

---

### Post by justleen on 2007-09-07
you can edit the time out value in /boot/grub/menu.lst

im not sure if you can comment out the line, but at least you can change it here to something more comfortable
# time in seconds..
timeout=30

---

### Post by Tomosaur on 2007-09-07
Editing menu.lst by hand is worth learning how to do, but if you don't wish to do that, then you might like to try GrubEd, which is a gui tool which should do what you need :)

The link is in my sig.

If you still just want to edit menu.lst by hand, type the following in a terminal:
```

gksudo gedit /boot/grub/menu.lst

```

Type your password in the box which pops up, then once the file is open, look for the line which says 'timeout'. Simply change the number there to however many seconds you want the grub menu to display for.

---

### Post by ocean223 on 2007-09-07
Okay, thanks. I can't post menu.lst 'till later though.  If you could just point out what to change for the countdown I may be able to figure it out since I've been in there before to add XP to my boot list. (For some reason when I installed Gutsy, my XP partition did'nt shoe up in grub so I had to add it.)

Thanks in advance!:)

---

