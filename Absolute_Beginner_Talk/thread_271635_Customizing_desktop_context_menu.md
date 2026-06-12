---
title: "Customizing desktop context menu"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Tamil on 2006-10-05
Is it possible to customize desktop context menu?

---

### Post by kerry_s on 2006-10-05
In what?(gnome,kde,xubuntu,other)

---

### Post by Tamil on 2006-10-05
> **kerry_s said:**
> In what?(gnome,kde,xubuntu,other)GNOME

---

### Post by Tamil on 2006-10-05
I want to add shorcuts in context menu.

---

### Post by chavo on 2006-10-05
In gnome there's no way to do it without altering the source.
 In KDE you can use whatever menu you want for all 3 mouse button clicks. You can also create your own menus.

---

### Post by Tamil on 2006-10-05
Thanks.

---

### Post by kerry_s on 2006-10-05
That's not exactly true. You can create a type of custom menu. using natilus scripts. In your home folder go to (hidden file)->  /.gnome2/nautilus-scripts
Then right click and create a text file then open the file with gedit and put your command for the application you want to launch. Then close it and right click it and make it execute(executable).

Example of launcher to launch nautilus as root in /

```
#!/bin/sh
gksudo nautilus /

```


as long as you make the text file executable, it will launch, you can even skip the "#!/bin/sh" and just put the command.

example:
firefox

I haven't used my Gnome desktop in age's, let me do some updates and i'll post some pics to make it easier for you to follow.

---

### Post by y6FgBn)~v on 2006-10-06
Kerry could you post or pm me with your script for terminal. It would be very much appreciated.

Thanks,

Bill

---

### Post by jaboua on 2006-10-06
If you only want a terminal shortcut, you might as well install "nautilus-open-terminal".

---

### Post by y6FgBn)~v on 2006-10-06
Thank you Jaboua. :D

---

