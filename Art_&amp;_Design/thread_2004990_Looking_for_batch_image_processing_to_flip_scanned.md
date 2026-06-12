---
title: "Looking for batch image processing to flip scanned images"
date: 2012-06-16
forum: Art &amp; Design
---

### Post by hoey2011 on 2012-06-16
I have a huge project ahead of me: Scanning about 35 years worth of photos from my grandmother's world travels.  This is my birthday present to her, as she will be 75 this year, and she will surely want to reminisce on her experiences over the years.  I am using a neat little Pandigital hand scanner that speeds up the process 10x over a traditional clamshell scanner.  I am cropping my little workstation setup images one-by-one, because, well, I have to.  Once I'm finished, however, I will need to flip all of the images horizontally, as is the limitation to these kinds of scanners.  

I am looking for either a command line batch program, GUI program will work also, that will do this for me.  I do NOT want to go back through and flip them all, and would much prefer to just point to a folder and have all the contents transposed for me.  

Suggestions?:eek:

---

### Post by d2btoo on 2012-06-16
Although I'm not sure, but maybe Phatch can do that.

HTH

---

### Post by texpat on 2012-06-16
Try Imagemagick. This is a command line tool.

Go to your imgaes directory and

```
convert -flop *.jpg
```

Consult [http://www.imagemagick.org/script/command-line-options.php](http://www.imagemagick.org/script/command-line-options.php) for details.

---

### Post by hoey2011 on 2012-06-16
Will this allow a batch processing of all the contents? Or will I be forced to process them one by one?

---

### Post by hoey2011 on 2012-06-16
Just read the documentation (had to do some laundry), and saw that the * is for globbing, and answered my own question.  Thanks for pointing me to the info :)

---

### Post by SeijiSensei on 2012-06-16
Someone recently asked a more complex version of this question about rotating only images in landscape mode.  I wrote a little [script]("http://ubuntuforums.org/showthread.php?t=1951949") using Imagemagick that apparently did the trick.  You might find it helpful.

---

### Post by hoey2011 on 2012-06-17
I asked you to post it, then noticed you linked it... lol  I MUST be tired

---

