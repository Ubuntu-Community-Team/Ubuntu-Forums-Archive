---
title: "[SOLVED] encrypted dvds wont play with gxine"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Cobbs on 2007-08-04
Okay, I am completely new to using linux and ubuntu so I am struggling to get my bearings and understand my new OS.  I am really happy with it so far though! 

I have been reading the other posts similar to mine in the forums but I have not been able to fix my problem yet.  I have tried this fix already:

~~~~~~~
Install the following packages from the “Universe” and “Multiverse” repositories (see Add Applications):	
    * gxine
    * libdvdcss2
    * libdvdnav4
    * libdvdplay0
    * libdvdread3

Click Applications &#8594; Accessories &#8594; Terminal and type the following into the screen which appears, followed by the Return key:
sudo /usr/share/doc/libdvdread3/install-css.sh

Press System &#8594; Preferences &#8594; Removable Drives and Media and click on the Multimedia tab.
In the Command box under Video DVD Discs, type “gxine -S dvd:/” (without quotes) and then press Close.

Insert a DVD disc into the DVD drive of your computer. It should play automatically in gxine. You can press the f key to watch the DVD full-screen.
~~~~~~~~~~~~~~~

However, when the program starts and tries to run the DVD, I get this error: "The xine engine failed to start.  No demuxer found - stream format not recognised"

I am at a complete loss of what to do now, and I am afraid that I might mess stuff up by continuing to try different suggestions from other posts.  Any help would be greatly appreciated!  I am running Ubuntu 7.04 on an Acer Travelmate 2480 2943.

Thank you and if you need more info or I left something out, let me know.

---

### Post by apswartz on 2007-08-04
Ok, good, you've already done a lot. I take it you check out the RestrictedFormats doc?
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And that you have installed the Medibuntu repositories for the codecs, etc.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you have done all of that, how about this...
1. Can you play other commercial DVDs?

2. Does it work in another Video Player, e.g. vln (videolan)?

If it turns out to be that one DVD, what is the title?

---

### Post by Cobbs on 2007-08-04
Yes, I have installed the RestrictedFormats package but I have not installed the Medibuntu stuff.  I had linked to the site from another post but I was unsure on what/how to install it.  Am I supposed to install the entire repository or just libdvdcss2?

I tried Casino Royal and Lucky # Slevin and both stopped with the same error msg.

---

### Post by apswartz on 2007-08-04
Yes, follow the install instructions further down this page...
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and follow their advice on getting DVDs to work.

---

### Post by Cobbs on 2007-08-04
I fixed it by installing videolan.  I was able to play the DVDs after doing that.  Thank you apswartz!!

:popcorn:

---

