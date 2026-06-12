---
title: "Oh My Gui!!"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by tmofarns on 2008-04-16
so i love the gui that comes with ubuntu, compiz is really kewl but after watching this video 
[http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ) 
well how do i make my desktop do that ? how do i make my screen back up and go to the cube like that? its so freaking sweet how do i do it?

---

### Post by NightwishFan on 2008-04-16
In Terminal:
```
sudo apt-get install compizconfig-settings-manager
```
Now there is an option for advanced effects. Go to general options and set horizontal desktop size to 4 and vertical to 1. Then check the desktop cube plugin. ctrl+alt+mouse1 will rotate it. :)
There also is other plugins as well ask me if you have any questions.

---

### Post by tvtech on 2008-04-16
if you are using ubuntu version 7.04  or 7.10  check out[ compiz-fusion]("http://www.compiz-fusion.org/")

if your using earlier versions check out[ beryl]("http://www.beryl-project.org/")

---

### Post by tmofarns on 2008-04-16
> **NightwishFan said:**
> . ctrl+alt+mouse1 will rotate it. :)
There also is other plugins as well ask me if you have any questions. yeah that worked i guess i just couldnt figure out the key codes. so how do i put in the 3d images in the backround?

---

### Post by wolfen69 on 2008-04-16
first go to system>admin>restricted drivers manager. install your video driver. reboot. then open terminal and: ```
sudo apt-get install compizconfig-settings-manager
```
then go to system>preferences>appearance. then visual effects tab. enable advanced. then you can go to system>preferences>advanced visual settings? (it's right above appearance) and configure what effects you want. here is a link for keyboard shortcuts. [http://ulyssesonline.com/2007/10/25/compiz-fusion-keyboard-shortcuts/](http://ulyssesonline.com/2007/10/25/compiz-fusion-keyboard-shortcuts/)

---

### Post by NightwishFan on 2008-04-16
It is called the skydome I believe it is a pull down section of sorts in the cube plugin section.

---

