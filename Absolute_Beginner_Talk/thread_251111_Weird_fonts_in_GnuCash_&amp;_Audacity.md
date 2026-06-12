---
title: "Weird fonts in GnuCash &amp; Audacity"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by ramjet_1953 on 2006-09-05
I'm not sure what has happened, but GnuCash and Audacity now have weird, super ugly fonts. They were OK, but for some unknown reason have changed and I can't find any way to change them back.
Please see the attached screenshot.

Regards,
Roger:(

---

### Post by croak77 on 2006-09-05
It's GTK-1 so look for a ~/.gtkrc-1.0 or something like that but not ~/.gtkrc-2.0. You can specify your font in there. Or you can delete the file to go back to the defaults. I'm not sure if switch can change the font of gtk1 apps or not. You can try installing gtk-theme-switch and run 'switch' .

---

### Post by ramjet_1953 on 2006-09-05
Key?
Please speak nubie talk!
I have no idea what your post was all abou!

Regards,
Roger

---

### Post by croak77 on 2006-09-05
There is gtk-1 and gtk-2. Gnucash uses gtk-1. In your /home/username folder ( '~/' = /home/username ) there should be a hidden file ( '.' = hidden ) which controls your gtk-1 style. It should be called something like .gtkrc-1.0 or just .gtkrc. You might have 2 different config files, one for gtk-1 and one for gtk-2, it should be obvious which is which. If you open a terminal, and type, nano -w ~/.gtk then hit the tab key, it will give you a list of files which are in your /home/username/ folder that bgein with .gtk. If you see one for .gtkrc-1 or .gtkrc continue typing the name and open it with nano. There might be a line which controls the font setting for all gtk-1 applications. If there is you can change it to the one you want. 

If you are more confortable using a GUI. Install gtk-theme-switch.Open a terminal and type```
sudo aptitude install gtk-theme-switch
```

Then hit Ctrl-F2 and type switch or run switch from the terminal. You can the change the font and theme. There are not a lot of gtk1 themes. It might also show gtk2 themes but those are not compatible with gtk1. So if you just select the 'Default' theme, there will be a check box and button to select the font and size you want.

---

