---
title: "Starting progroms in terminal as root, problems"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by cheber on 2007-06-20
gimp gives: GIMP could not initialize the graphical user interface.
Make sure a proper setup for your display environment exists.

gedit: GIMP could not initialize the graphical user interface.
Make sure a proper setup for your display environment exists.

I tried to change prompt under etc with bash.bashrc and profile but I changed everything back, So why do I get the errors?

---

### Post by eldepeche on 2007-06-20
Why do you want to run GIMP as root?

---

### Post by Skrynesaver on 2007-06-20
You are logged in as yourself to X-windows (The GUI), so when you attempt to open an application as root on the current display you don't own that display.

You should, as the user who is logged in, gksudo gimp, if you wish to run the application with administrative rights
OR if you wish to run as root (Not advised) log in as root and run the application.

---

### Post by st0nes on 2007-06-20
Why are you trying to run GIMP as root?

---

### Post by kerry_s on 2007-06-20
Why are you trying to launch gimp as root?

the command> gksu gimp

there should be no reason to have to use gimp as root.

sudo >is for root commands
gksu or gksudo > is to launch graphical apps, like the file manger(nautilus), or the editor(gedit), etc...

using root for no reason can mess up your system, you been warned. ;)

---

### Post by cheber on 2007-06-20
I don't _want_ to I just thought I messed something up and wanted to fix it. 
But I guess I didn't mess it up then. Thanks.

I was only logged in as root to change the prompt for it too.

---

### Post by wormser on 2007-06-20
Why are you trying to run GIMP as root?  I had to third that one!

---

