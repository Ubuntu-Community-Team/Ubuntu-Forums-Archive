---
title: "Help with Console font"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by ludzter on 2005-11-22
Hi There

I am trying to change my console font, i found this one that i like:
[http://www.gnome-look.org/content/show.php?content=19621]("http://www.gnome-look.org/content/show.php?content=19621") 

But i dont know how to install it, did search for a thread about installing font´s but didn´t find anything of use.

So can you Guys and Girls help a newbie out? ;) 

/Ludzter

---

### Post by Irtimid2001 on 2005-11-22
well, if you go to your profile in the console => general => use the terminal font of the system (uncheck) and choose the font you want :)

edit: srr, i didn't saw you didn't know how to install the font, i'll check it out for you
edit2: go to system => preferences => fonts => details => go to font folder (below)
this opens a map, try to copy the font into this map and set the right restrictions. This will probably work, haven't tried it. (srr if the paths aren't exacltly correct, i've translated them into english)

---

### Post by ludzter on 2005-11-22
Thnx.. i am at work now, but will give it a try later tonight.. again thnx:D

---

### Post by endersshadow on 2005-11-22
Whoops, gave bad advice...working on getting it working...I'll let you know how to do it when I figure it out :)

---

### Post by ludzter on 2005-11-23
Hmm.. some got a clue how to do this? :)

---

### Post by kperkins on 2005-11-23
download the file
open up a terminal cd to where you downloaded it
tar xvfz <file name>.tar.gz (extracts the file) conversely you can open it with the package manager in nautilus, and just extract the .ttf to you home folder for now.
in the terminal do the following: sudo mv <file name>.ttf /usr/local/share/fonts/
you could, also just "cp" it to the folder.
Or you can extract the .ttf file to ~/.fonts folder, if you don't need it to be a system-wide font.

---

### Post by ludzter on 2005-11-24
> in the terminal do the following: sudo mv <file name>.ttf /usr/local/share/fonts/
you could, also just "cp" it to the folder.
Or you can extract the .ttf file to ~/.fonts folder, if you don't need it to be a system-wide font.

I did as you said but it didn´t quite work for me, i dont know if it´s matters but it´s a .psfu file instead of .ttf

Do i need to activate it in some way?

---

