---
title: "[SOLVED] Online videos wont work :("
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Jakerz on 2008-01-30
Some videos, for example on YouTube, work, but are very slow and the picture doesn't go with the sound. All other sites I have tryed the videos dont work at all and dont give an error. When I try to download flash 9 it can't install for some reason, it opens as a word file. Any help would be appreciated, thanks. Oh I also read a a few things mentioning typing sudo things, I was just wondering where you type these. Thanks again

---

### Post by seventhc on 2008-01-30
How are you trying to install flash 9, and can you post a link to a site that isn't working.?

---

### Post by Flyingjester on 2008-01-30
have you tried installing flash 9 by following the instructions on adobe.com?

---

### Post by jan quark on 2008-01-30
[http://janquark.fatfreehost.com/tutorial3.html](http://janquark.fatfreehost.com/tutorial3.html)
this small guide should help you to install flash for firefox

---

### Post by Jakerz on 2008-01-30
Oo thanks ;p works now :D

---

### Post by mr_ed on 2008-01-30
About the people mentioning sudo, there should be a Terminal program under Accessories.  (I'm at work in front of a Windows machine, so that's just off the top of my head)

I tried installing flash 9 yesterday and it gave me a checksum error.  Maybe that happened to you too.

If that is the case, download the .tar.gz file from here:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)
and open up the Terminal.

Type in
```
cd Desktop
```

and that will point you to where you downloaded the file.  This assumes, of course, that you're using Firefox and you didn't change the default to where Firefox downloads files.

If that is true, next type
```
tar xzf install_flash_player_9_linux.tar.gz
```

next type
```
cd install_flash_player_9_linux
```

If you want to install system-wide, type this:
```
sudo ./flashplayer-installer
```
and then enter your password

It will prompt you to enter something along the lines of "Where's your browser install?" and in there you type
```
/usr/lib/firefox
```
They suggest /usr/lib/mozilla at that point.  Just replace "mozilla" with "firefox" and it'll be fine.
Don't forget the / in front of "usr."  It's very important!

---

### Post by jan quark on 2008-01-30
good to hear that you solved the problem
please mark this thread as solved if everything is working fine 
you do so under thread tools at the top
thank you

---

### Post by ubuntu-freak on 2008-01-30
If anyone else has problems with flash or other formats, try my easy [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
There is also a link there for flash, a deb file though (easier to install and remove than a tar).
 
Nathan

---

