---
title: "skydome not showing"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by InsertNameHere on 2008-02-17
I downloaded this skydome 

[http://www.compiz-themes.org/content/show.php/Carina+Nebula+Skydome?content=72349](http://www.compiz-themes.org/content/show.php/Carina+Nebula+Skydome?content=72349)

and when I directed to it, it would not show.

I also tried another one

[http://www.compiz-themes.org/content/show.php/Milky+Way+Skydome?content=55640](http://www.compiz-themes.org/content/show.php/Milky+Way+Skydome?content=55640)

and same thing, all I get is a white background.

If I put lower resolution pictures, it will work, but I want higher res pictures.

Can anyone help me please?

---

### Post by lian1238 on 2008-02-17
Have you made sure you have enabled the Png plugin under Image Loading?

---

### Post by RomeReactor on 2008-02-17
Hi. Did you save the image as a .PNG?

---

### Post by InsertNameHere on 2008-02-17
Yes PNG loading plugin is enabled, and yes the image is in PNG

---

### Post by RomeReactor on 2008-02-17
Which of the Carina nebula images did you use? I downloaded the fifth one and it worked here.

---

### Post by InsertNameHere on 2008-02-17
First and second wont work at first
Then I downloaded the 5th one and it still doesnt work

I don't think it's with the image, as all high res pictures wont work here as skydomes.

I have a intel GMA 950 gfx card if it helps.

---

### Post by RomeReactor on 2008-02-17
I'm not sure it has to do with your card. You could try the suggestion on the Carina page and resize the image in Gimp. At the moment that's all that comes to mind; sorry.

---

### Post by InsertNameHere on 2008-02-17
I will try that tonight and see how it goes

---

### Post by InsertNameHere on 2008-02-17
Scaling it down works..

40% of origional, if anyone have the same gfx card as me, 40% would probably work best.

---

### Post by icechen1 on 2008-02-17
I don't know the exact size of a skydome but you need to resize the png to the right size for your resolution in GIMP.use google to rearch the size you need.Otherwise,the skydome won't show up.

---

### Post by InsertNameHere on 2008-02-17
Nope, i think it's because my video card was crappy, I scaled it down with the exact same width/length and it works perfectly, but not in High Def...

---

### Post by Earl_Maroon on 2008-02-28
As far as I know the size of the Skydome image you can use is hardware dependent and  can't be changed. However, you can find the maximum size allowed with the command:

```
glxinfo -l | grep MAX_TEXTURE_SIZE
```

---

### Post by oedha on 2008-02-28
(try to clarify......) 	 	 	 	 	  if you can play default compiz...with high def display, leave it high definition
 

did you do this ?
 open terminal then type ccsm ( if you have installed compiz-fusion it will show the compiz setting menu )
 if you didnt install it yet......type :==> sudo apt-get install compizconfig-settings-manager
 after ccsm shows up, click on desktop cube ( you will go to the cube setting menu )
 choose appearance tab
 scroll down.......click on skydome
 have you mark on skydome and change the skydome picture ?
 to play it :==> ctrl+alt+mouse drag

---

