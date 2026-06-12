---
title: "Permissions in file system"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by soul_motor on 2007-08-07
I was reading a tutorial on how to add fonts to Ubuntu and decided why not.  I made the directory it told me to, but when I tried to copy the font to the folder I made, I don't have user privileges.  I'm the only user on the computer, how do I get privileges to paste a file???  Thanks in advance.

---

### Post by xopher_mc on 2007-08-07
firstly, what tutorial were you following?

putting sudo before the command given should give you the ability to copy it.

If not you need to check the permisions of the folder. To do so type in the directory that you folder is in

ls -l | more

and post the line regarding your folder.

---

### Post by forestpixie on 2007-08-07
If you want to add to a folder through nautilus (file manager)
open a terminal and enter

gksudo nautilus

will allow you to add a font into the folder _ you'll get an error message - it's a bug, so don't worry. But be careful while you're using nautilus as root

---

### Post by proalan on 2007-08-07
which directory did you put the fonts in?

normally I do it by

creating a folder named .font in my home folder e.g. /home/myaccount/.font
then copy the fonts over to that folder.

then in a terminal do
 ```
sudo fc-cache -f -v
```since the home folder belongs to you, you should have permissions to read / write to it.
you can check the permission of your folder by checking the permissions tab in the properties menu.
or in a terminal do
```
ls -la
```

---

### Post by stchman on 2007-08-07
> **soul_motor said:**
> I was reading a tutorial on how to add fonts to Ubuntu and decided why not.  I made the directory it told me to, but when I tried to copy the font to the folder I made, I don't have user privileges.  I'm the only user on the computer, how do I get privileges to paste a file???  Thanks in advance.

Follow my tutorial:

[http://www.stchman.com/install_fonts.html](http://www.stchman.com/install_fonts.html)

---

### Post by soul_motor on 2007-08-07
I was following the instructions at [http://howtoforge.net/sharp_fonts_gnome](http://howtoforge.net/sharp_fonts_gnome)  I did pretty good up until the second page where it had me paste the font into the directory...  There seems to be enough info here for me to get it in there.  Thanks for the help

---

