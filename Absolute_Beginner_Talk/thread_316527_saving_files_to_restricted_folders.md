---
title: "saving files to restricted folders"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2006-12-10
I've seen several threads that nearly answer this question but nothing that really tells me how to do this. I want to be able to edit, delete, and create files that are in folders such as /etc/X11 and other folders. I tried right clicking and going to the permissions tab of properties but that doesn't work. Is the a terminal command I can issue that will give my user name (only mine) read/write permissions to such folders?

---

### Post by igknighted on 2006-12-10
Just use the 'sudo' command when you want to edit these.  You can try 'gksudo nautilus' to open the file browser as root.  You don't want to give yourself those privileges, you would be reverting back to windows-level security.

---

### Post by nickburns on 2006-12-10
You can always use the terminal:

cd /etc/X11

then:

sudo gedit xorg.conf

or:

sudo mousepad xorg.conf (if using mousepad)

to delete:

sudo rm xorg.conf

to delete a folder with all the stuff in it:

sudo rm -R /some/folder

hope this helps.

---

### Post by mongooseman1128 on 2006-12-10
yeah I know I can use sudo to do this, but I'd just like to be able to use the GUI to do this stuff. Also, I can't remember the terminal command to create a file. What is it? ct?

---

### Post by nickburns on 2006-12-10
if you use an editor you can just:

gedit yournewfilename.txt

or:

vi thenewfile.txt

---

### Post by mongooseman1128 on 2006-12-10
wow... I can't believe I never realised that I could use gedit to create a file through terminal. That beats the hell out of my old method (create the file on my desktop then use sudo cp to copy the file where I want it

---

### Post by mcduck on 2006-12-11
> **mongooseman1128 said:**
> yeah I know I can use sudo to do this, but I'd just like to be able to use the GUI to do this stuff.

run 'gksudo nautilus'. But be aware that there's a reason why normal users only have access to their home directories.. And be sure not to forget that root nautilus open, as it allows you to completely destroy your system with a singlw wrong mouse click..

---

### Post by aysiu on 2006-12-11
*gksudo nautilus* is your friend.

Create a launcher or keyboard shortcut for it, if you use it often.

---

### Post by BenHobbs on 2007-07-31
Thank you so much! This helped me a lot! :)

---

