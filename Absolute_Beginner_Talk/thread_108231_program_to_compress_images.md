---
title: "program to compress images"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by matog on 2005-12-25
I´m looking for a program to compress image in a simple way. Something like the IrfanView in Window$. Click, open and compress, simple.

Do an equivalent program exist in linux?

TIA!

---

### Post by ninotob on 2005-12-25
You could use "gimp".  Open your file, choose "save as" and you are given a slider bar to indicate the compression level.  You can also resize it (image-resize).

There are command line tools as well in the imagemagick set of tools.  Before turning away from the CLI, note that you can process hundreds of files with almost no effort using the CLI.  For one file, it works like this:

convert [COLOR="DarkRed"]-quality 50[/COLOR] [COLOR="DarkSlateBlue"]filename.jpg[/COLOR] [COLOR="DarkGreen"]reduced_filename.jpg[/COLOR]

-The red section of the command:  indicate quality level from 0 - 100 where 0 is worst, 100 best.
-The purple part is the name of the file you want to modify.
-the green part is the name of the file you want to generate, in this instance, the compressed picture.

If you have a bunch of pictures, you could do this on the command line to automatically change all the pictures.  In other words, if you have a 100 pictures, opening each file and saving it at a different compression level would be slow and boring.  This method does it all at once with almost no user input.   You have to use "cd" to get to the directory that the pictures are in.  Then enter:

```

for i in *.jpg; do convert -quality 50 $i reduced_$i; done

```

If your pictures are not "jpg", replace jpg with the proper extension.  Set the "-quality 50" to a different level if you want.  The "reduced_" is prepended to the filenames for the compressed pics -- change it to whatever you want if you don't like that lable.

---

### Post by ninotob on 2005-12-25
BTW, "convert" can do more than compression.  Resizing, cropping, rotating, and million other things I don't even understand.  Check it out:

[http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

---

### Post by kaamos on 2005-12-25
Whoa, this is good info. Thanks ninotob.

---

### Post by matog on 2005-12-25
Great!!! Thanks!!!!

---

### Post by ninotob on 2005-12-25
Thank you. ;-)

It occurs to me that there is a potential area of confusion in my CLI command above.  If your picture filenames have spaces in them, it will cause problems and things won't work right.  To remedy the situation, you could change all spaces in the filenames to "_" like this:

```

for i in *.jpg; do mv "$i" `echo $i | tr ' ' '_'`; done 

```

Again, use "cd" to go to the directory with your files and change the "*.jpg" to indicate whatever filetypes/extension is appropriate.

So, if you had a file called "vacation picture.jpg", the line above would change the name to "vacation_picture.jpg".  After you eliminate spaces, then run the convert command in my first post.

---

### Post by matog on 2005-12-26
I&#180;ve been looking the imagemagick page, and I saw a lot of GUI. Which is the best?

Thanks!

---

