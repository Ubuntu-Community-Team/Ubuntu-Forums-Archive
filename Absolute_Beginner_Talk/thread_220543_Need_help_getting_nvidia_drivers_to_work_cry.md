---
title: "Need help getting nvidia drivers to work :cry:"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by cyme on 2006-07-21
i have tryed many guides and how to:s to make it work but i dont get it to work

---

### Post by trent dillman on 2006-07-21
Have you tried [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) ?

What is not working?

---

### Post by Lord Illidan on 2006-07-21
Which guides have you tried? Have you searched the wiki? What kind of card do you have anyway?

---

### Post by cyme on 2006-07-21
the is not working after i install nvidia drivers

---

### Post by Lord Illidan on 2006-07-21
> **cyme said:**
> the is not working after i install nvidia drivers
The what is not working? Can you express yourself better please?

---

### Post by Dinerty on 2006-07-21
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Thats the guide i used mate to get my nvidia drivers working

---

### Post by Jagot on 2006-07-21
If you have a newer card all you should ned to do is:

```
sudo aptitude update && sudo aptitude install nvidia-glx
```

Or with an older card:

```
sudo aptitude update && sudo aptitude install nvidia-glx-legacy
```

Then, with either of those to enable the card you will need to do this:

```
sudo nvidia-glx-config enable
```

---

### Post by cyme on 2006-07-21
okey im trying to explain notice im not good in english so,

when i try to install the drivers i cant get back in "X" becuse the x seems to be configurated wrong.

but i notice something in the [https://help.ubuntu.com/community/Bi...erHowto/Nvidia](https://help.ubuntu.com/community/Bi...erHowto/Nvidia)

that i should not install some files that i installed before and no the dont crash but i get this instead 

cyme@cyme-desktop:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
cyme@cyme-desktop:~$

---

### Post by cyme on 2006-07-21
i think i got it 2 work guys :D
but how do i check if i have it installed

---

### Post by Jagot on 2006-07-21
Type the command 'glxinfo' in Terminal.  One of the first ouputs should be a line starting 'Direct Rendering'.  If it says Yes then it's installed.

---

### Post by cyme on 2006-07-21
i dont get Direct Rendering when i type glxgears only thing i get is a new window with something moving in it :( i dont now if thats right but when i write this i dont understand

cyme@cyme-desktop:~$ glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600 GT/AGP/SSE2
OpenGL version string: 2.0.2 NVIDIA 87.62
OpenGL extensions:

---

### Post by Jagot on 2006-07-21
Sorry - meant glxinfo.

---

### Post by cyme on 2006-07-21
does this meen that its installed in the right way?

---

### Post by Jagot on 2006-07-21
Type glxinfo on it's own - without the | grep OpenGL - if it says yes to direct rendering then it's installed, if not then no.

---

