---
title: "Synaptic downloads not showing in menus"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Kersus on 2006-03-19
So I've downloaded various programs and games via Synaptic, but don't see any of them in the menus, or have any idea how to access them.  Is there a way to get them into the menus?

---

### Post by m.musashi on 2006-03-19
I've noticed this too. I recently downloaded atomic tanks (I think that was the name) but it did not appear in the menu anywhere. In this case, I was still able to launch in by opening up a terminal window and typing "atanks". You can try that approach (the terminal) or you can add a launcher to the menu. I'm not sitting in front of ubuntu at the moment and can't quite remember how to do that but I think there is something about menu editor.

---

### Post by Ozitraveller on 2006-03-19
Yes there is a menu edit under the accessories menu.

The problem with applications not setting themselves up in the menus mostly lies with the developer/packager and whether done what is necessary to add their applications into the menus.

---

### Post by Kersus on 2006-03-19
I don't have a menu edit under accessories.  Using Hoary-gnome.

---

### Post by Kersus on 2006-03-19
I guess I could write down a list of what I've downloaded so I can play from terminal....  but it would be nice to know how to add it to the menu...

---

### Post by KansasJoe on 2006-03-19
You need to find the executable for it by typing which programname

e.g. say your program is called firefox then type in terminal

which firefox

it will show you the path to the executable and then you can paste it to your desktop or add in into your menus since you now know the path

---

### Post by Kersus on 2006-03-19
Okay, I figured out how to find my installs, and add them to the desktop, but how do I add them to the menu?

---

### Post by ice.man on 2006-03-19
i have a problem with not been about to see phpmyadmin but yet my other linux box can, any idears what to do there as i would like it on my box that can't see it as it is my webserver

---

### Post by Sutekh on 2006-03-19
[QUOTE=Kersus]Okay, I figured out how to find my installs, and add them to the desktop, but how do I add them to the menu?[/QUOTE]

Two ways I can think of


1 - Create the .desktop files that GNOME uses for its menu structure

[Ubuntu Forums - HOWTO: Create and Polpulate Sub-menus in the Applications Menu]("http://ubuntuforums.org/showthread.php?t=36479")

[Ubuntu Forums - HOWTO: Create GNOME Menu Entries](http://ubuntuforums.org/showthread.php?t=61713)


2 - Install SMEG (Simple Menu Editor for GNOME) or Alacarte (as its known now)

[http://ubuntuforums.org/showpost.php?p=475145&postcount=15]("http://ubuntuforums.org/showpost.php?p=475145&postcount=15")

[Alacarte - 0.8 (may not work with Hoary)]("http://www.realistanew.com/projects/alacarte/")

---

### Post by SSTwinrova on 2006-03-19
If the packages are from Main or Universe, might not be a bad idea to file a bug against them so that this issue can be corrected.

[https://launchpad.net/malone](https://launchpad.net/malone) -- "File a Bug on a Package" link near the top would be my guess

---

### Post by ice.man on 2006-03-19
SSTwinrova, was your post for me or Kersus??

---

### Post by Ozitraveller on 2006-03-19
Alacarte Menu Editor
[http://ubuntuforums.org/showthread.php?t=82537](http://ubuntuforums.org/showthread.php?t=82537)

---

### Post by SSTwinrova on 2006-03-20
[QUOTE=ice.man]SSTwinrova, was your post for me or Kersus??[/QUOTE]
It was intended for Kersus.

For you, are you saying that phpMyAdmin isn't showing up in a menu? Since it's not a "desktop" application, I wouldn't really expect it to -- it's designed to be brought up by just going to the address it listens on. As for seeing it on your webserver, have you installed it on that actual box?

---

