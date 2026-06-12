---
title: "Audio in Videos, themes, and desktop effects."
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Pethegreat on 2008-01-13
I have 3 issues right now that i want to get fixed. None are critical, but they would make things nicer for me. 

1. Audio in Videos. I can't get audio in you tube videos or any other video right now. I have a M-audio Audiophile 192 running OSSv4 right now. I have the 192 set as my default card. I got rythmbox's audio working just fine. 

2. Themes. How to install these things confuses me. I download the file, extract it, and get the folder with the files in it. I try to put the folder in my themes folder, but it gives me a permissions error. I need either to know how to install these things, or find a way around the permissions. 

3. Desktop effects. I downloaded the stuff that I need for compiz-fusion. I go to enable it in my appearances. I click on it and I get "The composite extension is not avalable" I have an  x1650 running the latest ATI drivers.

---

### Post by ubuntu-freak on 2008-01-13
You can install themes using system>preferences and opening appearances. 
 
Try my how-to for multimedia
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

And this one for sound
   
 [http://ubuntuforums.org/showthread.php?t=590989&highlight=flash+sound](http://ubuntuforums.org/showthread.php?t=590989&highlight=flash+sound)

You might need the ubuntu-restricted-extras too.

And concerning your effects problem 
 
[http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)
 
Nathan

---

### Post by Pethegreat on 2008-01-13
> **reassuringlyoffensive said:**
> You can install themes using system>preferences and opening appearances. 
I am still baffled on how you install a theme. I download the tar and extract it. The installer does not recognize any of the files as a theme file. 

> 
And this one for sound
   
 [http://ubuntuforums.org/showthread.php?t=590989&highlight=flash+sound](http://ubuntuforums.org/showthread.php?t=590989&highlight=flash+sound)

You might need the ubuntu-restricted-extras too.
I get an error when trying to get pulse audio to work.
```
gcc -fPIC -shared -O2 -Wall -Werror  -lpthread -DLIBDIR=/usr/lib \
        -DALSA_INTERNAL  -DPULSEAUDIO -DLIBPULSEPATH='"/usr/lib/libpulse-simple.so.0"' -DESD -DLIBESDPATH='"/usr/lib/libesd.so.0"' \
        -DOSS -DOPENSSL -lssl  \
        flashsupport.c -o libflashsupport.so
flashsupport.c:225:17: error: esd.h: No such file or directory
flashsupport.c:290: error: expected &#8216;)&#8217; before &#8216;format&#8217;
flashsupport.c: In function &#8216;FPX_SoundOutput_Detect&#8217;:
flashsupport.c:476: error: &#8216;FPX_esd_play_stream_fallback&#8217; undeclared (first use in this function)
flashsupport.c:476: error: (Each undeclared identifier is reported only once
flashsupport.c:476: error: for each function it appears in.)
cc1: warnings being treated as errors
flashsupport.c: In function &#8216;FPX_SoundOutput_Open&#8217;:
flashsupport.c:502: warning: cast from pointer to integer of different size
flashsupport.c:514: warning: cast from pointer to integer of different size
flashsupport.c:544: warning: cast from pointer to integer of different size
flashsupport.c: In function &#8216;ESD_FPX_SoundOutput_Open&#8217;:
flashsupport.c:1251: error: &#8216;ESD_DEFAULT_RATE&#8217; undeclared (first use in this function)
flashsupport.c:1253: error: &#8216;ESD_BITS16&#8217; undeclared (first use in this function)
flashsupport.c:1253: error: &#8216;ESD_STEREO&#8217; undeclared (first use in this function)
flashsupport.c:1254: error: &#8216;ESD_STREAM&#8217; undeclared (first use in this function)
flashsupport.c:1254: error: &#8216;ESD_PLAY&#8217; undeclared (first use in this function)
flashsupport.c:1255: error: &#8216;esd_format_t&#8217; undeclared (first use in this function)
flashsupport.c:1255: error: expected &#8216;;&#8217; before &#8216;format&#8217;
flashsupport.c:1263: error: &#8216;format&#8217; undeclared (first use in this function)
flashsupport.c:1271: warning: implicit declaration of function &#8216;FPX_esd_play_stream_fallback&#8217;
make: *** [libflashsupport.so] Error 1

```

> And concerning your effects problem

[http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)
I used envy to get my drivers to work. I have the drivers enabled in the restricted driver manager.

---

### Post by ubuntu-freak on 2008-01-13
The tar doesn't need extracting by you manually. Click on 'Install' and select the theme tar.
 
Would be best to ask for help regarding sound and effects in the actual threads I found for you.
 
Hope you get it sorted.
 
Nathan

---

