---
title: "Gnome downloaded but no show on desktop"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by dominic mckeever on 2006-05-23
I think this is a simple one. 

i have downloaded and installed gnome using synaptic manager and have rebooted but still have same desktop options - i assumed it would automatically become the default. how do i make it my default desktop manager?

---

### Post by skippy81 on 2006-05-23
You could just download the "ubuntu-desktop" package which will include everything to use gnome.  What GUI are you currently using? You should have a desktop manager (GDM) which lets you choose between desktops.

---

### Post by hotbrainz on 2006-05-23
I am not sure of this , but do try it:

 apt-cache search gnome

This should show you all the gnome pakages which are present.

Then you just choose the package you want and type:

apt-get install [package]


Hope this helps..

---

### Post by dominic mckeever on 2006-05-23
I'm going to seem pretty stupid I think. GUI is graphical user interface i presume but not sure how to establish which one i am using.

---

### Post by hotbrainz on 2006-05-23
Hey Dominic, Nobody is stupid if you have decided to learn...

The desktop or the graphical interface you see on the screen is by default gnome on Ubuntu. But if you got something like "kubuntu" then the GUI would be KDE. 

Hope this helps..

---

### Post by dominic mckeever on 2006-05-23
Thanks for your kind response- seems Gnome is present after all as my desktop manager. 

i became confused when i consulted a gnome manual to find out how to change my desktop appearance. it suggested i choose applications/ desktop preferences. however when i click on applications i don't get that option. 
i therefore thought i had some alternative to gnome. is there a different route to 'desktop preferences' on some versions of gnome?

---

### Post by hotbrainz on 2006-05-23
you could just click on "system" which is in the same panel on the top and you will find your preferences :)

IF you are a person who likes to make the system look good like me(eye candy). Then you could do:

apt-get install kde-desktop

This is another Gui and looks quite good too.

---

