---
title: "A problem using ImageMagick's convert function to create thumbnails"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by monocycle on 2006-08-02
Hi all.

I want to create a script which creates specific sized thumbnails
from a set of images. This is my progress so far:

```

#!/bin/bash

for img in `ls *.jpg`
   do
      convert -quality 80 -thumbnail 140x105 $img thumb_$img
done

echo "All done!"

```

The problem is that my set of images are photos, and everyone
certainly knows people take "horizontal and vertical" photos,
so what I need is an if-clause to determine if the picture is
horizontal or vertical. Or in other words, is the width of the
image greater than the height of the image. So I could easily
create thumbnails which are resized horizontally (140x105) or
vertically (105x140). I did find that "convert" has a function
"verbose", which prints out information about images, but I have
no idea what to do with it.

Thanks in advance.

---

### Post by gThree on 2006-08-02
Not enough time to really look into this, but not sure ImageMagick offers anything more specific than string returned by:
```
identify fileName.ext
```

Someone else will probably know a quick, easy way to do this ... in the meantime, you might want to check out feh.  While essentially an image viewer, it offers this:
```
feh -L %w fileName.ext
```
which uses its custom listing option to get just the width of an image.  The man page does a good job of laying out your options.

---

### Post by monocycle on 2006-08-02
Thanks alot gThree!

I will paste my code here, in case someone knows a better way
to do this or find my code useful...

```

#!/bin/bash

echo "Generating thumbnails..."
for img in `ls *.jpg`
   do
      if [ "feh -L %w $img > feh -L %h $img" ]; then
         convert -quality 80 -thumbnail 140x105 $img thumb_$img
      else
         convert -quality 80 -thumbnail 105x140 $img thumb_$img
      fi
done
echo "All done!"

```

edit:
I noticed it resizes some photos 79x105... Does anyone know why?

---

### Post by Aelfric5578 on 2006-12-24
You asked this a few months ago, so maybe you've already found your answer or given up, but I was just trying to do something very similar to what you were doing, and I ran into the same problems.   I decided to do a little digging/experimenting.  The reason some of your images were not being resized the way you expected them to be was the test in your if/then statement was never being evaluated in the way you had hoped it would be, for two reasons: apparently the greater than symbol (>) doesn't work in this kind of if/then statement, and also you never told bash that "feh -L" is a system command.  The following should work (at least it worked in my case):

```

#!/bin/bash

echo "Generating thumbnails..."
for img in *.jpg
   do
      if [ "`feh -L %w "$img"`" -gt "`feh -L %h "$img"`" ]; then
         convert -quality 80 -thumbnail 140x105 "$img" thumb_"$img"
      else
         convert -quality 80 -thumbnail 105x140 "$img" thumb_"$img"
      fi
done
echo "All done!"

```

I am still having one problem that I was hoping someone could help me with.  Right now, in the collection of photos I have to process, some of them have spaces in the file names.  So instead of resizing "Our Show.jpg"  I get two errors: "Our" does not exist and "Show.jpg" does not exist.  How do I escape the spaces in $img.  I've tried various quoting strategies, but I'm still pretty new to bash scripting, and I don't really know what I'm doing.  I will continue to research, but if anyone could offer any suggestions, it would be greatly appreciated.

UPDATE: I was able to find the answer to my problems. (Thank you Google!)  The code above has been altered so that files with spaces in their names are now processed.

---

### Post by Admoseley on 2007-11-30
Great job guys, your script help me out big time!

Thanks a mil.

---

### Post by Nebvin on 2007-12-15
I know this is pretty much resolved but...

convert -quality 80 -thumbnail 140x140 "$img" thumb_"$img"

would fit all the images into a 140x140 box, making the longest side 140 and the shorter side whatever it needs to be to keep the proper aspect ratio.

I do this with the -resize option and it should work fine with the -thumbnail option too.

---

