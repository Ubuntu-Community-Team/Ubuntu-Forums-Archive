---
title: "HOW TO resize and watermark lots of graphics files at once using Linux"
date: 2007-04-20
forum: Art &amp; Design
---

### Post by Ted_Smith on 2007-04-20
Since I moved to linux a couple of years ago, I have always found it to be a terrible struggle to resize AND  watermark a mass of pictures all at once using one command and if you was also wondering hwo to resize and watermark using Linux, here's the answer! 

First, install the imagemagick suite ([http://www.imagemagick.org](http://www.imagemagick.org))
```

sudo apt-get install imagemagick

```

That installs various graphics apps such as convert, mogrify, resize etc which are all part of the ImageMagick suite of tools. 

As an exampe, if you want to resize all your JPEG files by 65% of their original width and then stamp a watermark on them in the middle, at the bottom of each picture, then just run this command from the terminal (change the values accordingly to fit your needs - this example assumes they are jpg's. If they're something else just change the extension type at the end or just use * for all files) : 

```

mogrify -resize 65% -font Arial -pointsize 25 -verbose -draw "gravity south fill black text 0,33 'YOUR WATERMARK TEXT HERE' fill white text 1,32 'YOUR WATERMARK TEXT HERE' *.jpg

```

Ted

---

### Post by durand on 2007-04-26
Nice, thanks a lot!

---

### Post by Ted_Smith on 2007-04-29
I've just found out today that you can also chuck a '-quality 80' in there as well to reduce the quality of your JPEGs to a lesser value. In this case, 80% but you can choose 85, 90, or whatever you like. For example : 

```

mogrify -resize 65% -quality 85 -font Arial -pointsize 25 -verbose -draw "gravity south fill black text 0,33 'YOUR WATERMARK' fill white text 1,32 'YOUR WATERMARK'" *.jpg
```

---

### Post by michux on 2007-05-11
Here is a new howto about Imagemagick where more such tricks are presented: [Enchanting Pictures with ImageMagick](http://polishlinux.org/apps/graphics/enchanting-pictures-with-imagemagick/)

---

