---
title: "Huh? Desktop blocked"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by ignorance on 2006-05-02
I blocked myself from writing to my desktop how did i do that.

Error while moving items to "/home/bla/Desktop".
You do not have permissions to write to this folder.

---

### Post by aysiu on 2006-05-02
Reboot and choose "recovery mode" from the Grub menu.
It's between the regular boot and "memtest."

You'll then be logged in as root. Type ```
chown -R bla:bla /home/bla
``` Then reboot into normal mode.

---

### Post by ignorance on 2006-05-02
i don't really get it

but i figured out that i made my desktop root

---

### Post by ComplexNumber on 2006-05-02
[quote=ignorance]i don't really get it

but i figured out that i made my desktop root[/quote] how did you manage that? the only thing i can think of is by going to the terminal and typing 'chown -R root:root /home/bla'. to set the permissions back again, its 'sudo chown -R bla:bla /home/bla'

EDIT: oops. just noticed that thats what aysui said :D

---

### Post by aysiu on 2006-05-02
I'm trying to tell you how to get it back from root.

Go to the KMenu or the Gnome menu and select **Logout**.

One of the logout options should let you reboot your computer.

When you select reboot, one of the first things you should see, if only for a few seconds is a boot menu that lets you pick one of several options.

The default option will most likely be Ubuntu Kernel 2.6.### something.

The option underneath that will be Ubuntu **recovery mode**

The third option will be Ubuntu memtest.

Using the down arrow on your keyboard and the Enter key, select the second option (**recovery mode**)

Wait until Ubuntu finishes booting. You'll then be at a black screen with white text.

You'll then be logged in as root, and you will have the ability to type things.

Type this: ```
chown -R bla:bla /home/bla
reboot
``` When you get to the boot menu, select the top option instead of recovery mode.

**Edit**: Okay. I'm stupid. Yes, if you have *sudo* working fine, you don't need to boot into recovery mode. Just go to the terminal and copy and paste this command: ```
sudo chown -R bla:bla /home/bla
```

---

### Post by ignorance on 2006-05-02
thnx for the help

---

### Post by ComplexNumber on 2006-05-02
[quote=ignorance]thnx for the help[/quote] also, don't forget to put 'sudo chmod -R 960 /home/bla'. this makes your home directory writable.

---

