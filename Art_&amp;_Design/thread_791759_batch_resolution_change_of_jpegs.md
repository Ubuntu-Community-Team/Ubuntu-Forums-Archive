---
title: "batch resolution change of jpegs"
date: 2008-05-12
forum: Art &amp; Design
---

### Post by jessika-kaos on 2008-05-12
I have a few directories each with several thousand jpegs (at 3264 x 2448 pixels) that I would like to reduce to maybe half resolution. Is there a command line program that could do this for all pictures in the directory in one go? If so, how?

---

### Post by rax_m on 2008-05-12
Hi Jessika

It is possible, in fact one of the members of this forum designed a GUI application called "Phatch". Search for it on these forums and there'll be a link to the download. 

Regards
Rax

---

### Post by jessika-kaos on 2008-05-12
Cool, thanks!

---

### Post by dangermouse28 on 2008-05-14
Google for nautilus scripts - one of them does re-sizing of multiple images. Then you just right-click, scripts, re-size images, bang in the size you want and you're all done!

---

### Post by lessthanjake on 2008-05-17
Just use Imagemagick, it is perfect for tasks like this:


```

sudo apt-get install imagemagick
cd image_folder
mkdir resized
for f in *jpg
do
convert -resize 50% $f resized/$f
done
```

or you can make it a bit more fancy, with a script:

```

#!/bin/bash

types="*jpg *png"

mkdir resized

files=`ls $types 2> /dev/null`
n=`echo $files |wc -w`
i=0

for f in $files
do
    i=$[i+1]
    printf "[$i/$n] $f"
    convert -resize 50% $f resized/$f
    printf "\r"
done
echo

```

---

