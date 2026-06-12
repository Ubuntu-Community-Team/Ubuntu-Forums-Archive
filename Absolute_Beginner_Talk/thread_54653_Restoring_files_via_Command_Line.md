---
title: "Restoring files via Command Line"
date: 2005-08-05
forum: Absolute Beginner Talk
---

### Post by Irony on 2005-08-05
As a newbie to linux one of the things I didn't like doing was changing system files, because if it didn't go right I might find myself booting up into command line and of course I didn't know what to do then.

For example the first time I changed my xorg.conf file to get the GUI to display the correct resolution I ended up at command line instead.

Let's assume you want to change something in the xorg.conf file then first do the following;

Open a terminal and type;

*sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup*

What this does is make an exact copy of your xorg.conf file but the copy is called xorg.conf_backup. You can see this by actually navigating your way to the X11 folder in GUI.

You can now change your xorg.conf file with the knowledge that you can restore it, if it doesn't work;

*sudo gedit /etc/X11/xorg.conf*

Now on booting up if GUI doesn't appear but goes to command line;

[I]ubuntu login; username
password; password[/I]

Then type;

*sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf*

What this does is the reverse of your original copy, i.e. it restores your xorg.conf file to what it was. Now press;

*Ctrl + Alt + Del*

This reboots and should bring you back to GUI.

---

### Post by az on 2005-08-05
Instead of editing the file by hand, try 

sudo dpkg-reconfigure xserver-xorg

This reconfigures the X package.  You can revert changes by running it again ang changing the stuff back.  It is pretty straightforward.

Also, instead of rebooting, you can do
sudo /etc/init.d/gdm restart


If you cannot get into X to run gedit, you can always use nano as a text editor.

sudo nano /etc/X11/xorg.conf

---

### Post by Irony on 2005-08-06
Excellent, good stuff. I'm picking up bits as I go along, so examples like nano and dpkg are very useful.

---

