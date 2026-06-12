---
title: "[SOLVED] how can i get glmatrix"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by divindavid on 2008-02-18
hello i saw on an episode of the screensavers that with a thing called glmatrix your desktop background is a moving version of the matrix code not a screensaver but as your desktop backround.


david.

---

### Post by randy78 on 2008-02-18
This might be what you're looking for :)

[http://lifehacker.com/software/linux-tip/use-a-screensaver-as-desktop-wallpaper-299410.php]("http://lifehacker.com/software/linux-tip/use-a-screensaver-as-desktop-wallpaper-299410.php")

---

### Post by divindavid on 2008-02-18
ok i have read the instructions and they make no sence can i have some help from someone who has done this

---

### Post by randy78 on 2008-02-18
> **divindavid said:**
> ok i have read the instructions and they make no sence can i have some help from someone who has done this

Check here: [http://blog.prashanthellina.com/2007/08/22/matrix-desktop/]("http://blog.prashanthellina.com/2007/08/22/matrix-desktop/")

You're going to have to get used to doing some things on your own...
Just follow the instructions and you'll be good ;)

Good Luck :D

---

### Post by divindavid on 2008-02-18
ok when attempting this i screwed up my desktop to it is just black and all of my icons are gone and i cant place any icons back on my desktop. is there a command that it makes the desktop go back to the defult so i can place my icons back. i realized that my computer is way to slow to do this.

---

### Post by randy78 on 2008-02-18
> **divindavid said:**
> ok when attempting this i screwed up my desktop to it is just black and all of my icons are gone and i cant place any icons back on my desktop. is there a command that it makes the desktop go back to the defult so i can place my icons back. i realized that my computer is way to slow to do this.

Try this in a terminal:
dpkg-reconfigure xserver-xorg

---

### Post by divindavid on 2008-02-18
when i did that i got 


david@david:~$ dpkg-reconfigure xserver-xorg
/usr/sbin/dpkg-reconfigure must be run as root
david@david:~$  


now my desktop is the same


david

---

### Post by randy78 on 2008-02-18
> **divindavid said:**
> when i did that i got 


david@david:~$ dpkg-reconfigure xserver-xorg
/usr/sbin/dpkg-reconfigure must be run as root
david@david:~$  


now my desktop is the same


david

do this in a terminal: 
sudo dpkg-reconfigure xserver-xorg

BTW, thanks for posting the output of the terminal... you'd be surprised how much it helps when we are trying to diagnose something ;)

---

### Post by divindavid on 2008-02-18
ok i did all of that and followed all of the steps and now....... nothing
do you have anyother things i should try.


yeah about the terminal output i try to put that any time it would help because a while ago i have a big wireless problem and it helped out a lot if i put the terminal output

david

---

### Post by randy78 on 2008-02-18
Copy and paste this into a terminal:
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true && nautilus

---

### Post by divindavid on 2008-02-18
thank you so much it is back to normal

---

### Post by randy78 on 2008-02-18
Cool... please mark it as solved by using the **Thread Tools** button near the top ;)

Take Care,
Randy ;)

---

