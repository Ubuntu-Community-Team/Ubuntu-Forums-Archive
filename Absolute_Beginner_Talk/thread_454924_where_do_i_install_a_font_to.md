---
title: "where do i install a font to?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by thesonisshining on 2007-05-26
i was wondering, where would i install a font to? also do any applications accept .ttf fonts?:(

---

### Post by Ek0nomik on 2007-05-26
Put them in your home folder, and the .fonts folder.

~/.fonts

You can install msttcorefonts and the core Microsoft fonts will be installed.  You can install any thing into .fonts though.

```
sudo aptitude install msttcorefonts
```

---

### Post by thesonisshining on 2007-05-26
thank you but how do i get to that folder?

---

### Post by Ek0nomik on 2007-05-26
Do you want to do it via GUI or Terminal?

GUI:

```
gksudo nautilus
```

Navigate to your home directory, and create a folder called .fonts (yes, use the DOT)

Terminal:

```
cd ~/
mkdir .fonts
mv ~/Desktop/my.font.here.ttf ~/.fonts
```

If you have more questions please ask.  :)

---

### Post by thesonisshining on 2007-05-26
it says no such file or directory......

---

### Post by Ek0nomik on 2007-05-26
You should post your Terminal output (good to start doing if you are going to ask for help)

You need to make the directory, that's probably why it's saying it doesn't exist.

Post me something exact and we can get somewhere.  :)

---

### Post by jwelsh405 on 2007-05-26
type in terminal
sudo pico ~/yourhomefolder/.fonts
 example
mine would be
sudo pico ~/jeff/.fonts

when it is brought up in the text editor hit control x and save it
if you are using gnome you can open a folder an click on the go menu and click location
from there just type *example*/home/jeff/.fonts and it will open the folder to where you can just copy and paste your fonts

---

### Post by thesonisshining on 2007-05-26
alright i went into my home folder and it wouldn't allow me to create a folder; so i tried the terminal and i got 

"chris@christopher-desktop:~$ cd ~/
chris@christopher-desktop:~$ mkdir .fonts
mkdir: cannot create directory `.fonts': File exists
chris@christopher-desktop:~$ mv ~/Desktop/danub__.ttf ~/.fonts
mv: cannot stat `/home/christopher/Desktop/danub__.ttf': No such file or directory
chris@christopher-desktop:~$ 


"

---

### Post by jwelsh405 on 2007-05-26
in a terminal cd to your home directory and then type this
mkdir .fonts

---

### Post by jwelsh405 on 2007-05-26
> **thesonisshining said:**
> alright i went into my home folder and it wouldn't allow me to create a folder; so i tried the terminal and i got 

"chris@christopher-desktop:~$ cd ~/
chris@christopher-desktop:~$ mkdir .fonts
mkdir: cannot create directory `.fonts': File exists
chris@christopher-desktop:~$ mv ~/Desktop/danub__.ttf ~/.fonts
mv: cannot stat `/home/christopher/Desktop/danub__.ttf': No such file or directory
chris@christopher-desktop:~$ 


"

are you using gnome

---

### Post by BoyOfDestiny on 2007-05-26
Hi, ok other posters, you don't need sudo or gksudo for this.

In nautilus, you go 
View -> Hidden Files
Or press ctrl + H

the folder you want is .fonts

If it doesn't exist, just right click and Create Folder
the "." makes it hidden

Just drop in whatever .ttf files you want. It will show up in the Font Config and apps.

---

### Post by DARKGuy on 2007-05-26
Are you sure you're typing the font name correctly? extensions also count, it might be danub__.ttf as it also might be danub__.TTF <- Linux is case-sensitive :P

---

### Post by thesonisshining on 2007-05-26
> **jwelsh405 said:**
> are you using gnome

i've been using ubuntu for about a week i have no idea. i wish i could answer that. is there a way to find out?

---

### Post by thesonisshining on 2007-05-26
> **BoyOfDestiny said:**
> Hi, ok other posters, you don't need sudo or gksudo for this.

In nautilus, you go 
View -> Hidden Files
Or press ctrl + H

the folder you want is .fonts

If it doesn't exist, just right click and Create Folder
the "." makes it hidden

Just drop in whatever .ttf files you want. It will show up in the Font Config and apps.

alright i did that now will they show up in gimp and abiword?

---

### Post by Ek0nomik on 2007-05-26
> **thesonisshining said:**
> alright i went into my home folder and it wouldn't allow me to create a folder; so i tried the terminal and i got 

"chris@christopher-desktop:~$ cd ~/
chris@christopher-desktop:~$ mkdir .fonts
mkdir: cannot create directory `.fonts': File exists
chris@christopher-desktop:~$ mv ~/Desktop/danub__.ttf ~/.fonts
mv: cannot stat `/home/christopher/Desktop/danub__.ttf': No such file or directory
chris@christopher-desktop:~$ 


"

Did you create a .fonts **file**?

jwelsh405:  What you told him to do was to create a .fonts **file**, not **folder.**

thesonisshining:  Follow these steps (copy and paste if you want)

Open a NEW Terminal or cd ~/  (~/ is the same as /home/YOURuserNAME)

```
rm .fonts
mkdir .fonts
```

If it says you don't have *permissions* to create the directory, use "sudo mkdir .fonts" instead.

Now, just to make it easy for now:

```
nautilus
```

