---
title: "Help with Imagemagick convert -strokewidth"
date: 2012-03-19
forum: Art &amp; Design
---

### Post by acrocephalus on 2012-03-19
Hello!
I'm using this code
```
#Create watermark
convert -size 700x80 xc:black -font /usr/share/fonts/truetype/eager___.ttf -pointsize 100 -gravity center \
          -draw "fill black text 0,0  '©Acrocephalus'" -stroke black -strokewidth 2 \
          stamp_fgnd.png
  convert -size 700x80 xc:black -font /usr/share/fonts/truetype/eager___.ttf -pointsize 100 -gravity center \
          -draw "fill white  text  1,1  '©Acrocephalus'  \
                             text  0,0  '©Acrocephalus'  \
                 fill black  text -1,-1 '©Acrocephalus'" -stroke black -strokewidth 2 \
          +matte stamp_mask.png
  composite -compose CopyOpacity  stamp_mask.png  stamp_fgnd.png  stamp.png
  mogrify -trim +repage stamp.png
```
 adapted from [http://www.imagemagick.org/Usage/annotating/#wmark_text]("http://www.imagemagick.org/Usage/annotating/#wmark_text") to generate a png image to watermark my pictures. I'd like to increase the stroke width, but setting it to higher values does not seem to produce any effect. Could anyone help me to get thicker strokes?
Cheers!

---

