---
title: "[SOLVED] basic editing question: fade"
date: 2008-04-09
forum: Art &amp; Design
---

### Post by alphaniner on 2008-04-09
My image editing expertise involves too many hours with MS paint and a bit of playing around with GIMP.  I have [what I hope is] a fairly simple image editing question, and it goes like this:

I have a black square centered on a white backround, something like this:  [IMG]http://i145.photobucket.com/albums/r208/AshFooYoung/alone2e.jpg[/IMG]
(the blue border is just for reference, it is not part of my intended image)

What I want to do is 'fade' the black to white so that it would kind of blend in to a larger white background (the idea is to use the image on white t-shirt).  Does anyone know how to do this with GIMP, or any other (free) Linux software for that matter?  If not, could someone please point me to some forums or tutorials where I might get further information?  Thanks.

a9

---

### Post by Lux Perpetua on 2008-04-09
One way in GIMP is to use s blur filter. For example, Filters->Blur->Gaussian Blur. Raise the blur radius slowly to see what it does.

---

### Post by st0n3cutt3r on 2008-04-09
an alternative option is to select the black using the wand tool in gimp, and then use in the image window Select < Feather..., and tell it how many pixels you want the fade to be. After feathering, select inverse (Ctrl+I), get yourself a big brush tool, and then paint over the border between the black and the white.  you should cover the entire border in a single stroke (move your mouse around the border and make sure you get it all). continue using the brush tool making a complete pass every time until it is how you want it.  because gimp is a little weird, it took 5 brush strokes for me using this method to get the fade completely smooth. YMMV

Attached are before and after pictures using this method, and a 20px feather.


(playing around with the feather settings will get you different results.  There are a few better methods for doing this, but i'm not familiar enough with the gimp to try to explain them)

---

### Post by alphaniner on 2008-04-09
Thanks to both of you, I'll give this stuff a try.

---

### Post by natehall on 2008-04-09
Were you thinking of something like this?( It's great as a mask by the way, to fade one image into another That's why I made it with the mathmap plug in.)

---

### Post by alphaniner on 2008-04-09
I tried the feather method, but I didn't really get the part about using the brush tool.  Plus it seemed like it would require, ya know... skill.  I did some cutting, pasting, and inverting but it didn't look right.  I ended up using a combination of filters (Blur -> Gaussian Blur and Noise -> Pick) which turned out pretty good.  Thanks again for all the tips.

---

### Post by st0n3cutt3r on 2008-04-10
lol.  nice work.

---

