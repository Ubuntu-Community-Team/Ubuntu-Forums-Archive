---
title: "Error in updates"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by shawn fernandes on 2006-11-10
When I click on the software updates I get this message
(A error occured, please run Package Manger from the right-click menu or apt-get on terminal to see what is wrong. The error message was:'Error:Opening the cache<E:Type'dep' is not known on line 33 in source list /etc/apt/sources.list,E:The list of sources could not be read.>') 
 and I also can't use the Synaptic Package Manager.

Please Help Me.

---

### Post by Sef on 2006-11-10
> The error message was:'Error:Opening the cache<E:Type'dep' is not known on line 33 in source list /etc/apt/sources.list,E:The list of sources could not be read.>')

Open the terminal (Applications > Accessories > Terminal)

and type this:

sudo gedit /etc/apt/sources.list

Next copy and paste your sources list here.

---

### Post by shawn fernandes on 2006-11-10
I did as you said and I got this message from the terminal-
(gedit:10921): Gdk-WARNING **: locale not supported by Xlib

(gedit:10921): Gdk-WARNING **: cannot set locale modifiers

What do I do now?

---

### Post by shawn fernandes on 2006-11-10
I did as you said and I got this message from the terminal-
(gedit:10921): Gdk-WARNING **: locale not supported by Xlib

(gedit:10921): Gdk-WARNING **: cannot set locale modifiers

What do I do now?
Edit/Delete Message

---

