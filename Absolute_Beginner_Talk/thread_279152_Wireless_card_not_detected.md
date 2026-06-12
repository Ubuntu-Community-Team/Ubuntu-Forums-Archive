---
title: "Wireless card not detected"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by Syd22 on 2006-10-17
I'm currently using xubuntu on my laptop. There is something odd. With the live cd, the os detects my wireless card; and I am able to log on to the internet like I'm doing now. But with the installed program, it detects nothing. In the internet settings, it only gives dial-up as an option.

---

### Post by vayde on 2006-10-17
As I understand it, the Live version has tons of extra drivers that it loads by default, hence your wireless was working.

When it installed, you installed a smaller set, and the one you needed was left out.  That's the problem.

To fix it you will need to find the correct module containing the drivers for your card.  Theoretically you can put the proper module into /etc/modules and it will load on boot from then on.

In my (limited) experience, the module in question is probably on your system, it's just not loading by default.

Post the type of card if you will, and we'll do what we can to help.

---

### Post by Syd22 on 2006-10-17
Its a microsoft wireless card MN-520. How would I go about loading the modules. By the way, thanks alot

---

### Post by Syd22 on 2006-10-17
is there a way for all the drivers to load from the live cd.

---

### Post by vayde on 2006-10-17
Ill tell you how I do it, which is probably way harder and cruder than it has to be- Hopefully someone with a more elegant solution will chime in.

First of all: Learn to love your command line.  There are gui tools, but they don't always get the job done.  The command line allows you to speak to your computer in complete sentances, gui's allow you to point and grunt at things.

Likewise get used to reading the man pages.  They take some getting used to, but it's worth it.

You will need to do some web searching to find the kernel module that your card uses.  Google under:linux drivers <card name>  Look for some driver file that is mentioned.

Go back to your machine.  Im assuming it's a fairly fresh install.  type the following command:

sudo updatedb

this will update the database of files on your system.

after it's done (It might take a few minutes) type the following:
locate <driver file>

if it shows up with .ko on the end, its a kernel module that is in your system.

you can put it in by typing:
sudo modprobe <name of module without the .ko at the end>

That will load it into the kernel for this boot.

If you want it to load automatically, you need to put the name into /etc/modules

use the editor of your choice (I use vim) and add another line with the module name

If all else fails read the man pages for modprobe and for modules

Good luck, and don't hesitate to holler if you need help.

---