Go to your Desktop, find your font, and cut it, than go to your home folder, show hidden files, and go inside your .fonts folder.  Paste your font in.

You can do what I told you to do before (using the mv command to move files, but I imagine you are more comfortable with the GUI for now)

---

### Post by BoyOfDestiny on 2007-05-26
> **thesonisshining said:**
> i've been using ubuntu for about a week i have no idea. i wish i could answer that. is there a way to find out?

If you are using Ubuntu, GNOME is the default. 

If you have an Applications, Places, System menu at the top. That's Gnome :). Click System, there is an about Ubuntu section and about Gnome.

---

### Post by Ek0nomik on 2007-05-26
> **BoyOfDestiny said:**
> Hi, ok other posters, you don't need sudo or gksudo for this.

In nautilus, you go 
View -> Hidden Files
Or press ctrl + H

the folder you want is .fonts

If it doesn't exist, just right click and Create Folder
the "." makes it hidden

Just drop in whatever .ttf files you want. It will show up in the Font Config and apps.

That's exactly what I told him to do earlier.  You're right though, you don't need gksudo, but it doesn't matter what the permissions on the .fonts folder are anyway.

---

### Post by BoyOfDestiny on 2007-05-26
> **thesonisshining said:**
> alright i did that now will they show up in gimp and abiword?

I double checked, my fonts do show up in GIMP (don't have abiword at the moment)

I don't recall if a reboot or logout was required.

---

### Post by thesonisshining on 2007-05-26
> **Ek0nomik said:**
> Did you create a .fonts **file**?

jwelsh405:  What you told him to do was to create a .fonts **file**, not **folder.**

thesonisshining:  Follow these steps (copy and paste if you want)

Open a NEW Terminal or cd ~/  (~/ is the same as /home/YOURuserNAME)

```
rm .fonts
mkdir .fonts
```

If it says you don't have *permissions* to create the directory, use "sudo mkdir .fonts" instead.

Now, just to make it easy for now:

```
nautilus
```

Go to your Desktop, find your font, and cut it, than go to your home folder, show hidden files, and go inside your .fonts folder.  Paste your font in.

You can do what I told you to do before (using the mv command to move files, but I imagine you are more comfortable with the GUI for now)

the folder was already created but i couldn't see it. i didn't realize it was hidden.

---

### Post by BoyOfDestiny on 2007-05-26
> **Ek0nomik said:**
> That's exactly what I told him to do earlier.  You're right though, you don't need gksudo, but it doesn't matter what the permissions on the .fonts folder are anyway.

True, sorry about the repetition. I just like to avoid using root type privileges unless really necessary.

---

### Post by Ek0nomik on 2007-05-26
So, you are good to go now thesonisshining?

---

### Post by Ek0nomik on 2007-05-26
> **BoyOfDestiny said:**
> True, sorry about the repetition. I just like to avoid using root type privileges unless really necessary.

No, you are correct, it is wise, and is good practice to avoid it when you can.  I try to use the Terminal most of the time, but sometimes I fire up nautilus and generally I need root privileges so I am so used to typing that.  ;)

---

### Post by thesonisshining on 2007-05-26
thank you for all your help. i really do appreciate it. it is working now. thank you for all your patience.

---

### Post by jwelsh405 on 2007-05-26
Did you create a .fonts file?

jwelsh405: What you told him to do was to create a .fonts file, not folder.

My bad i did didnt i gosh

---

### Post by Ek0nomik on 2007-05-26
> **jwelsh405 said:**
> Did you create a .fonts file?

jwelsh405: What you told him to do was to create a .fonts file, not folder.

My bad i did didnt i gosh

No worries, just remember when you use nano, you're creating a file, not a folder.  :)

> **thesonisshining said:**
> thank you for all your help. i really do appreciate it. it is working now. thank you for all your patience.

Glad you got it working.

---

### Post by BoyOfDestiny on 2007-05-26
> **Ek0nomik said:**
> No, you are correct, it is wise, and is good practice to avoid it when you can.  I try to use the Terminal most of the time, but sometimes I fire up nautilus and generally I need root privileges so I am so used to typing that.  ;)

All good. I'm a fan of the terminal myself, one thing I'll mention if you gksudo over ssh -X, Under System -> Accessiblity -> Assitive Technology Preferences, you can set password boxes
as floating windows. No drawing or darkening of the bg, etc. It was lagging and generally bothersome otherwise. Not sure if you knew about it, but it makes things nicer I think.

> **thesonisshining said:**
> thank you for all your help. i really do appreciate it. it is working now. thank you for all your patience.

:)

---

### Post by Ek0nomik on 2007-05-26
> **BoyOfDestiny said:**
> All good. I'm a fan of the terminal myself, one thing I'll mention if you gksudo over ssh -X, Under System -> Accessiblity -> Assitive Technology Preferences, you can set password boxes
as floating windows. No drawing or darkening of the bg, etc. It was lagging and generally bothersome otherwise. Not sure if you knew about it, but it makes things nicer I think.



:)

I didn't know that.  Thanks.  :)

---

### Post by dptxp on 2007-05-26
It is simple to add fonts in KDE. There is ADD FONTS or something similar in it.

I installed kde-core, much smaller than kubuntu-desktop, and added fonts from Windows/Fonts in a minute.

I have retained my kde-core. I normally do not use it, but it can be useful at times.

---

