---
title: "&quot;graphical login has crashed&quot; and no nice themes..."
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by arno1991 on 2007-03-29
Hello to you all,

i use Ubuntu since 5.04 Hoary Hedgehog, but now I'm running since the launch of it, 6.10.
I have two questions... The first one is, why does my loginscreen always crash? Do I something wrong? The last time, i wanted to install a new loginscreentheme and ever since it crashed, also with the standard ubuntulogin theme. Can somebody help me?
Another thing that bothers me, is that i can't install a new theme. It works, but if i want to use the theme, then can you see the window$-ish environment trough it. Can it be that in de 6.10 version no engines for themes are installed? Because all the themes that I download from the net (gnome-look) don't work, except the ones like the Human theme...

hopefully you do understand my poor english (I'm belgian) and can you help me

thanx

arno

---

### Post by ComplexNumber on 2007-03-29
> The last time, i wanted to install a new loginscreentheme and ever since it crashed,do you have a link to where you downloaded it from so i can have a look at it myself?




>  Another thing that bothers me, is that i can't install a new theme.i assume that we are talking about gtk themes here rather than GDM. ok, 2 questions:
a) what exactly do you do t install a new theme and where do you place it?
b) can you give me an example of the name of a theme that doesn't work properly?
i half suspect that you may have to update various engines.

---

### Post by arno1991 on 2007-03-29
> **ComplexNumber said:**
> 
a) what exactly do you do t install a new theme and where do you place it?

Well, because I have no internet on my Ubuntu (our modem is too old) i place all the files on my USB-stick and place it then on /home/arno1991/installatie (last word=installation)
from there I open the program "themes" that you can find in the system menu and I drag and drop my theme in the window. Then it asks me to install the new theme, i answer yes, and shortly after that the theme is in the short menu. But when you click on the theme to apply it, you get a windows-ish theme, like the first Debian pc's or Windows 95's.
But the windowborder is correct.
This is what I've tried:

[http://gnome-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548](http://gnome-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548)

(offcourse the GTK2 theme and metacity.



> **ComplexNumber said:**
> 
b) can you give me an example of the name of a theme that doesn't work properly?
i half suspect that you may have to update various engines.

here you go

[http://gnome-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548](http://gnome-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548)

(same as above)

And here you can a sample of the GDM:
[http://gnome-look.org/content/show.php/AppleUbuntu?content=38813](http://gnome-look.org/content/show.php/AppleUbuntu?content=38813)

but it also don't work with others...

thanks for the fast reply and your help


arno

---

### Post by ComplexNumber on 2007-03-29
do you have the following theme engine installed:
gtk2-engines.pixbuf

the OSX theme that you mention uses that. in fact, many themes use that engine. you need to have it installed for the theme to look right. 


i can't quite see anything about the GDM that would cause it to crash.

---

