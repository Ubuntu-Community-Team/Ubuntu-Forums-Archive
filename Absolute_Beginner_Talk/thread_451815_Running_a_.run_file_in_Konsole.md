---
title: "Running a .run file in Konsole"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by gantww on 2007-05-22
Hello all,
I'm trying to get the ATI drivers installed on my machine. Apparently I have to run a .run file from the command line. I marked the file as executable, but I can't run it from Konsole. Is there something else I need to do to make it work?

Thanks,
Will

---

### Post by Kobalt on 2007-05-22
You need to launch it this way : ```
sudo sh file.run
```

---

### Post by myoungf1 on 2007-05-22
For some reason sh won't work with the ATI .run file you need to use bash to have it work properly 

sudo bash file.run

---

### Post by khardbored on 2007-05-22
I'm in a similar situation. Instead of starting a new thread I figure I'll just semi-hijack this one. I need to install some video drivers as well but I need to get out of X windows. Uhm. How do I quit gnome and get dropped directly to a bash prompt?

---

### Post by myoungf1 on 2007-05-22
> **khardbored said:**
> I'm in a similar situation. Instead of starting a new thread I figure I'll just semi-hijack this one. I need to install some video drivers as well but I need to get out of X windows. Uhm. How do I quit gnome and get dropped directly to a bash prompt?

You shouldn't have to get out of gnome to get to a command prompt just run the .run file from a terminal window.  But if you still want to just reboot into rescue mode from the boot loader to get to the command prompt.

---

### Post by khardbored on 2007-05-22
> **myoungf1 said:**
> You shouldn't have to get out of gnome to get to a command prompt just run the .run file from a terminal window.  But if you still want to just reboot into rescue mode from the boot loader to get to the command prompt.

I fire up a terminal and attempt to install the new Nividia drivers and it yells at me to get out of X. :(

---

### Post by myoungf1 on 2007-05-22
> **khardbored said:**
> I fire up a terminal and attempt to install the new Nividia drivers and it yells at me to get out of X. :(

Oh okay i don't have an nvidia card but an ATI card so if it asks to restart then choose the rescue selection from the boot screen on restart and you should be good to go.

---

### Post by RomeReactor on 2007-05-22
Hi. khardbored, the easiest way to do that is to press **CTRL+ALT+F1**; that drops you to the terminal, and then you enter:
```
sudo /etc/init.d/gdm stop
```
to stop the graphical desktop manager; afterwards run the nvidia installer, and when that finishes:
```
sudo /etc/init.d/gdm start
```
to start GDM again, and lastly, press **CTRL+ALT+F7** to return you to your desktop.

---

