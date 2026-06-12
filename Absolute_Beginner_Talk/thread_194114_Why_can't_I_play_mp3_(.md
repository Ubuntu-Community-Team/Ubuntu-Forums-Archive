---
title: "Why can't I play mp3 :("
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by madu on 2006-06-11
Hi guys..

I folowwed the guide here: [http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs)

and installed the codecs. And t hen I installed XINE. And then I install Win32 from Synaptic. I followed this too: [http://ubuntuforums.org/showthread.php?p=1057180#post1057180](http://ubuntuforums.org/showthread.php?p=1057180#post1057180)

But no matter what, I cant play mp3: I get this error in Totem and Xine:
**Audio codec 'MPEG 1 Layer 3 CBR' is not handled. You might need to install additional plugins to be able to play some types of movies**

When trying to play WMV I get this:
**Audio codec 'Windows Media Audio v2 (win32)' is not handled. You might need to install additional plugins to be able to play some types of movies**

But I can play these with Rhythmbox with no problem. 
I followed the guide above. Why does it give me the win32 and codec errors.

Please someone help me. This bugs me why the codecs aren't working.

Thanks a lot guys..

Cheers...
 MAdu.

---

### Post by Jucato on 2006-06-11
you need to install the w32codecs. Go to this page to get the download link: [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) and scroll down to the part about Windows Media Formats

---

### Post by r3st on 2006-06-11
hmm i was able to play mp3's right after a fresh install.

---

### Post by madu on 2006-06-11
Thank you Fenyx..

I tried that link ..it worked.. Thanks a lot man.. 
The nex Ubuntu version seems quite hard to get going..
Thanks again..

Cheers..
 Madu..

---

### Post by slb33 on 2006-06-11
[QUOTE=Fenyx]you need to install the w32codecs. Go to this page to get the download link: [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) and scroll down to the part about Windows Media Formats[/QUOTE]

Not sure how you got that to happen, everytime I've installed ubuntu I had to go get all the files needed to play mp3's. :confused: 

If you follow all of the steps in the restricted format's section you should have no problems getting it to work.

---

### Post by chenel on 2007-10-20
I had this same problem and it was solved by installing 'totem-xine' and then 'libxine-ffmpeg' (the latter being the library Xine needs to decode MPEG-based format, which includes MP3).

---

