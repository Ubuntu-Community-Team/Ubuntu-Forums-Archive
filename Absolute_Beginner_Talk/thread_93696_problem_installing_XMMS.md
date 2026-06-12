---
title: "problem installing XMMS"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by jo2 on 2005-11-22
Hi,

I am an absolute newbie to linux and I have started to try working with Ubuntu 4.10. I want to install XMMS and I did this using Synaptic packet manger. When I open a file (mp3,wav) XMMS opens and shows some information about the file (title, length,...) but when I press Play nothing happens the programme hangs (i dont know if you say it hangs in English, it doesn't work anymore).
What do I do wrong?

Thanks,
Jonas

---

### Post by Brunellus on 2005-11-22
you probably don't have the codecs installed.  go to the wiki, go to FindPage, and search for 

RestrictedFormats

---

### Post by purdy hate machine on 2005-11-22
I had a similar problem with XMMS hanging when trying to play a file, even after instaling codecs from here [http://ubuntuguide.org/#codecs]("http://ubuntuguide.org/#codecs")

This can be resolved by changing the output plugin in XMMS

Open XMMS, > Right Click > Options > Preferences >
On the Audio I/O Plugins tab in the Output Plugin section select the &#8220;eSound&#8221; Output Plugin. > Apply > OK

---

### Post by patrick295767 on 2005-11-23
chmod 666 /dev/dsp
 
helped me for permissions !
   
--------------------
[http://www.ubuntuforums.org/showthread.php?t=64557&page=8](http://www.ubuntuforums.org/showthread.php?t=64557&page=8)

---

### Post by patrick295767 on 2005-11-23
also: 
try alsamixer 
(pressing M for un/ mute)

---

### Post by jo2 on 2005-11-23
OK, it works fine now. Thanks.

---

