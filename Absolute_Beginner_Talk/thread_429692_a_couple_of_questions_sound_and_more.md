---
title: "a couple of questions sound and more"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by ac1240 on 2007-05-01
hi 
i have ubuntu 7.04 and i dont know how to install sound on my computer??
another:
i have installed ati driver and i wanna know if it was really installed because i cant find any sign of it any were  
another:
how can i copy files to the linux drive(i cant paste files in there ) how can i give the restriction to copy files+how can i copy files from the windows drivers?
another:
how can i write in my language (i have installed it )i can see the desktop in my langauge but i cant write in that langauge why?
how can i make my linux to look like that :
[IMG]http://blog.go4teams.com/wp-content/uploads/2006/04/tv_linux2a.jpg[/IMG]

ty

---

### Post by rhysmc on 2007-05-01
> **ac1240 said:**
> hi 
i have ubuntu 7.04 and i dont know how to install sound on my computer??
another:
i have installed ati driver and i wanna know if it was really installed because i cant find any sign of it any were  
another:
how can i copy files to the linux drive(i cant paste files in there ) how can i give the restriction to copy files+how can i copy files from the windows drivers?
another:
how can i write in my language (i have installed it )i can see the desktop in my langauge but i cant write in that langauge why?
how can i make my linux to look like that :
[IMG]http://blog.go4teams.com/wp-content/uploads/2006/04/tv_linux2a.jpg[/IMG]

ty
Hi
To set the keyboard to your language go to **System > Preferences > Keyboard > Layouts Tab > Add** and choose your keyboard layout (on Ubuntu Feisty)

To get your system to look like that:

I assume you currently are using the GNOME window manager (preinstalled with Ubuntu), That is KDE - The K Desktop Enviroment.

To get KDE:

Note: I have not done this and may have got something wrong

Type (or copy) into the terminal:
```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

When prompted select kdm

When finished logout, and on the login page click **Options > Select session > KDE**.
Click 'This session only' and login.
Next time you login you should use KDE.

As for your other problems you'll have to have a more experienced member help ( Yes I'm a noob)

---

### Post by ac1240 on 2007-05-02
o ok ty for the help
can someone help to fix the other problems

---

