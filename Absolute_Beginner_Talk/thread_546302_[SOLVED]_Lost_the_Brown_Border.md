---
title: "[SOLVED] Lost the Brown Border"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by cwrann on 2007-09-08
I was removed Beryl from my computer and was messing around with Compiz trying to get the cube to work. I ended up installing Compiz fusion and messed up my graphical interface to the point that I had to go through the xconfiguration process. After getting my GI back I reinstalled Compiz. Now my computer is slower, when I try to open terminal I get a white square and I have lost the brown border which allows me to move windows with the mouse, minimize and close windows.

---

### Post by n3tfury on 2007-09-08
you lost your windows borders.  this is the best guide around and touches on just that problem:

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion##comments](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion##comments)

---

### Post by overdrank on 2007-09-08
> **cwrann said:**
> I was removed Beryl from my computer and was messing around with Compiz trying to get the cube to work. I ended up installing Compiz fusion and messed up my graphical interface to the point that I had to go through the xconfiguration process. After getting my GI back I reinstalled Compiz. Now my computer is slower, when I try to open terminal I get a white square and I have lost the brown border which allows me to move windows with the mouse, minimize and close windows.

Hi you can try to use the command 
```
metacity --replace 
```
use the keys alt,F2 and enter the command.

---

### Post by n3tfury on 2007-09-08
> **overdrank said:**
> Hi you can try to use the command 
```
metacity --replace 
```
use the keys alt,F2 and enter the command.

OP:  that command above will get you back to default, but read the link i posted have borders in compiz-fusion

---

### Post by Crafty Kisses on 2007-09-08
> **cwrann said:**
> I was removed Beryl from my computer and was messing around with Compiz trying to get the cube to work. I ended up installing Compiz fusion and messed up my graphical interface to the point that I had to go through the xconfiguration process. After getting my GI back I reinstalled Compiz. Now my computer is slower, when I try to open terminal I get a white square and I have lost the brown border which allows me to move windows with the mouse, minimize and close windows.

If you had Emerald themes installed and you removed Beryl, the borders do come down, but you can always put them back on. :)

---

### Post by n3tfury on 2007-09-08
although i get borders in compiz-fusion, i figured i'd try out emerald and the themes package.  when i enable emerald though, i lose my borders.  i've followed the guide i posted above to a T.  suggestions?

---

### Post by therunner on 2007-09-08
this forum is a lifesaver!!!

now how do I get compiz

---

### Post by therunner on 2007-09-08
ok I did everything that is listed but I still don't have a border. 

When I did metacity --replace I got the brown border back but that was it.

---

### Post by therunner on 2007-09-08
I did everything all over again and received this error msg

E: /var/cache/apt/archives/compiz-extra_0.3.6.1-0ubuntu2_i386.deb: trying to overwrite `/usr/lib/compiz/libbench.so', which is also in package compiz-fusion-plugins-extra

---

### Post by cwrann on 2007-09-09
>  you lost your windows borders. this is the best guide around and touches on just that problem:

[http://forlong.blogage.de/article/20...sion##comment](http://forlong.blogage.de/article/20...sion##comment)s

In the first paragraph in this link there is a link to an excellent how to on installing compiz-fusion. I followed it as well as the link you gave me and so far I have my brown borders and other basic functions back. I am waiting for my new nvidia glx driver to finish installing then I should have all the extras working too.

thanks a lot.

---

### Post by n3tfury on 2007-09-09
> **cwrann said:**
> s

In the first paragraph in this link there is a link to an excellent how to on installing compiz-fusion. I followed it as well as the link you gave me and so far I have my brown borders and other basic functions back. I am waiting for my new nvidia glx driver to finish installing then I should have all the extras working too.

thanks a lot.

you're welcome.

---

### Post by cwrann on 2007-09-09
I got the extras working but now I have lost my borders!!!! although the new effects are beautiful.

---

### Post by therunner on 2007-09-09
I have everything working on mine now except the cube effect. 

What do I need to do?

---

### Post by cwrann on 2007-09-09
As soon as I get the cube effect on mine I lose the borders, also it seems to be randomly reverting back to the default.

---

### Post by therunner on 2007-09-09
> **cwrann said:**
> As soon as I get the cube effect on mine I lose the borders, also it seems to be randomly reverting back to the default.

I can't figure out how to get more than one desktop to be able to go into cube.

---

### Post by cwrann on 2007-09-09
> I can't figure out how to get more than one desktop to be able to go into cube.

try going into the compiz config settings manager and under general options go to desktop size. change horizontal virtual size to 4, leave the others at 1

---

### Post by n3tfury on 2007-09-09
> **therunner said:**
> I can't figure out how to get more than one desktop to be able to go into cube.

that's in the link i provided also.  take a look.

---

### Post by therunner on 2007-09-09
GOT IT!!

Thanks!!

However, I just I realized I need a new updated and faster maChine

---

### Post by therunner on 2007-09-09
Whenever I activate the cube I can't type because it will automatically start rotating. 

I will work on this tomorrow. 

Thanks for all the help. 

-Todd

---

### Post by cwrann on 2007-09-10
After restarting my computer a magically got my borders and all the compiz fusion extras. Thanks again for the help.

---

