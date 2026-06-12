---
title: "EXIF batch processing software"
date: 2011-05-14
forum: Art &amp; Design
---

### Post by jcolyn on 2011-05-14
Any good software for batch deleting of exif data in digital photos?

Irfanview will do it but then I'd have to install wine which I don't want to unless it is the only option..

---

### Post by robert shearer on 2011-05-15
Perhaps this would be worth investigating....
[http://linux.die.net/man/1/jhead](http://linux.die.net/man/1/jhead)

Cheers Bob.

---

### Post by jcolyn on 2011-05-15
> **robert shearer said:**
> Perhaps this would be worth investigating....
[http://linux.die.net/man/1/jhead](http://linux.die.net/man/1/jhead)

Cheers Bob.

I've tried jhead. It only does part of what I need.

So far the only program I have found that will do it all is Irfanview which of course is a Windoze program.

In the end I suspect I'll have to install it via wine..

---

### Post by mcduck on 2011-05-17
Imagemagick does that pretty well (And removes all other metadata as well).

for example:
```
convert file.jpg -strip file.jpg
```

...or the same for all images in the current directory:
```
for i in *.jpg; do convert "$i" -strip "$i"; done
```

(if you don't need to keep the original image you can use the *mogrify* command instead of *convert*. In that case you don't need to specify the output file, as mogrify simply overwrites the original.)

edit: Exiftool should work as well if it's only the EXIF data you wish to edit/remove.

---

