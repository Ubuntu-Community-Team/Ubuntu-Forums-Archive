---
title: "How can I batch edit images?"
date: 2008-09-10
forum: Art &amp; Design
---

### Post by grs on 2008-09-10
I have Ubuntu Studio installed with various graphoc packages that come as standard.

My question is about batch editing. Which program do I use to do the following?

I have a large number of photographs which I would like to resize. Most of the images are the same size/ratio and its a matter of say, reduce by 50%.
For the images of different sizes can I tell it to make, say, the horizontal axis 200 pixels long and then resizes but maintaining the vertical ratio to preven t the image from getting squashed.

---

### Post by eilu on 2008-09-10
Try Phatch. It should be adequate for your needs. See the repos.

---

### Post by vanadium on 2008-09-10
The swiss army knife: imagemagick's convert: probably already installed by default. "man convert" shows a small help page that links to extensive documentation on the web.

---

### Post by leg on 2008-09-10
I have just been looking into convert/mogrify for my own use and it will work very well for re-sizing images. While I was looking for a solution I found out that image magick has a limit of 768 files for a run so
```
convert 50% *.jpg
``` would only work if you had less than that number in the directory to convert. The way around it is to wrap a script around the convert command something like this
```

for f in *.jpg
do
    convert 50% $f
done

```
now I am not totally up on bash scripting and trying to remember the loop construct and not sure the above is correct. If you are familiar with any other language you could probably wrap using that instead if you want.

Places I found useful:
[GimpTalk forums]("http://www.gimptalk.com/forum/") very useful place for image related stuff and very helpful.
[ImageMagick forums]("http://www.imagemagick.org/discourse-server/")

---

### Post by V for Vincent on 2008-09-11
Phatch has a really intuitive GUI, so it gets my vote.

---

### Post by grs on 2008-09-11
Thanks, I'll have a look at those.

---

