---
title: "Batch Watermarking Images?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by elivance on 2007-05-16
I'm totally new to Ubuntu (Fiesty Fawn) - I've been using it mfor a few weeks now and i'm finding a few things rather tricky!

I've been trying to add a watermark to some images using ImageMagick through the terminal but I can't seem to get it to do it properly!

I have created a watermark image called WM.jpg which i want to overlay at the very bottom of the original image. Whenever the watermark is added its grey background becomes transparant and the white text changes to all manner of different colours - the only thing that's added correctly is the black line at the top!

I have been using composite -watermark 60% -gravity southwest WM.jpg origimage.jpg processed.jpg

Also, is there a way to automate the process - so for instance it will apply the above to all the images in a folder?

Cheers!

---

### Post by trent dillman on 2007-05-18
...

---

### Post by eentonig on 2007-06-01
And a better command option(at least for me) is -dissolve

> composite -dissolve 25% -gravity south label.PNG   poloroid_South.png  wmark_dissolve.jpg

---

### Post by stani on 2007-06-16
In case you don't want to use the command line, but prefer a nice graphical program, I can recommend you phatch. It can do watermarking with any transparency you want. It can display a single watermark or tile/scale them as well. Besides that it allows you also to drop shadow, round corners, scale your image, ...

---

