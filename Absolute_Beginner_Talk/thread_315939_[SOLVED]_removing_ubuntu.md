---
title: "[SOLVED] removing ubuntu"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by squrl on 2006-12-10
Is there a way to get the dual boot out of the machine. Windows is on one drive and Ubuntu on another. I am giving up and want to remove the dual boot.I can just pull the second drive out but how to get rid of the dual boot loader???

---

### Post by AAM on 2006-12-10
are you removing Windows or Ubuntu?

---

### Post by bodhi.zazen on 2006-12-10
Restore windows MBR:

Yes boot from the (windows XP) cd.



Windows will come with some screens and look at "repair an existing XP" or something like that.

NOT THE AUTOMATIC REPAIR it will bring you nowhere.



You get three options,install windows,repair an existing XP or quit.



Choose "repair" ; You get a black screen where the existing install [a number] is displayed.



Choose that number and then it asks for your administrator password.



Type in ADMINISTRATOR if you don't know otherwise and pray it's the right one.



Then you get a prompt.

Type fixboot and see what it tells you.

If this doesn't work type fixmbr and you get a warning about messing up things,but ignore,and proceed.



This should make your windows bootable again.

---

