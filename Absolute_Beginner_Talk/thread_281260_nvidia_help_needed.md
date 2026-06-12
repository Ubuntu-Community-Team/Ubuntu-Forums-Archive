---
title: "nvidia help needed"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by SVWander on 2006-10-20
I was carefully following instruction on installing nvidia drivers on one of the how to's listed in this forum. I downloaded the drivers installed them and switch out of GUI well, now I can't get my display back. I had copied the instructions for editing the xorg.conf file but I copied it down incorrectly. Or the backup I made didn't take and I didn't notice. I typed:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
and then typed:
gksudo gedit /etc/X11/xorg.conf
If I remember correctly, because I am typing this on my XP system, I got an error message about gksudo . . . 
anyway, how do I get my display back and where could the problem be?

Of course, since I am not working in Ubuntu I cannot look up my url history to tell you which how to I was following but when I get the system working again maybe I can post that information and figure out how to get my refresh rate from a stomach turning 56 Hz!

Thanks, Tim

---

### Post by ReaderRat on 2006-10-20
This **might** help...
Resolution (Screwed Up xorg.conf)(Need Higher Resolution)
         [http://www.ubuntuforums.org/showthread.php?t=273188](http://www.ubuntuforums.org/showthread.php?t=273188)

---

### Post by SVWander on 2006-10-20
thank you for your help! Going through that setup program let me adjust the screen refresh rate to a more comfortable 75Hz so I wonder if there is even any need to keep playing around with nvidia setup? Do you know why the installation didn't allow me to pick the refresh rate while Ubuntu was setting up? 

Again, thank you for your help.

Tim

---

### Post by ReaderRat on 2006-10-20
No, I don't. I have read here that you may need to install the "nvidia" drivers and not the "nv" drivers sometimes.

See the link below for nVIDIA.

---

