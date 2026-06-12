---
title: "Changing file associations"
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by SnugglySoft on 2005-09-11
I want to change my file associations so that .avi's open with a different program. I've tried doing this in the GUI but I get an error along the lines of "Could not add application to the application database."

Is this a permissions-type error, where I need to be logged in as root (or use sudo in this case)? If so, how would I go about doing that?

---

### Post by GreyFox503 on 2005-09-11
I'm not sure why you're getting this error message, but I can tell you how to try it as root.  If you type

```
gksudo nautilus
```

that will open a file browser window with root privileges.  Be very careful what you do here!  That window, once open, is just like running it under the root account.  If it still gives you the same message, then it's not a permissions problem.

---

### Post by SnugglySoft on 2005-09-11
[QUOTE=GreyFox503]I'm not sure why you're getting this error message, but I can tell you how to try it as root.  If you type

```
gksudo nautilus
```

that will open a file browser window with root privileges.  Be very careful what you do here!  That window, once open, is just like running it under the root account.  If it still gives you the same message, then it's not a permissions problem.[/QUOTE]



Uhh...that was weird:

```

** Message: don't know how to handle video/x-divx, divxversion=(int)3, framerate=(double)24, width=(int)640, height=(int)272
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3, rate=(int)48000, channels=(int)2, codec_data=(buffer)010002000000800101007105totem-video-thumbnailer couln't open file 'file:///home/flugs/Movies/Blade.avi'
Reason: There were no decoders found to handle the stream, you might need to install the corresponding plugins.
** Message: don't know how to handle video/x-xvid, framerate=(double)23.975999999999999, width=(int)640, height=(int)272
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3, rate=(int)48000, channels=(int)2, codec_data=(buffer)010001000000d20101000000** Message: don't know how to handle video/x-divx, divxversion=(int)3, framerate=(double)24, width=(int)640, height=(int)272
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3, rate=(int)48000, channels=(int)2, codec_data=(buffer)010002000000800101007105
** (nautilus:12302): WARNING **: Couldn't open file:///home/flugs/Movies/Blade.avi: There were no decoders found to handle the stream, you might need to install the corresponding plugins
totem-video-thumbnailer couln't open file 'file:///home/flugs/Movies/The%20Fifth%20Element.avi'
Reason: There were no decoders found to handle the stream, you might need to install the corresponding plugins.

```



I got that after I clicked "add" in the File Manager window.


 ](*,)

---

### Post by GreyFox503 on 2005-09-11
What program are you trying to add/play these movies with?  I use xine.

To play some files (especially windows media/quicktime) files, you may need to download some extra codecs to handle them.  Ubuntu doesn't come with them because they aren't truly free (they are proprietary codecs).

For example, xine's extra codecs can be found here with instructions:  

[http://xinehq.de/index.php/faq#QUICKTIME](http://xinehq.de/index.php/faq#QUICKTIME)

I don't know if your problem is with missing codecs, but it's worth trying to solve it.

---

