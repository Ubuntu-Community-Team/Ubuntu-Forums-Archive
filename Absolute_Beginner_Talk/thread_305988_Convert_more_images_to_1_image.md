---
title: "Convert more images to 1 image ?"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by ToNneTje on 2006-11-24
Hi all,

I'm using Ubuntu for about 2 weeks now, and I like it.

On my XP comp I was using a program called PicJoiner.
With this program I converted more movie snapshots to 
1 big image in JPG format with all snapshots in it.

(When I make 20 snapshots of a movie scene, I wanna
convert all this snapshots to one big image, seems
a little like a comic book)

Does anyone know a Linux (Ubuntu) program that does the 
same ?

Thanks.

---

### Post by bodhi.zazen on 2006-11-24
> **ToNneTje said:**
> Hi all,

I'm using Ubuntu for about 2 weeks now, and I like it.

On my XP comp I was using a program called PicJoiner.
With this program I converted more movie snapshots to 
1 big image in JPG format with all snapshots in it.

(When I make 20 snapshots of a movie scene, I wanna
convert all this snapshots to one big image, seems
a little like a comic book)

Does anyone know a Linux (Ubuntu) program that does the 
same ?

Thanks.

gimp will do it

There are several online tutorials, try [this](http://www.gimp.org/tutorials/)

---

### Post by ToNneTje on 2006-11-24
Thanks bodhi.zazen, I will try Gimp :)

---

### Post by ToNneTje on 2006-11-24
It seems Gimp can't do this... any other suggestion ?

Thanks.

---

### Post by drphilngood on 2006-11-24
Have you tried [Pandora]("http://www.shallowsky.com/software/pandora/")?

> Pandora is a GIMP plug-in which helps in stitching together multiple images to make a panorama.

---

### Post by ToNneTje on 2006-11-24
Pandora looks okay, but the images are horizontal.
Is it possible to make it vertical to ?

Example:
When I have 20 images, and I want have 2 vertical
tables with 10 images (2x10 a table = 20), is that possible ?

Hope someone knows... thanks.

---

### Post by Marsolin on 2006-11-24
I don't know for sure if these can do it, but you might want to try [ALE]("http://linuxappfinder.com/package/ale") or [nip2]("http://linuxappfinder.com/package/nip2").

---

### Post by Marsolin on 2006-11-24
Another one I forgot to mention is [Hugin]("http://linuxappfinder.com/package/hugin").

---

### Post by junglepeanut on 2006-11-25
Gifsicle is nice. Obviously works with gifs though. Make sure you optimize on compile each animation if the files are large. I had large gif files and it made a nice double pendulum animation, but with out optimization playback was very choppy as it was almost .5MB, but with optimization it was nice .4MB and played really smooth. Also somebody wrote a script online check with google to make it animate images into mpeg, too. Maybe they used something other than gifsicle though its been a while since I read that page.

---

### Post by slush1000 on 2006-11-25
If Pandora works then try rotating the images 90Deg then stitching them together horizontally then rotating after 90Deg back to get the vertical stack as you wanted.

---

