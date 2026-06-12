---
title: "Inserting/Sizing photos into an e-mail"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by FreddyGill on 2007-09-05
How do I insert multiple photos (.jpg) directly into an e-mail. I do not want to send them as an attatchment. I want them embedded into the e-mail so I can explain them to people. They are too big to fit & need to be resized. I don't want to resize each one individually (too time consuming!) 6x4 inches would work. Problem I'm having: When I try to insert a photo, the link to the photo shows up instead of the actual photo. Why?

---

### Post by erfahren on 2007-09-05
you didn't mention what email client you're using. as for the resizing check this out:
[http://rhosgobel.blogspot.com/2006/07/bulk-resizing-and-renaming-images-in.html](http://rhosgobel.blogspot.com/2006/07/bulk-resizing-and-renaming-images-in.html)

---

### Post by vanadium on 2007-09-05
For batch-resizing images, use the command

convert infoto.jpg -resize 100x100 outphoto.jpg

This will resize the images and make sure their width or hight is at most 100 pixels

To do this automatically for a couple of images:

for f in *.jpg ;  do convert $f -resize 100x100 resized_$f ; done

I cannot help you with the email-part because you do not tell what email application you use.

---

### Post by n3tfury on 2007-09-05
i don't understand why people still use email to distribute photos when there are plenty of good places to host them with descriptions/comments?  (flickr and picasaweb).  have you thought about doing that instead?  it's especially nice for those poor recipients with dialup.

---

### Post by BlackMeTaL on 2007-09-05
> **n3tfury said:**
> i don't understand why people still use email to distribute photos when there are plenty of good places to host them with descriptions/comments?  (flickr and picasaweb).  have you thought about doing that instead?  it's especially nice for those poor recipients with dialup.

Some people don't want their pictures to be public.

Anyway ontopic:
I use a nautilus extension called nautilus-image-converter.
To install it: sudo apt-get install nautilus-image-converter

---

### Post by n3tfury on 2007-09-05
> **BlackMeTaL said:**
> Some people don't want their pictures to be public.

Anyway ontopic:
I use a nautilus extension called nautilus-image-converter.
To install it: sudo apt-get install nautilus-image-converter

both flickr and picasaweb allow you to make them private. carry on.

---

### Post by FreddyGill on 2007-09-05
Thank you. I'm using Evolution. By the way, this is the 1st time ever that I have used a forum. I have to go to work, but will look again tonight and try out your suggestions. I have lots to learn.

---

### Post by lisati on 2007-09-05
> **FreddyGill said:**
> Thank you. I'm using Evolution. By the way, this is the 1st time ever that I have used a forum. I have to go to work, but will look again tonight and try out your suggestions. I have lots to learn.

Good on you! 

And good luck!
:)

---

### Post by FreddyGill on 2007-09-06
I installed the "nautilus-image-converter" from the synaptic program and it works great! I'm not familiar with using ubuntu's command line stuff yet, so I went with easy for now, Thank you very much for helping me. I intend to try some of the other suggestions as my skills improve. Bye.

---

### Post by stani on 2007-09-10
To resize photos and apply effects, try out Phatch = Photo and Batch! It designed to be very user friendly. For more info and an easy deb installer, look here:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

---

### Post by chinasteve2000 on 2007-11-20
> **FreddyGill said:**
> I installed the "nautilus-image-converter" from the synaptic program and it works great! I'm not familiar with using ubuntu's command line stuff yet, so I went with easy for now, Thank you very much for helping me. I intend to try some of the other suggestions as my skills improve. Bye.
[COLOR="Blue"]
That's great! I want that converter...and I've installed it. Do I need to restart nautilus to be able to use it or something? I am not seeing the options that Synaptics offers:[/COLOR]

> **nautilus extension to mass resize images**
Adds a "Resize Images..." menu item to the context menu of all images.
This opens a dialog where you set the desired image size and file name.
A click on "Resize" finally resizes the image(s) using ImageMagick's
convert tool.

[COLOR="Blue"]Any suggestions?[/COLOR]

---

