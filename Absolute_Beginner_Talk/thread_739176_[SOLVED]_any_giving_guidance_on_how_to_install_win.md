---
title: "[SOLVED] any giving guidance on how to install win32 codecs?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by bhadotia on 2008-03-29
there is wiki giving guidance on how to install all the software so that one can play all types of media files on ubuntu; it was something like medibuntu , i have lost the link to it . can some one help me by giving me the exact link. thanks.:(

---

### Post by forestpixie on 2008-03-29
here it is
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

this is what you need to do in terminal
```
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
```
sudo apt-get install w32codecs
```

---

### Post by bumanie on 2008-03-29
> sudo gedit /etc/apt/sources.list
Add this to your sources list 
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free 
then sudo apt-get install w32codecs

---

### Post by mcduck on 2008-03-29
[http://www.medibuntu.org/]("http://www.medibuntu.org/")

Just follow the Repository-Howto on their site, and then you can install w32codecs with the package manager just like any other packages.

---

### Post by bhadotia on 2008-03-29
actually the wiki i am talking about is from a site other than medibuntu (i think ; actually i don't remember perfectly)  it was posted by some person named simon -or s--something and is very comprehensive - it first explains how to install various universal media players (vlc , xine , etc.) then it tells about how to install various codecs (including win32) and adding and updating repo's.

---

### Post by bumanie on 2008-03-29
You're probably looking for this.
[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by bhadotia on 2008-03-29
sorry ! thats not it. any other suggestions (plz!).

---

### Post by bumanie on 2008-03-29
Follow forestpixie's post and then return to the guide I gave you. It tells you how to install players, codecs + many more things. Finding the exact same guide is less important than getting your system up and running properly. If you look on the internet there are heaps of guides, finding theone you saw before might be like looking for a needle in a haystack.

---

### Post by Duck2006 on 2008-03-29
You may/or may not find what your looking for here.

[http://www.ubuntuhq.com/wiki/index.php/Ubuntu_Howtos](http://www.ubuntuhq.com/wiki/index.php/Ubuntu_Howtos)

---

### Post by waspbr on 2008-03-29
btw are there any medibuntu repos for hardy already?

---

### Post by forestpixie on 2008-03-29
yea - at the bottom of this post - I would guess that once it's sorted properly this will stop working though.

[http://ubuntuforums.org/showpost.php?p=4439914&postcount=1](http://ubuntuforums.org/showpost.php?p=4439914&postcount=1)

---

### Post by bhadotia on 2008-03-29
hey guys ! , guess what i found the exact link it this (check it out, its amazing):


[HTML]http://tuxenclave.wordpress.com/2008/01/03/how-to-enable-multimedia-suport-in-ubuntu-710/[/HTML]

 any way , thanks for all the help and tolerating me!:guitar::lolflag:

---

