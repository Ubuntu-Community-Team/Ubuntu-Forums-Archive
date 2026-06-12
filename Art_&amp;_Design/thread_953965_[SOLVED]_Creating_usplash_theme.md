---
title: "[SOLVED] Creating usplash theme"
date: 2008-10-20
forum: Art &amp; Design
---

### Post by Nonno Bassotto on 2008-10-20
I've been struggling trying to create a working usplash theme. Is there anybody here who is enough familiar with it to create it?

It should have the following logo instead of the Ubuntu one, on the same black background, and the throbber should be any shade of green from the "Ready" word.

If you don't have time but know a simple tutorial, just tell me, I wasn't able to find any.

---

### Post by smartboyathome on 2008-10-20
Is that in 256 colors? I think that is the amount of colors that Usplash allows.

---

### Post by Nonno Bassotto on 2008-10-22
Yes, but there are scripts (which don't work for me) which should automate color reduction and so on.

Anyway, here is a more complete attachment with backgrounds at 1024x768, 800x600 and 640x480, and a throbber in two colors. All files use the same 256 colors palette. I managed to obtain something which more or less works, but the throbber is out of place. Any help?

By the way, I've not been able to resize nicely the file. I should have resized it BEFORE applying the palette, but then I'm not sure that I would have obtained the same palette for all files. Is there a way to create a palette optimized for one file and apply it to other files?

---

### Post by Gannon8 on 2008-11-18
> **Nonno Bassotto said:**
> Yes, but there are scripts (which don't work for me) which should automate color reduction and so on.
Open the image in the GIMP. Go to Image > Mode. Select "Indexed" and make sure the number of colors is 256. Hit OK, then save.

Now you should have a 256 color pallet, and GIMP does a very good job of retaining the colors of the image while creating the palette.

---

### Post by volanin on 2008-11-18
Not to make an advertisement, but download this package here:

[Ubuntu Usplash Smooth]("http://gnome-look.org/content/show.php?content=93386")

I created it to enable a time-based progressbar in usplash.
If you install it, there is a VERY CLEAN usplash example source there.
It's in the directory **/usr/share/usplash-smooth**

It should help you.
Creating an usplash theme is not hard.
But the original ubuntu theme has a very messy source code.

__________________

[[IMG]http://brainstorm.ubuntu.com/idea/15741/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15741/)
__________________


_EDIT:_
Want an easy way to have the same pallette in all files?
Create a single image in true-color with the logo and both progressbars.
Then, reduce the image color to 256 colors, and cut the many parts into different files with GIMP.

---

### Post by Crafty Kisses on 2008-11-18
I can't really help you, but I wanted to say keep up the good work, it looks awesome!

---

### Post by Nonno Bassotto on 2008-11-19
I forgot to set this as solved (well, more or less). Thank you for your suggestion

---

