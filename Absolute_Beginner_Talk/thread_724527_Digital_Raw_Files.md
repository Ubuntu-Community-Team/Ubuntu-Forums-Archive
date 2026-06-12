---
title: "Digital Raw Files"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Terry S on 2008-03-14
Hi, 

Can anyone recommend a program to download, modify and convert Nikon D70 raw files from the camera.

When I used Windows XP  I used Adobe Photoshop CS but even Photoshop CS is not nearly enough to tempt me back to Windows XP or Vista.

I am running Ubuntu 7.10

Terry S

---

### Post by joshrobinson on 2008-03-14
i really have no experience with those files, but gimp doesnt work?
applications > graphics > gimp

---

### Post by Terry S on 2008-03-14
Hi joshrobinson

Thanks for the reply/.

No I have tried Gimp but all I get is a very small picture in the center of the window. No good at all.

Terry S

---

### Post by joshrobinson on 2008-03-14
alright, well i looked into it alittle bit to see what i could find.. lets see if we can find a fix for your problem

```
sudo apt-get install gtkam dcraw gimp-dcraw ufraw
```
now launch gtkam, im guessin this program access your camera to get the raw images off of it
launch ufraw, it allows you to open raw files, but i dont know what you can do from there

look into those applications and see what you can come up with.. i dont have a camera that uses those files, so i cant test for myself, but this should put you on the right track

---

### Post by Terry S on 2008-03-14
Excellent, thank you very much. I have to be up at 4 in the morning so I shall work on this tomorrow.

Again thanks a lot.

Terry S:)

---

### Post by joshrobinson on 2008-03-14
> **Terry S said:**
> Excellent, thank you very much. I have to be up at 4 in the morning so I shall work on this tomorrow.

Again thanks a lot.

Terry S:)

your welcome, hope you figure it all out

---

### Post by Terry S on 2008-03-15
Hi again Josh Robinson.

I input the code you supplied and hey presto it worked like a charm. I can now download, process and modify raw camera files.

Thank you very much. I for one am extremely grateful for the time and effort people like you put in to helping new users like me.

Kind Regard

Terry Sweeney
Kent in England.

---

