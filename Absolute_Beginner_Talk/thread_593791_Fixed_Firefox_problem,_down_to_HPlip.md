---
title: "Fixed Firefox problem, down to HPlip"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by ah pook on 2007-10-27
HPlip is still not working. I've removed it, and reinstalled it, but it still won't do anything. any ideas?

---

### Post by jimrz on 2007-10-27
> **ah pook said:**
> HPlip is still not working. I've removed it, and reinstalled it, but it still won't do anything. any ideas?

ok ... what is not working for you and what are you trying to get it to do?

---

### Post by ah pook on 2007-10-28
see the HP C5180, and Print. nothing fancy....

works in Feisty, just not Gutsy

---

### Post by jimrz on 2007-10-30
> **ah pook said:**
> see the HP C5180, and Print. nothing fancy....

works in Feisty, just not Gutsy

Did you go through the "add a printer" process and set it up? If so and assuming you are using gnome DE, try installing "gnome-cups-manager" (same thing that we used in feisty) from synaptic, remove the printer (not the whole foomatic thingy as the 2 can coexist just fine) and add the printer using the gnome manager. This will also simplify sharing the printer via cups and get your pdf printer to save to "PDF" folder in your /home (rather that whatever out of the way place foomatic saves them to).

---

