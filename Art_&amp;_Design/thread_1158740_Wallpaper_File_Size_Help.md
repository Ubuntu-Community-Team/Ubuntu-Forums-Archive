---
title: "Wallpaper File Size Help"
date: 2009-05-14
forum: Art &amp; Design
---

### Post by FootySr on 2009-05-14
Hello Everyone,

I was planning to upload a Wallpaper I've done but my png size is way to large. I've flattened the image in GIMP and exported it but even at the highest compression setting the file is still over 1MB.

How do I go about making the image size smaller without loosing the quality? I prefer png but should I just save it as a jpeg?

Thanks for your time,

Jake :)

---

### Post by Orlsend on 2009-05-14
I have gimp add-on called "save for web" it lets you preview changes and it has more options you should check it out. then you should send it to [SmushIt]("http://developer.yahoo.com/yslow/smushit/"), to mush every single pixel without damaging the quality.

---

### Post by Bölvaður on 2009-05-14
This method will definitely make the image lose quality, but you probably will never see any difference unless if you magnify the image with before and after snapshots and 1 hour of search.... or 5 minutes.... depending on what type of coffee you drink.

save as...
nameOfPicture.jpeg
advanced options
subsampling : 1x1,1x1,1x1 (best quality)
DCT: floating point
smoothing: 0
<check out the other options>
quality : 85 &#8594; 90 (that range is quite good, I often use 87)

---

