---
title: "Photo Presentations ?"
date: 2010-01-05
forum: Art &amp; Design
---

### Post by Rodney9 on 2010-01-05
Hello, 

I would like to show off some of my photos to my friends who have windows and macs.

What would be the best way, I have 70 odd photos to show off, they email me either power point or pdf's.

I have tried Open Office Presentation, it's ok, is there a pdf photo creator that looks good ? or something else altogether ?

Thanks,
Rodney.

PS: Another forum member suggested  "convert -compress jpeg *.jpg presentation.pdf " but I get a "Segmentation fault"

---

### Post by prshah on 2010-01-05
> **Rodney9 said:**
> I have tried Open Office Presentation, it's ok, is there a pdf photo creator

You can directly export your presentation to PDF from OOo Presentation's File-Export to PDF option.

---

### Post by Rodney9 on 2010-01-05
> **prshah said:**
> You can directly export your presentation to PDF from OOo Presentation's File-Export to PDF option.

Well ok convert -compress jpeg *.jpg presentation.pdf doesn't work.

So I'll try Open Office again, is there a way to add multiple photos ? , I seem only to be able to add one at a time.

Rodney

---

### Post by Rodney9 on 2010-01-05
My win friend sends me 35 photos in pdf @ 2.4 mbs

Why can I not do this ?

I don't necessarily need pdf, just something that will let me email 10-20 photos in under 3-4 mbs that looks good.

---

### Post by vanadium on 2010-01-05
You will need to use convert in a different way: first create the individual PDF versions of the photos, then concatenate the PDF's into one file with pdftk:

```

for f in *.jpg ; do convert -compress jpeg "$f" "$f".pdf ; done
pdftk *.jpg.pdf cat output output.pdf

```

Alternatively, you might just zip the graphics into one zip archive for mailing.

---

### Post by Zimmer on 2010-01-05
Try gThumb image viewer and either:
Create a web album of the photos you wish to send or
an Index image which will collect several images onto one single image...

a 12 image album I tested created a folder of just 1.1Mb,

also, they only need a browser to access it.

---

### Post by Dragonbite on 2010-01-05
> **Rodney9 said:**
> Hello, 

I would like to show off some of my photos to my friends who have windows and macs.

What would be the best way, I have 70 odd photos to show off, they email me either power point or pdf's.

I have tried Open Office Presentation, it's ok, is there a pdf photo creator that looks good ? or something else altogether ?

Thanks,
Rodney.

PS: Another forum member suggested  "convert -compress jpeg *.jpg presentation.pdf " but I get a "Segmentation fault"

Once the images are placed into a PDF, they will not be subject to different machines displaying things differently as a PowerPoint, Word, Excel file may.  It in essense makes a "snapshot in time"

---

### Post by kaibob on 2010-01-05
> **Rodney9 said:**
> My win friend sends me 35 photos in pdf @ 2.4 mbs

Why can I not do this ?

In the past, I have used Imagemagick to directly convert a number of JPG files to one PDF document just as you are attempting to do. Now, this always issues a segmentation fault, even with a very small number of JPG files. There are a number of bug reports on this. 

The solution suggested by vanadium works and is probably the best alternative until a bug fix is issued.

---

### Post by Newfoundlander on 2010-01-05
Why not e-mail a zip file of the photos?

---

### Post by Rodney9 on 2010-01-05
This works, Thank You Doc Dan @ [http://forums.whirlpool.net.au/forum-replies.cfm?t=1355736&p=-1#bottom](http://forums.whirlpool.net.au/forum-replies.cfm?t=1355736&p=-1#bottom)


@22217799 DocDan writes...
["Segmentation fault"]

["Ok I managed to recreate the same problem. Just install graphicsmagick-imagemagick-compat and it will work:"]

["sudo apt-get install graphicsmagick-imagemagick-compat"]

Thank You, that works with " convert *.jpg foo.pdf " very well or " convert -compress jpeg -quality 55 -resize 175% -density 150 *.jpeg Photo.pdf  "

---

