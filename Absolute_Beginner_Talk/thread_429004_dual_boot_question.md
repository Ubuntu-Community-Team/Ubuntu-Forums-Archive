---
title: "dual boot question"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by stajway on 2007-04-30
I have just installed ubuntu dual-booting with vista.  Everything seems to be working great (knock on wood) but i was wondering if i could modify this grub to boot vista automatically instead of ubuntu?  any help would be appreciated

thanks

---

### Post by antoz on 2007-04-30
Yes all you have to do is edit the menu lst and change it in there. Usually from 0 to what ever number corresponds windows. Just remember to start counting from 0.
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

good link to follow for instuctions

---

### Post by Tux Aubrey on 2007-04-30
The answer is yes.  You will need to edit grub's menu.lst file to change the default number to the one matching Vista's position in the list of boot options at the end of the file.  If you are new to this, I'd strongly suggest you back-up menu.lst first and get familiar with the layout and options available - the file itself is a plain text file and is heavily commented.

It can be found in Ubuntu's  boot/grub/ folder.

If you open it with a plain text editor from there (eg. with gedit) it will be read only.  I suggest you do that so that there is absolutely no chance you muck it up.

When you know what you need to change, open it from terminal with the command:

> gksudo gedit boot/grub/menu.lst

enter your password, make the change and save.

If you are at all uncertain, copy your complete menu.lst to this forum and have someone tell you what to change.

---

### Post by stajway on 2007-04-30
Thank you

---

