---
title: "How do you shrink the size of digital pictures?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by crazydiver on 2007-08-06
Hello All,

    I want to post some pics on the web but its too large and a hassle for some viewers to view a 5mb pic on slow internet conections. I would like to know how to convert a 5mb pic to a 50k or something small like that... as long as its in the kilos and not the megas. Do you recommend any software that can do that? 
  I use gimp and played around with it for a bit but haven't figured it out yet.

Thanks.

---

### Post by dmjones500 on 2007-08-06
Are you wanting to keep the picture at the same size?  If not, you can go  "Image > Scale Image" and choose a smaller size, which should result in a smaller file size.

You could also try resaving the file, using PNG file type with full compression -- that could make it smaller.  

Similarly saving as a JPEG with medium-ish quality will reduce the size.  If you save as a JPEG, check the box that says "show preview in image window" when you're picking the quality, as it helps you see what it will look like, and crucially it updates the "File size:" information (which would otherwise say "unknown").

---

### Post by crazydiver on 2007-08-06
thANKS...I forgot about the pngs!

---

### Post by Tux Aubrey on 2007-08-06
Hi

I'm no expert, but here are a few methods I use to reduce the size of image files:

1.  Make the image smaller (in GIMP select Image>Scale Image)

2. Reduce the number of colors (eg Image>Mode>Indexed) - that gives you the option to optimize for web colors too.

3. You could also try saving in a compressed (but web compatible) format (jpg or gif)  jpg save lets you trade off quality for size of the file.  But I seem to have better results with png format.

---

### Post by crazydiver on 2007-08-07
Tux Aubrey,

   Thanks for your expertise!!! :)

---

### Post by crazydiver on 2007-08-07
oh yeah... how do you convert the image to a png file? and how do you compress it?

---

### Post by daverich on 2007-08-07
sorry to butt in, but is there an image-batch-resizer available for ubuntu?

I bought one for xp, but haven't found anything similar yet and i do alot of batch photo work.

Kind regards

Dave Rich

---

### Post by nitro_n2o on 2007-08-07
> **crazydiver said:**
> oh yeah... how do you convert the image to a png file? and how do you compress it?
converting to png is easy in gimp you just save as and choose the filetype to be png ... it'll also prompt you for some compression things

---

### Post by hashimoto on 2007-08-07
> **daverich said:**
> sorry to butt in, but is there an image-batch-resizer available for ubuntu?

I bought one for xp, but haven't found anything similar yet and i do alot of batch photo work.

Kind regards

Dave Rich

There is a plugin for GIMP here: [http://members.ozemail.com.au/~hodsond/dbp.html](http://members.ozemail.com.au/~hodsond/dbp.html)
I haven't installed or used it, but seems to do what you are looking for.

---

### Post by Lord Illidan on 2007-08-07
Or this : [http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)

---

### Post by davidsrsb on 2007-08-07
Stripping the exif information from a jpeg file saves a little space

---

### Post by mattmole on 2007-08-07
As a command line user I have a simple way to shrink a load of images.

Use imagemagick (sudo apt-get install imagemagick)

If it is just one directory worth of images use

mogrify -resize 1024x1024 *.jpg

This will overwrite the images with new ones

Another way (and the way I prefer) is the following:

find /PATH/TO/IMAGES -name '*.jpg' -exec convert -resize 1024x1024 {} /NEW/PATH/{} \;

Of course it doesn't have to be jpg, it could be png etc. What this does is to search for any images with the extension 'jpg' and then use imagemagick to take the file found '{}' and to resize it using the convert command. Once resized it will retain the same filename in the new directory.

I am not sure if that is the exact syntax for mogrify.

HTH

Mattmole

---

### Post by daverich on 2007-08-07
> **mattmole said:**
> As a command line user I have a simple way to shrink a load of images.

Use imagemagick (sudo apt-get install imagemagick)

If it is just one directory worth of images use

mogrify -resize 1024x1024 *.jpg

This will overwrite the images with new ones

Another way (and the way I prefer) is the following:

find /PATH/TO/IMAGES -name '*.jpg' -exec convert -resize 1024x1024 {} /NEW/PATH/{} \;

Of course it doesn't have to be jpg, it could be png etc. What this does is to search for any images with the extension 'jpg' and then use imagemagick to take the file found '{}' and to resize it using the convert command. Once resized it will retain the same filename in the new directory.

I am not sure if that is the exact syntax for mogrify.

HTH

Mattmole

now that sounds interesting.

I wonder can you specify a percentage shrink?

Kind regards

Dave Rich

---

### Post by mattmole on 2007-08-07
Yes, Ive just done it:

convert -resize 10% file_to_shrink.jpg shrunk_file.jpg

mattmole

---

### Post by crazydiver on 2007-08-07
Thanks for all the help everyone. Mattmole... you just taught us something cool!

---

### Post by antoz on 2007-08-07
Any picture editor like the gimp, photoshop  etc... can resize photos, after you opened the file use click on image-> scale in the gimp or resize in some of the other programs-> choose the file format like JPG, file size and compression and then "save as" to save the file. Usually anything about 800x600 pixels or less will reduce the file size to less then 100 kbites. It is recommended that you duplicate the layer first and work on the copy but not absolutely necessary, A.

---

### Post by Phosphoric on 2007-08-07
For sending reduced photos via email I just use Digikam.  There is an option to resize images automatically.  Just click on that and it opens up your email client with the reduced file already attached.

Make sure that you install all the plugins for DigiKam as the autoresizing is not in the base package.

---

### Post by stani on 2007-08-08
Phatch is the ideal to batch process photos like resize, rounded corners, drop shadows. Send me a private message with your email and you will get a deb file:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

---

### Post by Obor on 2007-08-08
I use "nautilus-image-converter" - in repos. It adds a menu item, to batch resize images to your file manager. Just highlight and off you go. It can't get any easier.

nautilus extension to mass resize images
Adds a "Resize Images..." menu item to the context menu of all images.
This opens a dialog where you set the desired image size and file name.
A click on "Resize" finally resizes the image(s) using ImageMagick's
convert tool.

---

### Post by clinto on 2007-08-11
I wanted to post a screenshot but the .png I have is 1.5MB. How do you reduce the byte size without reducing the resolution size? I noticed others have uploaded some 1280x1024 sized pictures. How were they able to do it without changing how the picture looked? It doesn't make sense to me. Is it because there are more colors in my picture? I used gimp and tried the "indexed" option to change it to web-optimized, but it only reduced it to 1.2MB. How the heck did these people reduce a picture of 1280x1024 to 50KB?

---

