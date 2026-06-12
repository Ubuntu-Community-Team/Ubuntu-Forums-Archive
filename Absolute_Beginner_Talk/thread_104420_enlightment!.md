---
title: "enlightment?!"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Esca on 2005-12-16
hi,

i installed enlightment (some kind of theme...) 
it works perfectly but the only problem is that i find my menu (no the apps, system settings) nowhere, i cant find my options and it looks like i am in a totally different os. I would rather just return to the ubuntu standard theme.

so the question is, how do i get rid of this "theme" (not really a theme as it seems to have changed my os)

thanks for you're help

Frederic

---

### Post by redactech on 2005-12-16
which enlightenment it is ? E-16 or E17 ?

Assuming it is E16

did you try the middle button, the right one ? (if you are on a laptop with a synaptic pad) try to use the ctrl key with the right/left button

Also you should find in the menu a "generate menu" it will create shortcut for all the KDE/gnome shortcuts

if you want to change your themes (there's hundred of them) go to themes.freshmeat.net. At the same place you'll find detailed instruction on how to change your themes...

---

### Post by Perfect Storm on 2005-12-16
Enlightenment is a window manager, that's why it may seems strange compared to the default Gnome Desktop envoriment. One of the beauty of Linux is there are many diffrent Desktop envoriments and Window managers. Everyone with its own strengths and weakness. But also what you need and what you want with your Pc.

[http://enlightenment.sourceforge.net/](http://enlightenment.sourceforge.net/)

---

### Post by Esca on 2005-12-16
i still would like to get rid of enlightment...

how do i do so?

thanks

---

### Post by endersshadow on 2005-12-16
Did you follow the HowTo or install it from Synaptic/apt-get?

---

### Post by Esca on 2005-12-18
i did an apt-get to install it

thanks for the help

edit:

i did it like this...

[http://www.ubuntuforums.org/showthread.php?t=54476&highlight=enlightment](http://www.ubuntuforums.org/showthread.php?t=54476&highlight=enlightment)

---

### Post by Wolki on 2005-12-18
[QUOTE=Esca]i did an apt-get to install it[/QUOTE]

Hm... did you only install enlightenment or try to enlighten your Gnome? If you're gnome (or other favorite DE) is still normal, just choose it on the login screen (under "session"), then "sudo apt-get remove enlightenment", or use synaptic)

If hou have enlightened gnome, you changed a line in your ~/.gnome2/session file, undo this change and your gnome should use metacity again (if it doesn't, try executing "metacity --replace"). then uninstall as above.

If you have further questions or problems, feel free to ask.

---

