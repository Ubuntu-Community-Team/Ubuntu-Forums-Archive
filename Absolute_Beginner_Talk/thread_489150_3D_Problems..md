---
title: "3D Problems."
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2007-07-01
I have a ATI X1900 and I have updated and are using the restricted drivers. But my fglrxinfo reads:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

So how can I fix this? I take it that means I'm not using ATI drivers? Even though I'm using the restricted drivers. And I take it I'm not using 3D either?

---

### Post by swisscow on 2007-07-01
Try:

```
sudo depmod -a
```

```
sudo aticonfig --initial
```

```
 sudo aticonfig --overlay-type=Xv
```


Then REBOOT.

Worked for me!

---

### Post by solid0409 on 2007-07-01
hey 

i had the same problem with my ATI Mobility Radeon X1400

this is a web-site  follow these steps and it should fix your problem

**P .S make sure you follow it step by step, if you skip a step, then it might not work correctly.**

**in the website, i advice you to follow the second method.**

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

if anything, send me a message

---

### Post by toasty_ghosty on 2007-07-02
I tried method two but this is what I get:

theking@OptimusPrimeTheSecond:~$ sudo bash ati-driver-installer-8.38.6*.run --buildpkg Ubuntu/feisty
bash: ati-driver-installer-8.38.6*.run: No such file or directory

The file is sitting on my desktop. Any ideas?

---

### Post by solid0409 on 2007-07-03
o that problem, i got that same thing, basically what you need to do is to change the directory in which your in.  lets say if the file is in your desktop, you change the directory your in into the desktop. if is in your home folder, you change your directory to your home folder.  

you change the directory your in by typing  **cd **then the location of the file

Example:  
miguel@solid:~$ cd Desktop/
miguel@solid:~/Desktop$ 

i type** cd Desktop/ **and now i am in the Desktop and i can use any file that is in the desktop.

---

### Post by toasty_ghosty on 2007-07-04
Thanks for that tip. Now let me see if I can get this to work....

---

### Post by toasty_ghosty on 2007-07-04
Yep. Now using ATI drivers. Thank you all.

---

