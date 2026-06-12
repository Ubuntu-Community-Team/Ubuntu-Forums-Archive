---
title: "Imagemagick gives error 'ambiguous redirect'"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by diafygi on 2007-07-08
hey, I'm trying to resize some pictures, anybody know if I can do that with a simple command? I read on imagemagick's [[COLOR="Blue"]website[/COLOR]]("http://www.imagemagick.org/script/mogrify.php") that all you need to do is:
```
mogrify -resize 800x600 *.jpg
```
but when I do that, bash give the output: 
```
bash: *.jpg: ambiguous redirect
```
Does that mean that bash can't tell that I mean all files that end with '.jpg'? Is there something I should use instead of an asterisk?

---

### Post by diafygi on 2007-07-29
I needed to put quotes around the dimensions:
```
mogrify -resize "800x600" *.jpg
```

---

