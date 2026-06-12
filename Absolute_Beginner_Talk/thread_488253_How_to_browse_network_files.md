---
title: "How to browse network files"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by n36atr0n on 2007-06-29
I'm Sorry for asking this, im still can't forget what im used to do with windows. Here is my problem

Im used Ubuntu 6.06, Gnome, Nautilus, i configuring samba so now i can see windows network shared files. 
But when i want to search any file in other computers, problem found. Examples:

My IP : 192.168.0.2
Host : ubuntu

Other IP : 192.168.0.1
Host : neo

Workgroup : matrix

Document to Share : "Picture"
subdirectory-subdirectory under "Picture" shows like this :
-Neo
---Picture
------nature
------------mountain
-----------------Himalaya
-----------------Fuji
-----------------Krakatau
------------river
------------sea
------------fruits
------------------apple
------------------orange
------------------grape

 How i can just do (like windows did) right clik to picture, choose search, type Fuji, and lets ubuntu search it for me. Can Nautilus do that or must i install other additional programs?

---

### Post by letkemanp on 2007-06-30
One or more of the scripts located here [http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/) allows you to "Search From Here" with the context menu. I just extract 'nautilus-scripts.tar.gz' to /home/{username}/.gnome2/nautilus-scripts and I'm ready to go

---

