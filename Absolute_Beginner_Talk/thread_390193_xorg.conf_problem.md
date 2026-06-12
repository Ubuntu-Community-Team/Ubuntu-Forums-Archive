---
title: "xorg.conf problem"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Vandorius on 2007-03-21
Hey,

i ve made a mistake trying to make the ATI drivers work.Now GUI doesnt want to start sayin that its someting wrong with xorg.conf.What i did wrong is: I just pasted something in /etc/X11/xorg.conf file, just last two lines and restarted. Now how can i erase that two lines from here to get my GUI back.

Thanks a lot.

---

### Post by arochester on 2007-03-21
Try > sudo vim /etc/X11/xorg.conf 

---

### Post by doobit on 2007-03-21
> **Vandorius said:**
> Hey,

i ve made a mistake trying to make the ATI drivers work.Now GUI doesnt want to start sayin that its someting wrong with xorg.conf.What i did wrong is: I just pasted something in /etc/X11/xorg.conf file, just last two lines and restarted. Now how can i erase that two lines from here to get my GUI back.

Thanks a lot.

from the command line you can use gedit or nano to edit /etc/X11/xorg.conf 
```
sudo nano /etc/X11/xorg.conf
```
or use Ubuntu's guided xorg editing interface
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Vandorius on 2007-03-21
ok cool i can edit it and erase but how can i get out now and what is the reboot command? Sry im such a noob  :P

---

### Post by bulldog on 2007-03-21
Use CTRL-x to leave the nano session,don't forget to save your file!!

sudo reboot will reboot the computer.

---

### Post by Vandorius on 2007-03-21
Ok in nano i can tsee anithing opening the file. But if i go sudo vim /etc/X11/xorg.conf i can erase that lines but i dont know how to exit the screen ang go on from there to rebooting. Culd be anyone soo good and guide me to save this file and restart please.

---

### Post by Vandorius on 2007-03-21
Its ok i ll just reinstall it i messed it this time. But thanks anyway guys.

---

### Post by arochester on 2007-03-21
From vim "write the file and exit" => :wq

vim commands cheat sheet at [http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html)

---

### Post by metalkr on 2007-03-21
you could verify your xorg file and check if you need write a sentence of declaration  about the changes than you wrote before (you see the top of your file and check another examples). Excuse me my english \m/

---

