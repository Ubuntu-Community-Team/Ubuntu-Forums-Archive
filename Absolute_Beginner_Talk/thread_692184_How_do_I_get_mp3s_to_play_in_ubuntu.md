---
title: "How do I get mp3s to play in ubuntu?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by nydadx1x on 2008-02-09
I installed ubuntu about a year ago and was able to find the answers I needed with the help of you kind people.  I have intalled it on another computer and can't remember anything especially how to play mp3s and movie files.  Can someone direct me to the posts where it explains in detail how to install what I need to play my mp3 and avi files?

Thanks to all

---

### Post by halitech on 2008-02-09
which version did you install? will make a difference on where to go to install what you need.

---

### Post by nydadx1x on 2008-02-09
Sorry, I don't know...ubuntu 6.something???  It's from a disk I burned a year ago

---

### Post by jan quark on 2008-02-09
have a look here

[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by lolzlolz on 2008-02-09
```
sudo apt-get update
```
it will install all the latest files
then 
```
sudo apt-get install mplayer
``` 
:) should work
will take a long time ot upgrade to 7.10

---

### Post by halitech on 2008-02-09
probably 6.06 then but could be 6.10 as well.

I think with both of those you need to enable the multiverse repository in order to install the needed codecs.

---

### Post by nydadx1x on 2008-02-09
Thanks, but so far no help.  It's unbuntu 6.06 btw.

---

### Post by nydadx1x on 2008-02-09
> **halitech said:**
> probably 6.06 then but could be 6.10 as well.

I think with both of those you need to enable the multiverse repository in order to install the needed codecs.
How do I enable multiverse repsoitory?

---

### Post by halitech on 2008-02-09
open Synaptic (System - Admin - synaptic package manager) then go to Settings repositories

follow the rest from here:

[https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9](https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9)

---

### Post by nydadx1x on 2008-02-09
> **lolzlolz said:**
> ```
sudo apt-get update
```
it will install all the latest files
then 
```
sudo apt-get install mplayer
``` 
:) should work
will take a long time ot upgrade to 7.10
got error message: E: Couldn't find package mplayer

---

### Post by jan quark on 2008-02-09
you probably have to enable the sources 

run this

```
cat /etc/apt/sources.list
```

and post the result


you can edit the source-list file with this commadn


```
gksudo gedit /etc/apt/sources.list
```

---

### Post by HappyFeet on 2008-02-09
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
then try to download mplayer again.

---

### Post by buntu_Geek on 2008-02-09
I think this could be an easy way....

Try to open any mp3 music file using any of the media players you have.. ( Totem must be available by default)

It would ask whether to search for the codec... give yes...

A new window would appear and ... select all the packages.. and install them....

Hope it works ....( i dont have that much experience with Dapper.. )

---

### Post by nydadx1x on 2008-02-09
I got mplayer installed, thank you.  It still doesn't play my mp3s though

---

### Post by jan quark on 2008-02-09
you need to download the codecs to be able to run mp3

run this in terminal
```

sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Shin_Gouki2501 on 2008-02-09
the player is not perfect but IF u have java isntalled this should work(without mp3 codecs ;):
[http://www.javazoom.net/jlgui/jlgui.html](http://www.javazoom.net/jlgui/jlgui.html)

---

### Post by nydadx1x on 2008-02-09
> **buntu_Geek said:**
> I think this could be an easy way....

Try to open any mp3 music file using any of the media players you have.. ( Totem must be available by default)

It would ask whether to search for the codec... give yes...

A new window would appear and ... select all the packages.. and install them....

Hope it works ....( i dont have that much experience with Dapper.. )Sorry it doesn't prompt me to search for the codec.

---

### Post by nydadx1x on 2008-02-09
> **jan quark said:**
> you need to download the codecs to be able to run mp3

run this in terminal
```

sudo apt-get install ubuntu-restricted-extras
```

Where do I find the codecs?

---

### Post by nydadx1x on 2008-02-09
I can play mp3s and AVI's in totem (movieplayer) on my older ubuntu computer, but for the life of me can't remember how I got it to work.

---

### Post by Shin_Gouki2501 on 2008-02-10
i repeat again: have u installed java?!
If so dowload this jar:
[http://www.javazoom.net/jlgui/jlgui.html](http://www.javazoom.net/jlgui/jlgui.html)
and use it as mp3 player nothing else needed ;)

---

