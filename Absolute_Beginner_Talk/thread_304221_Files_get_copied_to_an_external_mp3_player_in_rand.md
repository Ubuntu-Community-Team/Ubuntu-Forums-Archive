---
title: "Files get copied to an external mp3 player in random order"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by zozue49 on 2006-11-21
Hi everybody, im pretty new to this OS and im having a big problem with it. No matter what, if i copy files to my mp3 player they are all unsorted when i play them. Tried Fatsort, but it segfaults ](*,) . Im using Ubuntu 6.10 (updated from 6.06). Any ideas? Thx

---

### Post by louieb on 2006-11-21
Just a wild guess, but the files a probably being copied in the order they are in on the hard disk. The file manager sorts them in alpha order before displaying the list of files.

BTW what is Fatsort? I have never heard of it. Sound like it might be useful if it worked.

---

### Post by zozue49 on 2006-11-21
What is the alpha order? Also, i dont understand what you are saying about the display order (The files are sorted by name, might that help?) Also check here for Fatsort: [http://fatsort.berlios.de/](http://fatsort.berlios.de/)

---

### Post by Daimanta on 2006-11-21
In the file manager you use you get a list of files. Those files are in a certain order. That probably means that the order the files have in the ubuntu filemanager, is the same order they are placed on your mp3-player.

---

### Post by zozue49 on 2006-11-21
I wish it was that easy xD When you have a folder of, lets say, 2 gb and want to copy it to your portable player, you drag 'n' drop it to the portable player icon on the desktop. Turns out Nautilus copies the files in a random order, and my mp3 player doesnt sort them it just plays them the order they were written.
This is driving me really mad.

---

### Post by annda on 2006-11-21
hi!

in my experience, files are just files. they are sorted by filename on all devices i've ever used and if i need a different order, i need to create playlists.

tel us exactly what your problem is, i.e. the order you've originally had (not alphabetical? was it a directory or a playlist?) and what kind of player you would like to have it reproduced on. that might help.

> 
it just plays them the order they were written

does it mean your player sorts them by the timestamp?

---

### Post by zozue49 on 2006-11-21
Ok, ill try to explain it better:

Lets say we have a parent folder and a subfolder with some mp3s:

- Parent
  -- Folder 1
     --- 101.sample.mp3
     --- 102.sample.mp3
     --- 103.sample.mp3

It is showed correctly under Nautilus (if i sort it by name, its sorted by name; if done by size, its sorted by size...)

Now, i wanna copy these folders to my pendrive-shaped Mp3 player. I drag "Parent" to the Mp3_player icon on the desktop. Nautilus copies the files in some random order (first 102.sample.mp3, then 103.sample.mp3 and finally 101.sample.mp3). As a result, when i power on the player, the playlist is:

    - 102.sample.mp3
    - 103.sample.mp3
    - 101.sample.mp3

It seems it doesnt sort the files by name, but it just reads them in the order they were copied.

The question is, is there any way i can copy the files **just with a drag n drop** (like i am used to do in Windows) or is there any other method i should use? Keep in mind my player has a 2GB capacity, so answer like "drag the files one by one" would be refreshing but not so useful.

Wow, this is a quite large post. Thx for reading :-D

---

### Post by joris1977 on 2007-01-28
I used to have the same problem, it really isn´t linux or ubuntu related cause i also had it 
with windows explorer. As far as i know there is no filebrowser that copies the files in an alphabetical order.  In windows i solved this problem with a program called ReOrganize, in linux fatsort did the trick. I´m sorry but i don´t know anything about the segfault problem. There is a nice howto about fatsort here: [http://www.ubuntuforums.org/showthread.php?t=269101&highlight=fatsort](http://www.ubuntuforums.org/showthread.php?t=269101&highlight=fatsort)

There is linux port for Reorganize but it is still a beta version and i never managed to compile it... more info see here [http://reorganize4l.sourceforge.net/](http://reorganize4l.sourceforge.net/)

---

