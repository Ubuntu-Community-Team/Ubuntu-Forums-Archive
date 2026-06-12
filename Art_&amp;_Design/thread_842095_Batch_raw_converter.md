---
title: "Batch raw converter"
date: 2008-06-27
forum: Art &amp; Design
---

### Post by AJB2K3 on 2008-06-27
I have 178 photos in 2048/1024 raw format.
Is there any batch program to convert them to 
178 10X75 png thumbs?
178 640X480 pngs ?
Unless phatch has been up dated it wouldn't touch raw files.

---

### Post by dominiquec on 2008-06-27
Have you tried ImageMagick?

---

### Post by forger on 2008-06-27
open up gnome-terminal and install rawstudio:
> sudo apt-get install rawstudio

then head to applications > graphics > rawstudio
there's a "batch" tab on the right

---

### Post by AJB2K3 on 2008-06-27
> **forger said:**
> open up gnome-terminal and install rawstudio:


then head to applications > graphics > rawstudio
there's a "batch" tab on the right
How do I use it because it sits there doing noting.

---

### Post by forger on 2008-06-28
On the menu File > Open directory, open the directory with the raw files.
Then menu Batch > Add to batch queue - This should add them in the list under Batch tab.

Now click on the **Batch** tab on the right.
Output directory: Click on it to choose where to output the resulting files.
Don't change "Filename template" or "PNG".
Click the "Change" button, choose the constant width or height or maximum size.

At the end you click the Start button.

---

### Post by AJB2K3 on 2008-06-28
> Then menu Batch > Add to batch queue - This should add them in the list under Batch tab.

Its grayed out. Can't click it.

---

### Post by forger on 2008-06-28
sorry, don't have a raw image to test it with :(

there's a list on the top.. probably where the image files are listed - how about selecting the filename and then clicking "add to batch queue" ?

edit: Just tested it, it works. Select your files, hold left mouse button and select the images you want to add to the batch process.

P.S. This was easy, you could've experimented a bit on your own :)

---

### Post by AJB2K3 on 2008-06-28
> **forger said:**
> sorry, don't have a raw image to test it with :(

there's a list on the top.. probably where the image files are listed - how about selecting the filename and then clicking "add to batch queue" ?

edit: Just tested it, it works. Select your files, hold left mouse button and select the images you want to add to the batch process.

P.S. This was easy, you could've experimented a bit on your own :)
Nope grayed out as well.

---

### Post by forger on 2008-06-28
well.. I tested it with three raw pictures from [http://www.rawsamples.ch/index_en.php](http://www.rawsamples.ch/index_en.php) and it was working

what camera raw type is this? file extension?

---

### Post by AJB2K3 on 2008-06-28
> **forger said:**
> well.. I tested it with three raw pictures from [http://www.rawsamples.ch/index_en.php](http://www.rawsamples.ch/index_en.php) and it was working

what camera raw type is this? file extension?
Fuji S5000 in .raf

---

### Post by forger on 2008-06-29
You're right, it doesn't add the .raf files.

backup plan:
```
sudo apt-get install ufraw
ufraw-batch --help
```

(using bash, sed and grep)

open a terminal, use this bash script:
```

outputdir="./converted/"
outputsize="640x480"
thumbnailsize="100x75"

[ -d $outputdir ] || mkdir $outputdir
list=`ls -1 | grep -i "\.raf$"`
for i in $list; do
	fname=`basename $i | sed -e 's/\.raf$//i'`
	outputfile="$outputdir$fname.png"
	thumbfile="$outputdir$fname.thumb.png"
	ufraw-batch --overwrite --silent --out-type=png16 --size=$outputsize --output=$outputfile "$i"
	ufraw-batch --overwrite --silent --out-type=png16 --size=$thumbnailsize --output=$thumbfile "$i"
	echo "Done $i"
done
```

---

### Post by AJB2K3 on 2008-06-29
> **forger said:**
> You're right, it doesn't add the .raf files.

backup plan:
```
sudo apt-get install ufraw
ufraw-batch --help
```

(using bash, sed and grep)

open a terminal, use this bash script:
```

outputdir="./converted/"
outputsize="640x480"
thumbnailsize="10x75"

[ -d $outputdir ] || mkdir $outputdir
list=`ls -1 | grep -i "\.raf$"`
for i in $list; do
	fname=`basename $i | sed -e 's/\.raf$//i'`
	outputfile="$outputdir$fname.png"
	thumbfile="$outputdir$fname.thumb.png"
	ufraw-batch --overwrite --silent --out-type=png16 --size=$outputsize --output=$outputfile "$i"
	ufraw-batch --overwrite --silent --out-type=png16 --size=$thumbnailsize --output=$thumbfile "$i"
	echo "Done $i"
done
```
Thanks, seams to be working except for the thumbs are all blurred.

---

### Post by forger on 2008-06-29
they're not blurry, the thumbnails are 10x75 pixels as you required.. open the thumbnail png file to see its real, non-blurry size, if you want bigger thumbnails change the size.

---

### Post by AJB2K3 on 2008-06-29
> **forger said:**
> they're not blurry, the thumbnails are 10x75 pixels as you required.. open the thumbnail png file to see its real, non-blurry size, if you want bigger thumbnails change the size.
That was the issue.
I meant 100X75 but anyway I created a text file with your script, made it executable and it works out great thanks alot.

---

