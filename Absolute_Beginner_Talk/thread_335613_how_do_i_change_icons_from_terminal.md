---
title: "how do i change icons from terminal"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by joey_joe_joe on 2007-01-10
is it possible to change the icon of a folder/file from the terminal. I know you can do it by right clicking on the file and going to 'properties' but i need to do it in a shell script.
there is surely a way to do it, but google has turned up nothing. 
thanks.

---

### Post by ComplexNumber on 2007-01-10
> **joey_joe_joe said:**
> is it possible to change the icon of a folder/file from the terminal. I know you can do it by right clicking on the file and going to 'properties' but i need to do it in a shell script.
there is surely a way to do it, but google has turned up nothing. 
thanks.
i'm not entirely certain, but i think you may have to change the relavant  files here:
/usr/share/app-install/desktop

the /usr/share/app-install seems to be some sort of repository for linking up each install application with its icon and mime type etc (amongst other things)

---

### Post by joey_joe_joe on 2007-01-10
i am not trying to change the default icon associated with a specific file type, but rather the icon for one file/directory only. say for example to change your music folder icon to a cd icon....
anyone...?

---

### Post by echo $USER on 2007-01-10
> **joey_joe_joe said:**
> i am not trying to change the default icon associated with a specific file type, but rather the icon for one file/directory only. say for example to change your music folder icon to a cd icon....
anyone...?

why don' you just use the gui?

---

### Post by joey_joe_joe on 2007-01-10
cause i need to do it from a script....

---

### Post by mohamad on 2007-02-17
I'm looking for such a command to, I also want to use it in a script and scanned google for 2 hours with nog result, I only found this what I think only works with KDE since it didnt work for me in gnome:
[http://www.kde-forum.org/artikel/14478/konqueror-folder-icons.html](http://www.kde-forum.org/artikel/14478/konqueror-folder-icons.html)

where the command would be something like: 
**echo -e "[Desktop Entry]\n\tIcon=$PWD/folder.png" > .directory**

I hope someone has a working solution,
greetz

---

### Post by xopher on 2007-04-17
Let's bump this one. I need this too.

Just out of interest, you're mounting cd/dvd-images with fuseiso?

*CRY FOR HELP*

---

