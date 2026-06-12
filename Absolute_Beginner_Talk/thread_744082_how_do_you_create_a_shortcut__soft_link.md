---
title: "how do you create a shortcut / soft link?"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Malignity on 2008-04-03
I'm embarrassed to even ask this question - because it seems so simple yet I can't figure it out or find any reference to it in Ubuntu's help.

I'm using 7.10 desktop and basically want to create a shortcut to a folder on the desktop.  I browsed for it and dragged it out but later found that just makes a copy.

I guess this may also be called a soft link or hard link in other linux OS's?

So can it be done and if so how?

Thanks!

---

### Post by Tristam Green on 2008-04-03
right-click on desktop:

Create Launcher

Type: "Location"
Name: <insert name here>
Location: /folder/subfolder/subfolder
Comment: <insert comment>

Best of luck ^^

---

### Post by anaconda on 2008-04-03
or with terminal

cd Desktop
ln -s /folder/you/want/the/link/to/point nameOfTheLink

---

### Post by vanadium on 2008-04-03
A launcher and a link are different things. A launcher is gnome specific and most resembles the Windows "shortcuts". A symbolic link is much more powerfull because it behaves very much like the object (file or directory) to which it refers. anaconda told how to creat a symbolic link from the command line. In nautilus, right-click and choose "make link", then move the link to where you want it. You can also create a link after dragging an object with the two mouse buttons pressed (or the middel mouse button if you have a three mouse button) and choosing "make link".

---

### Post by Malignity on 2008-04-03
Who'd a guess both mouse buttons!? LOL Thanks I knew it would be easy.

---

### Post by vanadium on 2008-04-03
If you have a three button mouse or one with a scroll wheel, that will also do.

---

### Post by ddvanrooy on 2008-06-13
Hi
to chip in on this question: I use Gnome and 8.04. I had the same question as in the first one, except, when I try to make the link in Nuatilus, I get an error message: There was an error creating the symlink in /media/FILES. (Files being the folder I want to make the link to) Any ideas ??

Thx
D

---

