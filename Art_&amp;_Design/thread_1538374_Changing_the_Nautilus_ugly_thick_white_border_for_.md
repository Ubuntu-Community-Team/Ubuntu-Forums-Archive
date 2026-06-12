---
title: "Changing the Nautilus ugly thick white border for thumbnails"
date: 2010-07-25
forum: Art &amp; Design
---

### Post by pt123 on 2010-07-25
I found the new thick white borders around thumbnails in Lucid rather ugly. So I did some tweaking and got some good results.
Examples here
[http://ubuntuforums.org/showpost.php?p=9541118&postcount=2](http://ubuntuforums.org/showpost.php?p=9541118&postcount=2)

Maybe someone with better graphic design skills can improve it further. Hopefully get that as the default look for Maverick.

---

### Post by quixote on 2010-07-27
Looks nice!

---

### Post by hugmenot on 2010-07-27
Mh bevel.

---

### Post by pt123 on 2010-07-27
it is actually meant to produce a light shadow effect but on some background colours it ends up producing a bevel look

---

### Post by quixote on 2010-07-29
nice elegant bevel is still way better than nursery school-looking white border.

---

### Post by pt123 on 2010-07-29
true the thick white border looks fine on a white background, but rather ugly on other colours

---

### Post by hugmenot on 2010-07-29
> **quixote said:**
> nice elegant bevel is still way better than nursery school-looking white border.


bevel smells like ’80s

---

### Post by kyleabaker on 2010-07-30
+1 It's an improvement.

While its obviously not "perfect" I still like it much more than the thick white borders.

However, I have to agree with @hugmenot that beveling is a bit old school. What do you think about some light drop shadow? The first link is default, the second is with dropshadow x:2; y:2; radius:4; opacity:80; via Gimp.

[http://a.imageshack.us/img580/6392/screenshot1ry.png](http://a.imageshack.us/img580/6392/screenshot1ry.png)
[http://a.imageshack.us/img580/3383/screenshot2h.png](http://a.imageshack.us/img580/3383/screenshot2h.png)

How does this compare?

---

### Post by pt123 on 2010-07-30
sweet that is the effect I was trying to achieve.

Can you post the frame here?

---

### Post by kyleabaker on 2010-07-30
I'll have to put one together since I just edited that screenshot with Gimp as an example.

Where is the original frame stored? I'll put it together and post it, but I'd like to test it and tweak it before doing so.

---

### Post by quixote on 2010-07-30
hugmenot:> bevel smells like &#8217;80s

The 80s?  *The 80s??*  Bwahahaha!  What I remember from the 80s is an Apple store with funky boxen the size of carry-on luggage and dinky screens where you could see your BASIC programs.  And I remember spending way too much time in front of black terminals with white or green type.  

Bevels!  We would have killed for bevels.  (Oh, and yes, the snow *was* three feet deep because global warming wasn't so bad yet.)

P.S. kyleabaker's shadow effect is very nice!

---

### Post by kyleabaker on 2010-07-30
> **quixote said:**
> P.S. kyleabaker's shadow effect is very nice!

Thanks. If someone can tell me where this "thumbnail_frame.png" file can be found on my computer then I'll start tweaking until I get it like the picture I posted and link it here. 

Anyone know the location of the image file that they use for these thumbnail frames is?

EDIT:
Nevermind, I've found them, but there are two:
```

cd /
sudo find . -iname "*thumbnail_frame.png" -print

```

```

./usr/share/pixmaps/gsearchtool/thumbnail_frame.png
./usr/share/pixmaps/nautilus/thumbnail_frame.png

```

I'll start tweaking these and post my results when I get it looking like the screenshot.. wish me luck. ;)

---

### Post by pt123 on 2010-07-30
it is this one 
/usr/share/pixmaps/nautilus/thumbnail_frame.png

mentioned in the initial linked post
[http://ubuntuforums.org/showpost.php?p=9541118&postcount=2](http://ubuntuforums.org/showpost.php?p=9541118&postcount=2)

---

### Post by hugmenot on 2010-07-30
> **quixote said:**
> hugmenot:

The 80s?  *The 80s??*  Bwahahaha!  What I remember from the 80s is an Apple store with funky boxen the size of carry-on luggage and dinky screens where you could see your BASIC programs.  And I remember spending way too much time in front of black terminals with white or green type.  


I was thinking of Motif and CDE.

---

### Post by kyleabaker on 2010-07-30
Ok, I've got a working thumbnail_frame.png image. I will work on it a little more and polish it up, but in the mean time, if you want to test it out just do the following.

**Backup the original file using:**
```

sudo mv /usr/share/pixmaps/nautilus/thumbnail_frame.png thumbnail_frame.png.bak

```


**Install mine:**
```

wget http://a.imageshack.us/img651/8666/thumbnailframe.png
sudo mv thumbnailframe.png /usr/share/pixmaps/nautilus/thumbnail_frame.png
killall nautilus

```


**Restore to the original again:**
```

sudo mv /usr/share/pixmaps/nautilus/thumbnail_frame.png thumbnailframe.png
sudo mv thumbnail_frame.png.bak /usr/share/pixmaps/nautilus/thumbnail_frame.png
killall nautilus

```

If you need the original, I've uploaded it here:
[http://a.imageshack.us/img651/5790/thumbnailframey.png](http://a.imageshack.us/img651/5790/thumbnailframey.png)

Let me know how it works for you. Here is an actual screenshot of it working for me (click to view the full size)..
[[IMG]http://a.imageshack.us/img571/2682/screenshottz.png[/IMG]]("http://a.imageshack.us/img571/1791/screenshotai.png")

I'm gonna tweak the thumbnail_frame.png to lighten the shadow a bit, but I'll post it as well.

---

### Post by kyleabaker on 2010-07-30
Same rules for backing up and restoring the original image.

If you want the (almost) exact style that I had in the first screenshots I posted on page 1, then do the following which installs a slightly modified image from the one above.

Open a terminal and copy/paste the following..

**Install mine:**
```

wget http://a.imageshack.us/img135/8666/thumbnailframe.png
sudo mv thumbnailframe.png /usr/share/pixmaps/nautilus/thumbnail_frame.png
killall nautilus

```

Enjoy guys! I like it a lot already!

---

### Post by pt123 on 2010-07-31
Thanks for that, I have modified your frame, to a thinner more lighter shadow, which I prefer.

---

### Post by quids on 2010-08-01
Cool that worked a treat

---

### Post by AldenIsZen on 2010-10-11
Looks much better imho.

---

### Post by pt123 on 2010-10-12
you have great taste ;)

---

### Post by AldenIsZen on 2010-10-12
Well I mainly meant than the white bevel, but I did prefer yours... credit goes to him for making the first one and the idea of course. :P

---

### Post by Mr LJ on 2012-06-09
I tried to remove the thumbnail-frame in Nautilus 3.4.2 , but there is no file "/usr/share/pixmaps/nautilus/thumbnail_frame.png"

---

### Post by pt123 on 2012-06-09
This was for Nautilus in Gnome 2. I am not sure where files are kept in Gnome 3.

---

### Post by overdrank on 2012-06-09
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

