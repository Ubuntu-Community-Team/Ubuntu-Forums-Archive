---
title: "xcursor help"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by zmuth734 on 2007-01-04
I'm looking to change my cursor theme but I don't see a System/Preferences/Cursor Selection.

Here's my synaptic:
[IMG]http://img501.imageshack.us/img501/1686/snapshot1gw6.png[/IMG]

Thanks

---

### Post by MkfIbK7a on 2007-01-04
system>preferences>mouse 
choose pointer  tab

---

### Post by zmuth734 on 2007-01-04
thanks, but how do I install cursor themes from gnome-look.org

---

### Post by MkfIbK7a on 2007-01-04
srry dont know if you find out plz post it here

P.S. to zmuth check that other post you had where you figured out the answer yourself

---

### Post by zmuth734 on 2007-01-04
> **wert613 said:**
> srry dont know if you find out plz post it here

you have to add the downloaded cursor folders to the .icons folder in your home folder then you can pick which you want under mouse properties>pointers

by the way here is the cursor theme I installed: [http://www.gnome-look.org/content/show.php?content=27913](http://www.gnome-look.org/content/show.php?content=27913)

---

### Post by MkfIbK7a on 2007-01-04
did that work for you?

---

### Post by zmuth734 on 2007-01-04
> **wert613 said:**
> did that work for you?

yep it works

---

### Post by MkfIbK7a on 2007-01-04
it doesnt seem to work for me:confused:

---

### Post by MkfIbK7a on 2007-01-04
can you make a screen shot plz?

---

### Post by longxj on 2007-01-10
here is a method you can try.

first copy the theme in .icons directory.
the .icons directory may locate at:
/home/longxj/.icons
or 
/usr/share/.icons
depends on your system

make a file named .Xdefaults in your home directory, the content are:
Xcursor.theme: Gold(the name of the cursor theme)
Xcursor.size: 24(the size of the cursor)

---

