---
title: "This is headache!!!"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by Koech on 2006-05-22
I have really tried to install RaLink drivers on my box, I depend on it for my internet, I have installed build-essential, gcc, and many more plus compiling my kernel, which I doubt works, it's Dapper 6.06, I can't see the image so I can't install. Now I cant go past 'make all' in making my drivers, I get:

[FONT="Courier New"]questa@Questa:~$ cd ./RT61_Linux_STA_Drv1.0.4.0/Module
questa@Questa:~/RT61_Linux_STA_Drv1.0.4.0/Module$ make all make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/questa/RT61_Linux_STA_Drv1.0.4.0/Module modules
make[1]: Entering directory `/lib/modules/2.6.15-23-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-23-386/build'
make: *** [all] Error 2
questa@Questa:~/RT61_Linux_STA_Drv1.0.4.0/Module$[/FONT]

What else do i need to do? I am not sure I compiled my kernel well...

PS: I may not reply for a while so bear with me.

---

### Post by Sef on 2006-05-22
> plus compiling my kernel, which I doubt works

If your kernel doesn't work, I would suggest a clean install, i.e. using a disc to reinstall Ubuntu.

---

### Post by Koech on 2006-05-22
I meant the recompiling seems to have been a total waste of time since I got no image.

---

