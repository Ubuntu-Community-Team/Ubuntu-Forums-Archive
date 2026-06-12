---
title: "How to search?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-11-27
I have ten folders, each with mp3 files, and each folder has some jpg files in it. I want to rename those jpg files(to Cover.jpg). I don't want to open every folder, but I want to search those folders to find and show only the jpg files. I have tried Ctrl + F and add *.jpg(and hit enter), but then it searches all my folders in mye home folder. How can I search just those ten folders? 

In Windows I would just right click the main folder witch contains those ten folder and choose «search» and type in *.jpg. Is this possible in Nautilus? 

Thanks

---

### Post by linuxisfree on 2007-11-27
> **_sAm_ said:**
> I have ten folders, each with mp3 files, and each folder has some jpg files in it. I want to rename those jpg files(to Cover.jpg). I don't want to open every folder, but I want to search those folders to find and show only the jpg files. I have tried Ctrl + F and add *.jpg(and hit enter), but then it searches all my folders in mye home folder. How can I search just those ten folders? 

In Windows I would just right click the main folder witch contains those ten folder and choose «search» and type in *.jpg. Is this possible in Nautilus? 

Thanks

Hi _sAm_ ! Try changing the setting of the "look in folder" (its in places - search for files) to the folder which contains your 10 folders and then search for *.jpg from there.

(Hope that helps) :)

---

### Post by Keith Hedger on 2007-11-27
I had to do a similar thing and wrote this quick script to convert the album art jpgs in my nusic folder:
#!/bin/sh
find -iname "albumart.jpg" -o -iname "cover.gif" -o -iname "cover.png" | while read file
	do
	echo "$file"
	convert "$file" -thumbnail 130x130 "${file%/*}"/cover.bmp
done
This also converts the size (for use in rock box) if you dont want to do a conversion use mv to just rename the files

---

### Post by _sAm_ on 2007-11-27
Thanks both for your answers!

I didn't know about the "look in folder", but it dosnt help much cus you cant change to the «working folder». That means I have to browse to the folder I am working on each time in it, even though I have all ready opened it. I really like Nautilus, I find it much better then the one in windows – but this was not good at all. Perhaps there is a plugin that will fix this, I will try to Google it. 

Thanks again:-)

---

### Post by mahiyar on 2007-11-27
linuxisfree advice is perfectly correct go to >main menu> places > search for files, there you will get the option which linuxisfree describes.

---

### Post by _sAm_ on 2007-11-27
My point was this; 

Lets say I open Nautilus and go to my «Multimedia» partition, then «Music folder», then the «Faith No More» folder, and here I decide to check if all the front cover pictures are named «Cover.jpg».

In Windows I could just right click and search for *.jpg – fast and easy. 

In Linux(so far) I would _then_ need to go to places > «Search for files», change «look in folder» to «other,» then browse(again) to «Multimedia», »Music» and finally «Faith No More». Thats 6 more clicks then in Windows. And the same next time and so on, and I use the search function quite often. 

I have now checked Thunar, and its the same. PCMan File Manager the same. 
In Gnome Commander I can search just as in Windows, but it will only display text(and not smal pictures), so that cant be used for my need. And that's the file manager I know of.

Not trying to whine here _just_ to whine, just missing a option that I like.

---

