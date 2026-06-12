---
title: "Extracting tar.gz files"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Ganimede on 2008-01-29
I'm new to Ubuntu and need a bit of help installing a game.  I downloaded Eschalon from [here]("http://www.basiliskgames.com/book1.htm") and found that it's a tar.gz file.  I've installed tar.gz files before but only as themes and login windows which just involved dragging and dropping.  I think that I need to extract this file with Archive Manager but I don't know where to extract it to!  Ubuntu doesn't seem to have a Program Files sort of folder!

Also, when I have installed it, how do I remove it?

---

### Post by jan quark on 2008-01-29
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

try this guide it tells you how to install things in ubuntu

---

### Post by Ganimede on 2008-01-29
> **jan quark said:**
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

try this guide it tells you how to install things in ubuntu
I've seen that page already.  It doesn't say where to extract anything to, it just says "you must first extract it somewhere. This is easily done, simply right-click on the package and select Extract Here."  When I do that, the files open up and need to go somewhere.  Where do I put them?

---

### Post by jan quark on 2008-01-29
wait I download the game now and will try to install it so I know what I say :)

---

### Post by jcwmoore on 2008-01-29
I have downloaded the demo for this game, just extract.... like you said click it and extract here...

the program is already built and ready to go, open the folder and double click the file

eschalon_book_1_demo

the loader pops up and you click "Start"

---

### Post by Ganimede on 2008-01-29
> **jcwmoore said:**
> I have downloaded the demo for this game, just extract.... like you said click it and extract here...
But does it matter where I extract it to?  At the moment, the downloaded file is in my Home folder.  Does it need to be extracted to a particular folder?

---

### Post by ftmichael on 2008-01-29
I think what people are trying to say is that you can just extract it to your Desktop, or to your Home folder, or to anywhere you want.  It will create a new directory for it within that location.  I just downloaded a different .tar.gz file to my Desktop, right-clicked it, and selected Extract Here.  It created a directory (folder) on my Desktop that has the same name as the .tar.gz file, and extracted everything into that directory.  I can move that anywhere I want, and it will run just the same.

**Someone correct me if I'm wrong about that!**

I think Ganimede's issue was that he didn't know whether things need to be installed to a specific directory - /usr/bin or what have you - because he's used to things being installed in Program Files when using Windows.  What he needed was for someone to tell him whether the files need to be manually placed in a certain directory, or whether he can indeed just stick them in a directory of their own in his Home folder, and have everything work just the same.

Also, it's worth noting that a .tar.gz file is like a .zip file - extracting the contents does not equal installing anything.  You extract the install file, and use that to install.

Michael

---

### Post by jan quark on 2008-01-29
I think it does not matter where you extract it, just try to and run the launcher

---

### Post by wolfen69 on 2008-01-29
the home folder is good. then open terminal:
```
tar -zxvf nameoffile.tar.gz
```
it will then create a folder in home.
```
cd nameofnewfolder
```
```
./nameofinstaller
```

---

### Post by jcwmoore on 2008-01-29
> **Ganimede said:**
> But does it matter where I extract it to?  At the moment, the downloaded file is in my Home folder.  Does it need to be extracted to a particular folder?

I extracted to my desktop, all the data needed for the game is extracted into the new folder, so as long as you leave everything in the extracted folder it should work just fine

---

### Post by Ganimede on 2008-02-01
I've managed to get the game all sorted.  I extracted it to my Home folder where it set up a specific folder so it didn't need installing as such at all, it just runs from there.  Now I can't wait to play it because it looks really good! :)  Thanks everyone for all your help.

---

