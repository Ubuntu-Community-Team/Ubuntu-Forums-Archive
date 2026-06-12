---
title: "Hard Xserver Crash"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by LaDeDa on 2007-10-22
I installed the Realtek package for Linux.  There was a section to be copied and pasted into the Xserver-xorg file.  Did it all, and on reboot, I get nothing but the command line and a message saying the system wouldn't load because it didn't recognize Realtek ALC888 although PRIOR to the package install, it was listed along with Alsa.  How could I have recovered from the "no boot" situation ??

---

### Post by realvz on 2007-10-22
do you even get to a point where the system prompts you for a username password?

---

### Post by LaDeDa on 2007-10-22
Yes, but then it was back to the command line.  Seemed the only commands acceptable were from Gnome help.  I was hoping I could get into the xorg.conf file and delete anythng to do with Realtek, however, I was stuck at the command line.

---

### Post by realvz on 2007-10-22
sudo nano /etc/X11/xorg.conf

edit as you please

then ctrl+x to close...press Y to save

---

### Post by LaDeDa on 2007-10-22
OK, I entered sudo /etc/X11/xorg.conf (no nano),  and each time, received the message about doing --help to get available commands.  Was leaving out "nano" the error here ??

---

### Post by realvz on 2007-10-22
yep...nano is the editor that you will use to edit xorg.conf file...

its just like gedit...but text based

---

### Post by LaDeDa on 2007-10-22
So, I should always use "nano" rather than gedit or is its use specific to my situation ?
And thanks very much for you help !!!

---

