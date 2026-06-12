---
title: "Image optimization for web"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by kimro on 2007-01-07
Is there any software for Ubuntu that'll optimize & compress GIF/JPG/PNG images for web?

---

### Post by madmetal on 2007-01-07
try gimp.
you may find it a little hard first but it is great!

---

### Post by IYY on 2007-01-07
Gimp will do this. When saving a JPG, it will ask you for the amount of compression. If you want to set the amount of colours in a gif, set the mode to indexed (Image > Mode > Indexed) and choose the amount of colours you want. In that same dialog you will also see an option to use a web-optimized pallete, as well as some other palletes.

Of course if you want to do this to a large amount of images in an automated fashion, there is a commandline tool called ImageMagick, invoked with the *convert* command. It's a bit trickier to learn, but can do everything you need without ever leaving the terminal. Something like

```
convert screenshot.bmp -quality 16 screenshot.jpg
```

will produce a very low quality but high compression JPG (that's 16 out of 100 in terms of quality, I think). The cool thing is that you can do it for 100 images instantly:

```
convert *.bmp  -quality 16 out.jpg
```

---

### Post by Omnios on 2007-01-07
I have used Gimp to do web optimized images and just have to choose file type such as jpeg and do preview to see the image quality. Also it will optimize animated gifs for the web.

---

### Post by Mongo5000 on 2007-09-21
Just figuring this out myself right now.  I used Fireworks when I was using windows but can't find anything as easy for linux.

I like the imagemagik way, will have to look into that more, but has anybody figured out an easier way to batch optimize pictures?

---

### Post by stani on 2007-09-24
> **Mongo5000 said:**
> I like the imagemagik way, will have to look into that more, but has anybody figured out an easier way to batch optimize pictures?Yep: phatch = photo & batch. You can download a deb ubuntu installer here:
[http://photobatch.stani.be](http://photobatch.stani.be)

---

