---
title: "new ati drivers makes playing video choppy"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by joshrobinson on 2006-05-08
how can i get back to the drivers ubuntu comes installed with? whats the command to redo your xserver sudo dpkg something

---

### Post by r4ik on 2006-05-09
Is,

sudo dpkg-reconfigure xserver-xorg  the line you are looking for ?

Good luck.

---

### Post by joshrobinson on 2006-05-09
[QUOTE=r4ik]Is,

sudo dpkg-reconfigure xserver-xorg  the line you are looking for ?

Good luck.[/QUOTE]

yup thats it! thanks :-D

video plays fine now :-D

---

### Post by joshrobinson on 2006-05-09
server screwup sorry

---

### Post by joshrobinson on 2006-05-09
woah major server screwup

---

### Post by r4ik on 2006-05-09
The binary drivers can be found here if you want them

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28BinaryDriverHowto%2FATI%29](https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28BinaryDriverHowto%2FATI%29)

---

### Post by joshrobinson on 2006-05-09
[QUOTE=r4ik]The binary drivers can be found here if you want them

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28BinaryDriverHowto%2FATI%29](https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28BinaryDriverHowto%2FATI%29)[/QUOTE]

yeah they are the ones i grabbed off the ati website.. maybe a newer version then that though, but the same install methods

whenever i opened mplayer it told me the drivers didnt support something and would play anyway, but fullscreen was so choppy, like 5 frames per second.. so i switched back to the old ones with the reconfigure command

---

