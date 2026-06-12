---
title: "Very simple ?"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-04-16
Im srry 4 asking this simple of a ? but im used to windows so here it goes
I got frostwire and i just downloaded a movie and im trying to put it in a folder on my Desktop by click and dragging but it wont go in the folder. so how do i get it in the folder 
Please help the biggest noob around

---

### Post by zvacet on 2007-04-17
**copy/paste**

Let say you are in home directory and movie is in xfolder and you want move it to the yfolder on your desktop.
```
cp /home/xfolder/movie /Desktop/yfolder
```

---

### Post by hyper_ch on 2007-04-17
cp is copying, not moving...

Open the folder on your desktop, it will then open in the default file manager for your system and then you can drag and drop the file into that new window :)

---

### Post by microsoft92sucks on 2007-04-17
thats not working. Thats wat i did when i had windows but it wont work on Linux. And heres wat it says when i try to launch it from frostwire Executed command: xine/home/justin/shared/300 The movie.avi

and my defult browser is File Browser
and its frostwire 4.13.1 Beta 
I'm 90% sure im doing this right but maybe not
Please help i just wanna watch this movie:(

---

### Post by hyper_ch on 2007-04-17
Hmm, on Xfce it works copying files from Desktop into Thunar (and I also think from Desktop into Konqueror)

---

### Post by microsoft92sucks on 2007-04-18
i dont know wats up with it is there any thing i could try?

---

### Post by phossal on 2007-04-18
> **microsoft92sucks said:**
> i dont know wats up with it is there any thing i could try?

You could try not downloading movies on Frostwire. Is that properly licensed? Hmm...? Hmm...? Just kidding. You could try this at the command prompt:
```
sudo nautilus &
``` That should let you move the file around like you do in Windows. I don't think .avi files actually *play* on my Edgy by default.

---

### Post by user1397 on 2007-04-18
> **microsoft92sucks said:**
> i dont know wats up with it is there any thing i could try?maybe it won't let you move it because frostwire is running.  try quitting frostwire, and then try drag-and-dropping the movie to another folder, all within the file browser, aka nautilus.

and by the way, that movie is probably not worth watching.  300 is not out on dvd yet, so all you're gonna get is a really choppy movie bootlegged by some guy with a tiny camera.  Plus, all the lighting effects of 300 make it look probably worse.

---

### Post by user1397 on 2007-04-18
> **phossal said:**
> You could try not downloading movies on Frostwire. Is that properly licensed? Hmm...? Hmm...? Just kidding. You could try this at the command prompt:
```
sudo nautilus &
```why are you recommending that?  even though it might work for you, it is not safe practice to use **sudo **with graphical apps.  instead, use the command **gksudo**

---

### Post by BarfBag on 2007-04-18
Did you try it as root?

---

### Post by phossal on 2007-04-18
> **ubuntuman001 said:**
> why are you recommending that?

You're kidding, right? I'd like a detailed lecture on why it's not safe to use sudo with graphical apps. Please tell me all the things you've *heard.*

---

### Post by user1397 on 2007-04-18
> **phossal said:**
> You're kidding, right? I'd like a detailed lecture on why it's not safe to use sudo with graphical apps. Please tell me all the things you've *heard.*[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by microsoft92sucks on 2007-04-18
Thank u all 4 the help all i had to do was close frostwire and go to the fodler the movie was in....



                                                         DOWN WITH MICROSOFT

---

### Post by phossal on 2007-04-18
> **ubuntuman001 said:**
> [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Oh brother.

---

### Post by Tenicus on 2007-04-18
phossal please use gksudo
you do not want your computer to implode do you?

---

### Post by user1397 on 2007-04-18
> **phossal said:**
> Oh brother.I am not really getting the tone of this post.  Were you trying to be sarcsatic for some reason, even though the info on that site is very true and real, and is actually written by our most prolific writer in the forums (aysiu) ?

Or was it just a way of saying "Oh, right, I guess I was wrong and you are right."

---

