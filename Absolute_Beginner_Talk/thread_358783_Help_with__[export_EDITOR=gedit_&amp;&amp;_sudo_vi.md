---
title: "Help with  [export EDITOR=gedit &amp;&amp; sudo visudo ] for firewall"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by I SHOULD COCO on 2007-02-11
Having great fun discovering Linux !
Got samba and networking print working, but..........

I am following the the fire wall tutorial

[http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html)

and to suppress the request for sudo I am ammending the sudoer file as described below 

 [ export EDITOR=gedit && sudo visudo ] 

and upon submitting the password lets me edit sudoers.tmp and 
I then attempt to 'save as'  sudoers 

But I get the message
" You are trying to save the file on a read-only disc. Please, check that you typed the location correctly and try again. "

@@@ BUT @@@

If I merely 'save' the file and continue the tutorial is specified ( killing sudo etc)
I then get this message

"Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:15419): Gtk-WARNING **: cannot open display: "

I am stuck
I loathe posting( it seems most queries are lazy people who will not RtFm ! ) but am tired .

Thank you for any assistance

---

### Post by Rui Pais on 2007-02-11
> **I SHOULD COCO said:**
> ...
and to suppress the request for sudo I am ammending the sudoer file as described below 

 [ export EDITOR=gedit && sudo visudo ] 

and upon submitting the password lets me edit sudoers.tmp and 
I then attempt to 'save as'  sudoers 



hi, editing sudoers file have some tricky parts. 
it must be done with visudo that ensure that file will be saved in a proper format and without errors... the part of export is just to give a way to do the visudo with a GUI (gedit).
The way visudo work is save a temp copy on /tmp edit and when exit save it to correct place.

I don't know how or what you done... but seems from your post that you are trying to save manually on /etc/sudoers with save as... 

You should make your changes and simply press the save button (like saving the tmp file) not save as.

Even if it fails that way, maybe something is preventing to do it from the GUI. Try to edit then from a console with sudo visudo.

hth.

---

