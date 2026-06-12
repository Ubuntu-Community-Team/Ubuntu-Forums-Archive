---
title: "The GIMP and Jpeg quality"
date: 2007-03-04
forum: Art &amp; Design
---

### Post by Baelfael on 2007-03-04
I was wondering how (if I can) fix up JPEG images that have bad quality to them in the GIMP. Such as this picture:
[http://en.wikipedia.org/wiki/Image:Devious.jpg](http://en.wikipedia.org/wiki/Image:Devious.jpg)

I want to clear so it doesn't look so bad. (You can see what I'm talking about I think)

---

### Post by jem7v on 2007-03-06
More or less: you would have to repaint over the entire picture, I think. There's no plugin I know of to clear up jpeg artifacts. I could be wrong, though, as I'm not omniscient. :)

---

### Post by zgornel on 2007-03-08
Well, those artifacts could be considered aditive noise. The artifacts are mostly seen on uniform color surfaces so you could apply a median filter on them ([http://en.wikipedia.org/wiki/Median_filter)](http://en.wikipedia.org/wiki/Median_filter)). Other filtering method wich I recommend is the alpha trimmed filtering (in Gimp: Filters/Enhance/NL Filter... -->Alpha trimmed mean ). What the filter does is to take a square region around a pixel, order it's pixels, cut *alpha/2* pixels form start and end (the highest, lowest values) and compute the mean of the remaining pixels. The result replaces the original pixel. As you can imagine, this eliminates the high/low pixel values in the uniform regions but creates a little bluriness at the edges. I played a little with the filter on your image and a value on alpha=0.94 and radius 0.7 yelded a acceptable result. Try other values and choose what fits you best 
Cheers !

---

### Post by jem7v on 2007-03-08
Yeah, there are definitely things you can do, but no filter or easy process that'll actually take it back to the original quality that I know of.

---

### Post by zgornel on 2007-03-08
Jpeg compression is a lossy process and if coarse quantization is involved (low quality factor) there not much you can do.

---

