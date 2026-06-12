---
title: "howto set default icon for a file type"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-02-07
Hi
I have search for howto set a default icon for a specific file, but no result. For example, 

I know the following easy way to change the icon of a specific file:
right click, choose properties, then click on the icon next to "Name" property, and you can replace any .png or other icon file you like.

However the problem is: 
it only change that specific file, if I want to make all .pdf files with that icon, how do I do that? In windows there is "apply all", but there is no such option. You cannot change every .pdf file with icons so there should be an easy way to change icons of every file in that specific family (e.g. all .pdf files)

thank you
findik1

---

### Post by shareMenaPeace on 2007-02-08
Maybe if you know the name of the *png you could overwrite it inside the theme icon set.
The path can be found if you locate filename.png 
But i dont know how to get the filename :)

---

### Post by dimeotane on 2007-02-18
BUMP:

I'd like to know how to set the icon for all my tar.lzo backup files to have the file roller 'archive' icon

---

### Post by findik1 on 2007-02-19
dimeotane: same problem. searched google but could not find a sol. yet

---

### Post by kariopto on 2007-02-19
I was also looking for a long time,
Overwriting the *.png might help when you already have an icon associated with the file type.
This was not my case.
I just found this:
[http://ubuntuforums.org/showthread.php?t=150393](http://ubuntuforums.org/showthread.php?t=150393)
I followed it and it works!
HTH

---

### Post by dimeotane on 2007-03-10
I found an easy way to make custom icons for files.
I wanted a nice icon for files compressed with .lzo, which otherwise would have the blank paper icon.  

Here's what you do: 

find or make a folder in your /home/user directory called .icons 

in the hidden .icons folder in your user directory find or make

the folder for the icon theme you're using, for me its "Human"

then a 48x48 folder inside  (I suppose you need to do the other sizes as well if you want it to appear properly in the file manager)

and a mimetypes folder inside that

put your icon inside that folder, name it according to this format

gnome-mime-application-yourapplicationname.png

it worked, and it was pretty easy!

---

### Post by kxs on 2007-05-22
> **dimeotane said:**
> find or make a folder in your /home/user directory called .icons 

in the hidden .icons folder in your user directory find or make

the folder for the icon theme you're using, for me its "Human"

then a 48x48 folder inside  (I suppose you need to do the other sizes as well if you want it to appear properly in the file manager)

and a mimetypes folder inside that

put your icon inside that folder, name it according to this format

gnome-mime-application-yourapplicationname.png

Hi, thanks for that tip. But it seems that it`s much easier. You just have to copy icon (named as you mentioned) to your local .icons folder. Theme name folders and etc. aren`t needed. The icons will work then no matter what theme you`ve chosen

---

