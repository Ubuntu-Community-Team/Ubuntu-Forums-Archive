---
title: "Neat way to visualize binary data"
date: 2009-04-18
forum: Art &amp; Design
---

### Post by brywilharris on 2009-04-18
Hey all,
I wrote this cool little tool to visualize binary data!
Bryan

---

### Post by smartboyathome on 2009-04-18
I made one modification. I changed it to PNG instead of BMP (why does BMP exist still?!). It produces random noise?

---

### Post by Nevon on 2009-04-19
> **smartboyathome said:**
> I made one modification. I changed it to PNG instead of BMP (why does BMP exist still?!). It produces random noise?

You feel like sharing that? :P

---

### Post by brywilharris on 2009-04-20
Png does compression and the contents are no longer a faithful representation of what's underneath.

With minimal work, you could convert back from the bitmap to the file you were mapping.  With a png information is lost.  It makes almost the same pretty picture, but the picture is blurred.

Try running the program on a text file and look at the difference.  Or do:  dd if=/dev/sda of=mbr.img count=100; bin2bmp.py mbr.img 128

This shows you your master boot record.  I would like to munge the colors a little to automatically exphasize text files, executables, pictures, etc, but this is a first pass.

---

### Post by brywilharris on 2009-04-20
In the last line of the program change BMP to PNG to output png files.  Or you can make it JPEG to output jpg's.  Of GIF to make gifs.

---

### Post by red_Marvin on 2009-04-21
Fyi png uses a non destructive compression method, so no pixel data should be lost.

---

### Post by brywilharris on 2009-04-22
Yes I noticed that.   with bitmap I knew wouldn't mangle anything.  The newest version actually defaults to jpeg.  I don't have anything against png, I'm just more familiar with the other formats.

Here are the newest options:
bin2bmp.py -h, --help
usage: /home/bryan-user/bin/bin2bmp.py <options> ... <filename>
-i, --input       	filename to visualize  [mandatory] 
-w, --width       	width of output image
-o, --output      	output filename (default is <input_filename>.jpg)
-V, --verbose     	print lots of extra stuff
-b, --bmp        	reverts to the old bitmap style output(jpg is default)
-m, --monochrome 	one bit per pixel
-c, --compress   	highly compressed jpeg

[http://sourceforge.net/projects/bin2bmp/](http://sourceforge.net/projects/bin2bmp/)

---

### Post by brywilharris on 2009-04-22
The default is UNCOMPRESSED jpeg, CMYK.  quality=100.  
compressed jpeg uses quality=10
monochrome makes a pixel for each bit and uses gif output
bitmap output is still selectable.

---

### Post by brywilharris on 2009-04-22
I added png in to the latest release.  -p or --png.  It makes ~40% smaller pictures than bitmap with the same pixels.

---

### Post by Martje_001 on 2009-04-22
> **brywilharris said:**
> With a png information is lost.  It makes almost the same pretty picture, but the picture is blurred.
Not true! PNG uses lossless compressions (gzip IIRC).

---

### Post by brywilharris on 2009-04-22
> **Martje_001 said:**
> Not true! PNG uses lossless compressions (gzip IIRC).
You're right.  I didn't realize that!  Check this out!
I think I need to write a fuse filesystem for this.  It's almost too simple and so cool.  It's a file system where you can see the contents.

[http://randommusingsofarealgeek.blogspot.com/2009/04/bmpfs.html](http://randommusingsofarealgeek.blogspot.com/2009/04/bmpfs.html)

---

