---
title: "mp3's to work?"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by Jakobsdillusion on 2006-03-29
I switched to ubuntu today, and I loaded my audio files onto it, why wont they work? it says I need a decoder for it or something... Im sorry to ask, I didnt think there would be prblems like these... :-?

---

### Post by Sutekh on 2006-03-29
MP3's are not a free (as in freedom) format, they are patented and restricted in the distribution of the codecs that work with them.  Ubuntu doesn't ship with support for mp3 as this could bring a lot of legal issues with it

[Ubuntu Wiki - Restricted Formats](wiki.ubuntu.com/RestrictedFormats)

Can show you how to get mp3s and other media working.

---

### Post by xXx 0wn3d xXx on 2006-03-29
[QUOTE=Jakobsdillusion]I switched to ubuntu today, and I loaded my audio files onto it, why wont they work? it says I need a decoder for it or something... Im sorry to ask, I didnt think there would be prblems like these... :-?[/QUOTE]
Ubuntu is free so it would be illegal to include copyrighted formats with it. Use automatix to install them and other commonly used programs. In terminal do:

> wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
sudo dpkg -i automatix_5.7-3_i386.deb

press enter after each line. Just copy and paste.

---

### Post by Jakobsdillusion on 2006-03-29
wow... thanks!

---

### Post by Sef on 2006-03-29
Acutally the MP3 codecs are legal in some countries and not legal in others.

---

### Post by Jakobsdillusion on 2006-03-29
alright, a new question, my ubuntu computer cannot connect to the internet, where can I download these files?

---

### Post by roseynose on 2006-03-29
[QUOTE=Sef]Acutally the MP3 codecs are legal in some countries and not legal in others.[/QUOTE]

I know for sure that in the USA that MP3s open for decoding (Ie listening to the mp3 files). Unfortunately, it's the encoding process that is patented. I highly recommend working with ogg, flac, or mp2s if possible. I'd recommend lame for the mp3 encoder if you are truly in need of an mp3.

---

### Post by Jakobsdillusion on 2006-03-29
do these plugins come directly with the install disc? where can I find them to download manually?

---

### Post by Mustard on 2006-03-30
[QUOTE=Jakobsdillusion]do these plugins come directly with the install disc? where can I find them to download manually?[/QUOTE]

Doing so manually is probably not a really straightforward process and would entail a quite detailed explanation.  Practically speaking there are other methods and avenues you could go down to get a working linux installation with mp3 support.  The Ubuntu distribution is tied quite intimately to having an internet connection.  Other distributions are available that have mp3 support built in.  Ideally if you want mp3 support with ubuntu, you would get your internet connection going first.  If you can't/won't/don't want to do that, then you are probably better off getting hold of a distro that does have mp3 support built in.  You may find this a less than palatable explanation, but I think it's best to tell you the practical facts of the situation, rather than take you down a path of installing mp3 support without an internet connection, in which the process could well turn you off ever wanting to use linux again. :)  Ubuntu is not necessarily the linux distribution you want to start with.

To summarise..

1. If you want to play mp3's on ubuntu,  get an internet connection working.

2. If you can't get an internet connection working, try another distro of linux that has this stuff built-in.

3. If you don't want to do either option 1 or 2, prepare yourself for a quite convoluted process of downloading stuff on one machine, transferring it to another, and then installing locally.

---

### Post by Jakobsdillusion on 2006-03-30
Ive been wanting to use ubuntu for a long while now, Im not going to quit over one obstacle... (keeping that spirit up!) Im just going to convert all my files to .ogg

---

### Post by Mustard on 2006-03-30
[QUOTE=Jakobsdillusion]Ive been wanting to use ubuntu for a long while now, Im not going to quit over one obstacle... (keeping that spirit up!) Im just going to convert all my files to .ogg[/QUOTE]


You should keep your original mp3 format files then as a backup, as there will be a sound quality loss from the conversion to ogg.  This is just a problem with the two different formats converting one to another.

---

### Post by nanotube on 2006-03-30
skip the conversion to ogg, and do the following.
download this package with a bunch of codecs from the seveas repository:
[http://users.lichtsnel.nl/~seveas/pool/extras/w32codecs_20050412-0.0_i386.deb](http://users.lichtsnel.nl/~seveas/pool/extras/w32codecs_20050412-0.0_i386.deb)
transfer it onto your ubuntu computer by whatever means you have available (eg, usb key, cdrom, anything)
once you have it on your ubuntu comp, cd to the directory where you put the .deb file, and issue the following command from a terminal:
```
sudo dpkg -i w32codecs_20050412-0.0_i386.deb
```
this will install a whole bunch of codecs for you, mp3 included. 
have fun. :)

---

