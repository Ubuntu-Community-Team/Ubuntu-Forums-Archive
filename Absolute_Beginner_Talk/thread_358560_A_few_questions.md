---
title: "A few questions"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by BlackBar on 2007-02-11
Im new to the ubuntu OS and only find a few things that i cant find an answer to #1 how can i sync music and videos to my 5th gen ipod #2 how and i make my screen resolution in wide screen formate and mush higher then what its at now , #3 how do you install new themes and were can i find new themes the last question i have is if i remove the recycle bin for the try how do i bring it back :lolflag:. thanks for any help people can give me

---

### Post by Maestro23 on 2007-02-11
For your themes: [http://www.kde-look.org/](http://www.kde-look.org/)

Each one comes with a README(should) with instructions

That site also has links to gnome-look.org and Xcfe-look.org

---

### Post by aysiu on 2007-02-11
#1. No idea, but maybe you can try Banshee or AmaroK

#2. Read this:
[http://ubuntuforums.org/showpost.php?p=129379&amp;postcount=21](http://ubuntuforums.org/showpost.php?p=129379&amp;postcount=21)

#3. If you're using Ubuntu (and not Kubuntu or Xubuntu), download a theme (GTK, Metacity, or icon) from [http://www.gnome-look.org](http://www.gnome-look.org) and drag and drop it to the Theme Manager Window (System > Preferences > Themes). If you want to theme your login window, get a GDM theme from the same link and go to System > Administration > Login Window > Install Theme

#4. Right-click the panel, select **Add to Panel**, and find the Trash can.

---

### Post by BlackBar on 2007-02-11
thanks a lot ill try these thing out

---

### Post by BlackBar on 2007-02-11
sorry about this (im new) im not sure were to start with the screen res link you gave me any help would be good because now that really the only real problem i have with ubuntu:) also when i drag themes into the theme manager it says invalid file type or something like that

---

### Post by aysiu on 2007-02-11
Link to the theme in question?

---

### Post by BlackBar on 2007-02-11
O sorry [http://www.gnome-look.org/content/show.php?content=37395]("http://www.gnome-look.org/content/show.php?content=37395")

---

### Post by dckirba on 2007-02-11
> **BlackBar said:**
>  #2 how and i make my screen resolution in wide screen formate and mush higher then what its at now , 

System>Preferences>Screen Resolution

Not sure about wide format. 

[COLOR="DarkRed"]**EDIT:**[/COLOR] Oops, Aysiu has already answered this much better :)

Cheers,
David

---

### Post by aysiu on 2007-02-11
> **BlackBar said:**
> O sorry [http://www.gnome-look.org/content/show.php?content=37395]("http://www.gnome-look.org/content/show.php?content=37395")
That's a GDM (login screen) theme, not a GTK (window decorations) theme.

To install that, you go to System > Administration > Login Window > Install Theme

---

### Post by BlackBar on 2007-02-11
ok  so as im understanding  A GDM is a log in screen not a desktop them
A GTK is a desktop them ok if thats true then that solves that problem not i still have no idea how to go about fixing my screen res problem that for the help sorry i have no idea how to use ubutu or yet and im learning as i go also how do i install a font and mouse pointer as part of theam and when i try install my video card driver i get this ERROR: nvidia-installer must be run as root? also can some one please tell me how installing programs like banshee works in ubuntu

---

### Post by Daveth on 2007-02-11
If you do need still to sort your widescreen resolution then Aysiu's link needs following. To edit the xorg.conf file, back it up, and generally change the parameters to make your widescreen work, you must open a terminal. This lives in Applications/accessories/Terminal - Applications is in the top left hand corner of your screen. You need to enter your log-in password. Find the relevant bit of Aysui's link instructions and you can cut and past the code in. This is probably a bit safer than you trying to type it in manually, as it is easy to make mistakes.
Then make sure you save the file and exit. But do read through the instructions first and see what part of the guide is relevant.

---

