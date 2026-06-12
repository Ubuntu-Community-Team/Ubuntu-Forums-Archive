---
title: "Flash - What is the deal???"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by cybertron3000 on 2008-01-28
I tried every flash add-on in the add/remove, and it still doesn't work on various websites.  I also can't play a dvd with Totem.  All this stuff works fine on Windows.  Ubuntu is great, but "small" issues like this is adding up.

---

### Post by Pandemic187 on 2008-01-28
I would suggest getting Flash from Adobe's site. Although you must use the terminal to install it, doing so is very, very easy. Get the .tar.gz from the following site:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

Simply unpack the .tar.gz (right-click and "Extract Here"). Simply change diretories (cd /Desktop/flashplayer for example) to where the folder you have unpacked the .tar.gz to, then run:
```
./flashplayer-installer
```
And that's it! If this is at all confusing just let me know. I realize this is not the way you were trying to install it but this way should work.

---

### Post by shae on 2008-01-28
Fix for Flash:[http://ubuntuforums.org/showthread.php?p=3923465]("http://ubuntuforums.org/showthread.php?p=3923465")

To get DVD decodeing: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by billgoldberg on 2008-01-28
Yeah, installing the .tar.gz from adobes site should work (just as you had to do in windows).

You however don't need any terminal commands to install it. Right-click it, extract. In the folder look for the installer. Double click it. And then run in terminal (it could have a gui installer, never tried it.

Dvd support isn't standard included (just as it wasn't in win xp).

There are lot's of ways to install dvd support but the easiest thing is to install [this little script]("http://ubuntuforums.org/showthread.php?t=613462") that will install everything you ever need (**including flash**, dvd, java, win32 codecs, ...) and creates back-ups.

---

### Post by cybertron3000 on 2008-01-28
thanks for the flash help - the download procedure from the adobe site was effective.  i am now trying to get the dvd solution(s) to work, so far unsuccessful

---

### Post by emarkd on 2008-01-28
As to your original question, the "deal" with flash, as with your dvd trouble, all comes down to the licensing requirements of those softwares.  Ubuntu tries very hard to be a completely free (as in freedom) operating system but still allow people who are willing to give up a bit of that freedom to install certain non-free bits.  Like flash or dvd css decoding.  Sometimes this can be done easily, sometimes its a little bit harder or possibly even illegal.

As to your DVD question, did you try installing VLC and playing DVD's from there?  It usually works quite well.

---

### Post by wolfen69 on 2008-01-28
this page [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) can also help you get DVD's working.

---

### Post by cybertron3000 on 2008-01-28
the quick save dvd
 solution worked - thanks

---

### Post by cybertron3000 on 2008-01-28
My faith in Ubuntu is restored thanks to you all.  Don't really need DVD movie playback - that is what a DVD player or game system is for.  My biggest thing was to let my kids play their educational games that require flash.  I really do think Ubuntu is a lighter and snappier OS!

---

### Post by Pandemic187 on 2008-01-28
> **billgoldberg said:**
> Yeah, installing the .tar.gz from adobes site should work (just as you had to do in windows).

You however don't need any terminal commands to install it. Right-click it, extract. In the folder look for the installer. Double click it. And then run in terminal (it could have a gui installer, never tried it.
Ah yes, I didn't think of doing it that way (although I'm pretty sure the readme instructs users to use the terminal command).

---

