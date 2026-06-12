---
title: "New to Ubuntu again(this time I will lear it ;-)"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by marshaller on 2007-11-23
I have now installed ubuntu 7.10 on an old toshiba laptop, everything is working, I want that fore running a weather station with a program kalled open2300, but have to learn howto downloading, unpack an install it.(please give a hint if you know about it)
I have odred another laptop to run everything else. its testet with ubuntu so it will be nice.
I have another problem i have a lot of music on a external harddisk, but a lot of it is wma files, I want to change them to mp3, is there a program that can change that, I mean look in the maps fore wma, change it to mp3, and dellete the wma. it about 2000 songs so i dont want to do it one by one.
I also ordered a book about ubuntu linux, but i have no pation so hope to here some sugestion from u.

---

### Post by Ub1476 on 2007-11-23
First download open2300 here (.tar.gz fil): [http://www.lavrsen.dk/twiki/bin/view/Open2300/DownloadFiles](http://www.lavrsen.dk/twiki/bin/view/Open2300/DownloadFiles)

Unpack the file and open a terminal.

```
cd name of the open2300 unpacked folder
make
make install
```

Hope that helps:)

---

### Post by ZipoTe on 2007-11-23
Here it is a how-to: [http://ubuntuforums.org/showthread.php?t=37793&highlight=change+wma+mp3]("http://ubuntuforums.org/showthread.php?t=37793&highlight=change+wma+mp3")

Some search before asking gives you a faster answer ^^

---

### Post by catfishk on 2007-11-23
here's a good script to convert wma files to mp3.  i think it does it recursively, so you can just run it in a directory full of wma files and it will go to town.  however, i converted all mine already so i can't try!  you will need lame and mplayer installed, and to pop this in /usr/bin (call it wma2mp3 or something and make sure it is executable by chmod +x /usr/bin/wma2mp3, for example):

 >  #!/bin/bash
#
# Convert wma files to mp3

current_directory=$( pwd )

#remove spaces
for i in *.wma; do mv "$i" `echo $i | tr ' ' '_'`; done

#remove uppercase
for i in *.[Ww][Mm][Aa]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

#Rip with Mplayer / encode with LAME
for i in *.wma ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm -waveheader $i && lame -m s audiodump.wav -o $i; done

#convert file names
for i in *.wma; do mv "$i" "`basename "$i" .wma`.mp3"; done

rm audiodump.wav


 i did not write this script.  many thanks to whomever did, because it is one of my favorites :)

---

### Post by marshaller on 2007-11-23
Thank you all
now i have some hint to go fore.
To zipo te I have been searching, but have not finding a program/script that changing all files at once
I will now try to use the ideas
Thank you again

---

