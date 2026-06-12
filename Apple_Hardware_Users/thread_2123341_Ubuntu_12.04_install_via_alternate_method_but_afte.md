---
title: "Ubuntu 12.04 install via alternate method but after reboot i got only black screen"
date: 2013-03-07
forum: Apple Hardware Users
---

### Post by raleeha on 2013-03-07
Hi, 

i am not sure for now how to solve it. The installation of Ubuntu 12.04 went without error messages and the bootloader install via yaboot went ok (no errors were reported). But if i reboot the system the powermac G4 hangs on a black screen were no further messages displayed. i dont know exactly what goes here wrong. I suppose that the kernel was not boot. I cannot change to virtual terminal via Ctrl Alt F1. Only boot via alternate install CD and rescue mode were i can chroot into the newly installed system works. 

If anyone can point me what i can do this would be really appreciated. 

greetings raleeha

---

### Post by raleeha on 2013-03-08
I have found out following: 

```
Linux single debug nosplash break=premount
```

will boot it to initramfs built-in-shell. But what can i do there? How can i mount hard drive to change some values? There are no mount dir. 

Does anybody have same issues?

greetings raleeha

---

### Post by abtabt on 2013-03-08
identity your mac with    [http://www.everymac.com/](http://www.everymac.com/)

if you have nvidia card try this



[http://ubuntuforums.org/showthread.php?t=2090462&p=12389401#post12389401](http://ubuntuforums.org/showthread.php?t=2090462&p=12389401#post12389401)

post #1

---

