---
title: "Themes wont Install"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by ShadyTails on 2006-08-23
Hi everyone, Ive just installed Ubuntu and im liking it so far, but im having trouble getting themes installed, ive tried 3 thmes and none of them will install, heres a screenshot.

"The File Format is Invalid"

[IMG]http://img181.imageshack.us/img181/5796/error1dq4.png[/IMG]

---

### Post by aysiu on 2006-08-23
Can you link to the theme you're trying to install?

---

### Post by ShadyTails on 2006-08-23
okay, here

[http://www.gnome-look.org/content/show.php?content=32227](http://www.gnome-look.org/content/show.php?content=32227)

---

### Post by aysiu on 2006-08-23
Ah! The problem is that it is not a Gtk 2.0 theme (I know it's listed as one, but it's not one).

If you look inside, there is a Gtk theme, a Gtk 2.0 theme, a metacity theme, and an XFWM4 theme.

A regular Gtk 2.0 theme is just that--a .tar.gz containing one folder with a bunch of pictures in it and a gtkrc file.

In other words, you can't just drag and drop it in as you would any other theme--this one is packaged badly.

To do a manual install, double-click VistaBut.tar.gz and extract it. A new folder called VistaBut should appear on your desktop. Copy and paste that to /home/shadytails/.themes

Keep in mind that .themes is a hidden folder, so when you go to /home/shadytails, press Control-H so you can see the .themes folder.

---

### Post by ShadyTails on 2006-08-23
Well, I tried the GTK 2.0 Folder and it did the exact same thing.

---

### Post by aysiu on 2006-08-24
What do you mean you "tried the GTK 2.0 Folder"? What exactly did you do?

Never mind.

Just paste these commands into the terminal: ```
wget -c http://www.users.monornet.hu/linux/gtk2/VistaBut.tar.gz
tar -xvzf VistaBut.tar.gz
mv VistaBut ~/.themes/VistaBut
mv VistaBut.tar.gz ~/.Trash/VistaBut.tar.gz
```

---

### Post by nalmeth on 2006-08-24
The theme manager is expecting a tar.gz. Follow aysiu's advice and copy the folder to the hidden .themes folder in your /home

---

### Post by aysiu on 2006-08-24
> **nalmeth said:**
> The theme manager is expecting a tar.gz. Follow aysiu's advice and copy the folder to the hidden .themes folder in your /home
Whoops!

You're right, nalmeth. ShadyTails must have unzipped the .tar.gz.

I just tried dragging and dropping the .tar.gz on to the Theme Manager window, and it worked just fine.

ShadyTails, make sure you drop the .tar.gz in **exactly as you downloaded it from Gnome-Look**. Do not double-click the .tar.gz or try to unzip it.

---

### Post by ShadyTails on 2006-08-24
Ahhh thanks! XD now i feel stupid.

---

