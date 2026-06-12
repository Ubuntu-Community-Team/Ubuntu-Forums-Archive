---
title: "y500 webcam"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by sameer.india on 2008-03-29
i have lenovo y500 77614eq laptop. how do i make the webcam work on gutsy

---

### Post by linuxwizard on 2008-03-29
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.
To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If cam does not work post the results of the command > lsusb

---

### Post by sameer.india on 2008-04-04
yeah it worked but how do i use it to record video or take pictures

---

### Post by spydon on 2008-04-04
Install a program called cheese. With the terminal you can do: 
```
sudo apt-get install cheese
```
or just find it in Add/Remove.

Cheese can record video and take pictures, it also has some cool effects you can add on your pictures and videos. :)

---

### Post by sameer.india on 2008-04-09
Thanks i'll try it out

---

### Post by spydon on 2008-04-10
Yeah do that. If you think it works, you can mark this thread as solved.

---

