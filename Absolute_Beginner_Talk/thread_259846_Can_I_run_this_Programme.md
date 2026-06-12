---
title: "Can I run this Programme????"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by kcgreg on 2006-09-17
Hi Guys,

I would like to run this game on Ubuntu - can it be done?

The link for this game is found here:

[http://sourceforge.net/project/showfiles.php?group_id=139550&package_id=159434&release_id=393118](http://sourceforge.net/project/showfiles.php?group_id=139550&package_id=159434&release_id=393118)

Can someone please direct me step by step so that I can do it from here on???:confused: 

Many thanks,

Kcgreg

---

### Post by Najand on 2006-09-18
Simply download it and ectract it to ypur destination directory and then run brutalchess from the source directory.

---

### Post by kcgreg on 2006-09-18
> **Najand said:**
> Simply download it and ectract it to ypur destination directory and then run brutalchess from the source directory.

How do I do this please??? I am fres at this, about 6 days!!!:confused:

---

### Post by ncappel1 on 2006-09-18
Maybe this link will be of help to you now and for the future!
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

In case you want another site, aysiu wrote a nice page too: 
[http://www.psychocats.net/linux/installingsoftware](http://www.psychocats.net/linux/installingsoftware)

let us know if you have more problems!

---

### Post by Kilz on 2006-09-18
The program needs to be compiled into a executable. You will also need to have freetype, libsdl1.2, libsdl1.2-dev, libsdl-image1.2-dev, and libsdl-image1.2 installed to compile it. 
Once you have them installed, extract the zip file to the desktop. Open a terminal type in 
```
cd ~/Desktop/brutalchess-alpha-0.3
```
then 
```
make
```
Theis will make the executable. There is no installer as its a alpha, but you can click on the brutalchess executable that it will make and start the game.

---

### Post by catlett on 2006-09-18
Something is not compatable but maybe you'll have better luck, here are the directions.
Download the tar.gz file. You can download it to your desktop, home folder, opt or any folder you want to hold it. When the file is done, right click on it and select 'extract here'. That will give you a folder.
You need to enter the folder 'virtually' in the terminal. It is done by entering cd and then the path. This is the path I had, you may not have it on your desktop and you need to replace my name with your username 
```
 cd /home/tj/Desktop/brutalchess-alpha-0.3
```
Once you are in the folder, you are supposed to enter```
 make 
```That is supposed to run and then you would enter brutalchess from that directory and it would run. I had errors returned when running make so it did not setup the game. Maybe you will get lucky and it will woprk for you.
```
catlett@ubuntu:~/Desktop/brutalchess-alpha-0.3$ make
g++ -g -O2 `sdl-config --cflags` `freetype-config --cflags` -c brutalchess.cpp -o brutalchess.o
/bin/sh: sdl-config: command not found
/bin/sh: freetype-config: command not found
brutalchess.cpp:22:17: error: SDL.h: No such file or directory
In file included from brutalchess.cpp:24:
glhead.h:2:24: error: SDL_opengl.h: No such file or directory
In file included from brutalchess.cpp:26:
fontloader.h:18:22: error: ft2build.h: No such file or directory
fontloader.h:19:10: error: #include expects "FILENAME" or <FILENAME>
```The errors go on for a while but that will give you the gist of it. Maybe someone else has experience with brutal chess

---

### Post by Kilz on 2006-09-18
> **catlett said:**
> Something is not compatable but maybe you'll have better luck, here are the directions.
Download the tar.gz file. You can download it to your desktop, home folder, opt or any folder you want to hold it. When the file is done, right click on it and select 'extract here'. That will give you a folder.
You need to enter the folder 'virtually' in the terminal. It is done by entering cd and then the path. This is the path I had, you may not have it on your desktop and you need to replace my name with your username 
```
 cd /home/tj/Desktop/brutalchess-alpha-0.3
```
Once you are in the folder, you are supposed to enter```
 make 
```That is supposed to run and then you would enter brutalchess from that directory and it would run. I had errors returned when running make so it did not setup the game. Maybe you will get lucky and it will woprk for you.
```
catlett@ubuntu:~/Desktop/brutalchess-alpha-0.3$ make
g++ -g -O2 `sdl-config --cflags` `freetype-config --cflags` -c brutalchess.cpp -o brutalchess.o
/bin/sh: sdl-config: command not found
/bin/sh: freetype-config: command not found
brutalchess.cpp:22:17: error: SDL.h: No such file or directory
In file included from brutalchess.cpp:24:
glhead.h:2:24: error: SDL_opengl.h: No such file or directory
In file included from brutalchess.cpp:26:
fontloader.h:18:22: error: ft2build.h: No such file or directory
fontloader.h:19:10: error: #include expects "FILENAME" or <FILENAME>
```The errors go on for a while but that will give you the gist of it. Maybe someone else has experience with brutal chess


I compiled it after reading the install file and adding the packages I listed in my previous post.

---

### Post by catlett on 2006-09-18
> **Kilz said:**
> I compiled it after reading the install file and adding the packages I listed in my previous post.

I didn't see you post, I hit reply and instead of just saying how to cd etc, I decided to download and try the package, I got errors and posted them in the reply. Only after sending the reply did I see your post.

---

### Post by Kilz on 2006-09-18
> **catlett said:**
> I didn't see you post, I hit reply and instead of just saying how to cd etc, I decided to download and try the package, I got errors and posted them in the reply. Only after sending the reply did I see your post.

Cross posts happen. :biggrin:

---

