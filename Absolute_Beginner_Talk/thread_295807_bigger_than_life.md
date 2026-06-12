---
title: "bigger than life"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Linux&amp;Lizards on 2006-11-08
hey guys while trying to save a word document to a floppy all my icons and stuff grew huge!
when i try to change my resolution it wont let me!
i would reinstall ubuntu but then ill have to spend days putting all the stuff back on please help!!!!!!!!!!!!!!!!!!!!!! :)

---

### Post by Blutack on 2006-11-08
Thats a new one to me.  Have you tried logging back in and then out to restart the X-server (the thing that handles all that stuff), or pressing cntrl-alt-backspace.  If that doesn't help give us a shout.

---

### Post by GStubbs43 on 2006-11-08
Are just the icons huge, or everything? Try ctrl+alt+backspace and see if that fixes it. If it is just icons,right click them and say stretch icon, then you can resize them. :)

---

### Post by Linux&amp;Lizards on 2006-11-08
i tried the key comand and it didnt help.
How would i acess theis x server you speak of?

---

### Post by Linux&amp;Lizards on 2006-11-08
and by the way everything is huge really huge!

---

### Post by Linux&amp;Lizards on 2006-11-08
and ive tried restarting my computer many times but to no avail!!!!!!!

---

### Post by MWAAAHAAA on 2006-11-08
Can you post a screenshot?

---

### Post by Blutack on 2006-11-08
Have you turned on some accesibility thing?  Otherwise open up a terminal and type
sudo dpkg-reconfigure xserver-xorg
I don't understand most of the options either but take the defaults, when you get to the resolution bit make sure you choose whatever the native is for your screen.  It should autodetect the right one anyway.
Then cntrl-alt-backspace

---

### Post by Linux&amp;Lizards on 2006-11-08
here yo go

---

### Post by Linux&amp;Lizards on 2006-11-08
sry cant claims its a php file and then it opne upp with a tex editor

---

### Post by Blutack on 2006-11-08
Pop it in a tarball (right click and compress as tar.gz).  Should post then.

---

### Post by Linux&amp;Lizards on 2006-11-08
I dont know what kinda drivers i got

---

### Post by Linux&amp;Lizards on 2006-11-08
if it helps at all i got a dell 4100 and we threw a dvd burner in their too

---

### Post by Blutack on 2006-11-08
Pardon?  Is this something to do with the xserver-xorg reconfigure thing?  It should pick the driver for you, there is a list and one should already be selected (in red).

---

### Post by Linux&amp;Lizards on 2006-11-10
hey dudez!
I installed pclinuxos temporarily im not sure what happened there.

---

