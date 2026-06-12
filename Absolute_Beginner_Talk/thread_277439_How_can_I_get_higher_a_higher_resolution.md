---
title: "How can I get higher a higher resolution?"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-10-14
Can someone tell me how to get my resolution up to 1280*1024. My monitor can take this but the highest I can take is 1024*768 in ubuntu. 

I have an ati 9200 graphics card. *sigh*

---

### Post by ReaderRat on 2006-10-14
> **jincast90 said:**
> Can someone tell me how to get my resolution up to 1280*1024. My monitor can take this but the highest I can take is 1024*768 in ubuntu. 

I have an ati 9200 graphics card. *sigh*
For your information:
Resolution (& Refresh Rate) HOWTO Change
         [http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)
ATI - How to install the drivers          [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by jincast90 on 2006-10-15
> **ReaderRat said:**
> For your information:
Resolution (& Refresh Rate) HOWTO Change
         [http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)
ATI - How to install the drivers          [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

The way I understand it this guide is for people who cannot change their refresh rate and resolution. I can do both I just can not get it up to the resolution my screen can use which is 1280*1024.

---

### Post by jorn on 2006-10-15
Is the resolution 1280*1024 available in your /etc/X11/xorg.conf ?

---

### Post by meborc on 2006-10-15
> **jincast90 said:**
> Can someone tell me how to get my resolution up to 1280*1024. My monitor can take this but the highest I can take is 1024*768 in ubuntu. 

I have an ati 9200 graphics card. *sigh*

try```
sudo dpkg-reconfigure xserver-xorg
```answer the questions... if you are not sure, leave the default answer... when you get the resolution menu chose the resolutions your monitor supports... after that it should all work...

---

### Post by ckonrad on 2006-10-15
> **jincast90 said:**
> Can someone tell me how to get my resolution up to 1280*1024. My monitor can take this but the highest I can take is 1024*768 in ubuntu. 

I have an ati 9200 graphics card. *sigh*

try out this solution
[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

that worked great for me.

---

### Post by jincast90 on 2006-10-15
> **jorn said:**
> Is the resolution 1280*1024 available in your /etc/X11/xorg.conf ?

I just opened the document and made a search for 1280. There was nothing, So I guess it is not available in my xorg.conf

---

### Post by jincast90 on 2006-10-15
> **ckonrad said:**
> try out this solution
[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

that worked great for me.

Well Im not on breezy, I am on Dapper. Does it make any difference?

---

### Post by jorn on 2006-10-15
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by meborc on 2006-10-15
you have 2 options... run the command i posted earlier... or manually edit xorg.conf... ;) trust me... USE THE COMMAND... it will modify the xorg.conf to the appropriate resolution...

---

### Post by jincast90 on 2006-10-15
> **jorn said:**
> [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Yeah I found that guide.. And it worked!!! Now could anyone point me to a guide to install beryl with my ati radeon 9200?

---

### Post by meborc on 2006-10-15
> **jincast90 said:**
> Yeah I found that guide.. And it worked!!! Now could anyone point me to a guide to install beryl with my ati radeon 9200?

see this thread [http://ubuntuforums.org/showthread.php?t=265678](http://ubuntuforums.org/showthread.php?t=265678) and scroll down for POST NR 7 ;)

---

### Post by ReaderRat on 2006-10-15
> **jincast90 said:**
> The way I understand it this guide is for people who cannot change their refresh rate and resolution. I can do both I just can not get it up to the resolution my screen can use which is 1280*1024.
I, myself, am a newbie, so I have about run out of suggestions.
Can you just adjust the resolution with the controls on the monitor? (temp fix)

---

### Post by jincast90 on 2006-10-15
> **ReaderRat said:**
> I, myself, am a newbie, so I have about run out of suggestions.
Can you just adjust the resolution with the controls on the monitor? (temp fix)

If you look up about 3 posts you will se I have figured it out.

---

