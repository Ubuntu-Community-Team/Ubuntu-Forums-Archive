---
title: "convert avi"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by not_yet on 2007-01-26
I have a 640 x 480 avi, and I'd like to convert it to 320 x 240

is there an app that can do that?

thanks

---

### Post by Marsolin on 2007-01-26
Any video editor should be able to do that.  I suggest [Avidemux]("http://linuxappfinder.com/package/avidemux").  It simple to use and in the ubuntu repos.

After you load Avidemux, open the file you want to resize. If you don't want to change the encoding, leave the Video and Audio codecs set to Copy and select Filters from the Video menu. Click Add and you should see MPlayer Resize as the second option in the list. Select it, enter in the size you want, and click OK. The only thing left to do then is press Save, pick a filename, and let Avidemux do its thing.

---

### Post by petehall on 2007-02-03
> **Marsolin said:**
>  If you don't want to change the encoding, leave the Video and Audio codecs set to Copy and select Filters from the Video menu.

I found that if I left the Video codec as "Copy" then the filters wouldn't be applied. I had to choose something else from this dropdown before it would do anything.

---

