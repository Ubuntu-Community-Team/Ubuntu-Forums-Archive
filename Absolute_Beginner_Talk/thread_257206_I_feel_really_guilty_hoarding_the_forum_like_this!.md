---
title: "I feel really guilty hoarding the forum like this!!!"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by kcgreg on 2006-09-14
Hi Everyone,

Can I please get some help with loading flash player by adobe I think? The installation seems to fail and I have to manually install it - what does this mean? 

Thanking you in advance.

Cheers,

Kcgreg:confused:

---

### Post by Najand on 2006-09-14
Better to use:
```
sudo apt-get install flashplugin-nonfree
```
Than using the one in Adobe.com
It will installed the same version automatically.

---

### Post by Sef on 2006-09-14
Have you added the universe and multiverse?  If no, [click here.]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by Dinerty on 2006-09-14
**Originally created by **Artificial Intelligence**

Manually:

Download Flash from here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW)
to your Desktop.

Close your browser(s), to the terminal, batman



```
cd Desktop 
tar -zxf install_flash_player_7_linux.tar.gz 
cd install_flash_player_7_linux 
sudo sh flashplayer-installer
```


When you see this:
Quote:
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):

type: /usr/lib/mozilla-firefox

Done.

Now you need install the fonts that flash needs:



```
sudo apt-get install gsfonts-x11 
sudo fc-cache -f -v
```


Done.

---

### Post by xpod on 2006-09-14
> e: I feel really guilty hoarding the forum like this!!!

LOL.....when you`ve asked as many stupid questions as me mate THEN your hoarding the forum..:confused: :-k :???: :evil: :twisted: :-#

---

### Post by grimmson on 2006-09-14
At least your polite about it. We don't always get that, it's somehow usually our fault. Thanks for your post.

---

### Post by xpod on 2006-09-14
listen mate you`ll always get your psuedo i.t experts scoffing at your ignorance.
Ive learned that in my 6 months on a pc....but i`ll say this for THIS forum......THIS is the best one ive used in my short computing life...

And if people are being plonkers cause they think they know more than you....
Then you should be scoffing at THEIR ignorance..

They probably only come on a beginners forum to feel good about themselves and they mabey aint got much of a "REAL LIFE" outside of pc`s so you just have to make allowances for their shortcommings......THEY need more than their xlg`s,alsa`s and xconfig`s fixed........:biggrin:

---

### Post by kcgreg on 2006-09-14
You guys are awesome man!!!=D> 

I have never received so much help in my life and so quickly. Thank you all again and I am very grateful. Even my wife thinks that you guys are fantastic and she is not computer friendly - that's saying alot!

Keep up the good work guys. I am really beginning to love Linux - it is a much more "CLEAN" system and windows will have to say good bye to em forever. Hahahahahahaha!!!!!:lol: 

kcgreg

---

### Post by xpod on 2006-09-14
"killbill"

---

