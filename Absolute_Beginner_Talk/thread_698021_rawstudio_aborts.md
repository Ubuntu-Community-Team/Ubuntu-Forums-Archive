---
title: "rawstudio aborts"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-02-15
I am running Feisty and just used synaptic to install rawstudio.  The rawstudio version it installs just aborts.  If I run it in the command line without a raw file name it aborts, if I add the raw file name it aborts, if I go through "places" and click on the raw file it aborts.

What's up with that?  The version in synaptic, which we are usually told to use, doesn't work?

Any help would be greatly appreciated!  :)

---

### Post by Tatty on 2008-02-15
Are there any errors given in the terminal when you run it from there?

---

### Post by anewguy on 2008-02-15
Here's the terminal output - first without a raw file name, 2nd with a raw file name.  If it helps any, the rawstudio screen opens up, show progress 0/1 then disappears each time. 

dave@dave-desktop:~/pv2_pics/2008.02.15_06.53.33PM$ ls
IMG_0060.RAW
dave@dave-desktop:~/pv2_pics/2008.02.15_06.53.33PM$ rawstudio

(rawstudio:11401): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed

(rawstudio:11401): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(rawstudio:11401): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `pixbuf != NULL' failed

** ERROR **: file rs-image.c: line 547 (rs_image16_free): assertion failed: (rsi->pixels!=NULL)
aborting...
Aborted (core dumped)



dave@dave-desktop:~/pv2_pics/2008.02.15_06.53.33PM$ rawstudio IMG_0060.RAW

(rawstudio:11416): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `height > 0' failed

(rawstudio:11416): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(rawstudio:11416): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `pixbuf != NULL' failed

** ERROR **: file rs-image.c: line 547 (rs_image16_free): assertion failed: (rsi->pixels!=NULL)
aborting...
Aborted (core dumped)
dave@dave-desktop:~/pv2_pics/2008.02.15_06.53.33PM$ 


Thanks! :)

---

### Post by anewguy on 2008-02-15
bump.

---

### Post by anewguy on 2008-02-15
Tried downloading from the rawstudio site - it won't compile (the configure fails).

HELP!!  I really need to be able to process raw images.  Downloaded Picasa, but it apparently doesn't work with raw images.

:(

---

### Post by anewguy on 2008-02-16
bump.

---

### Post by anewguy on 2008-02-18
bump.

---

### Post by anewguy on 2008-02-23
One more bump - surely since this is from the normal repositories and I loaded it via Synaptic, I can't be the only person with this problem!

---

### Post by Anders Kvist on 2008-04-29
Do you still have problems?

You could contact us directly on the rawstudio mailing lists or submit a bugreport, then we'll get the message and see that someone has a problem, allowing us to help fixing it :)

/Anders Kvist
Rawstudio developer

---

