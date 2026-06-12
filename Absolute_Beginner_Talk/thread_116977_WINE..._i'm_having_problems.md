---
title: "WINE... i'm having problems"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by Killerbird on 2006-01-13
Hi, windows just died on me a few days ago so I said enough is enough, so now im trying to get thie wine program to install.  I'm running the amd64 version of ubuntu...

I tried using sypnatic and followed the instructions on the wine website to the letter, and it didn't work.  It said something like it couldn't find dependicies or something like that so I decided to just download the source and compile it myself.   I used the instructions at the bottom of this webpage:
h
ttp://www.winehq.org/site/download-deb

and when i typed in "apt-get --build source wine", it started to download some more files and everything was happy and suddenly i get this error:

"checking for C compiler default output file name... configure: error: C compiler cannot create executables"

And it dies.  I need some help i'm so lost :( 

Thanks :)

---

### Post by sesstreets on 2006-01-13
wait...why are u building from source? theres nothing wrong with getting the day older version precompiled? DUH!

also make sure that you have the new repositories installed from winehq.com

---

### Post by Killerbird on 2006-01-13
I have it set up to look at these two:
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

these are not correct?

And I went with the source cause I wasn't even able to start downloading the binaries from the repositories through sypnapsis... it yelled at me :(!

---

### Post by mustang on 2006-01-13
[QUOTE=Killerbird]I have it set up to look at these two:
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

these are not correct?

And I went with the source cause I wasn't even able to start downloading the binaries from the repositories through sypnapsis... it yelled at me :(![/QUOTE]

What did it say? It'd probably be better if you solved that problem rather than going through the hassle of compiling the source.

You did remember to sudo apt-get update after you added the two links to your sources.list right?

---

### Post by Killerbird on 2006-01-14
so I add the two repositories through the sypnapse program.  I search for "wise"

I select all of the files that come up and mark them for installation.  When i press "mark" it says the following in an error box that "could not mark all packages for installation"

"
libwine:
 Depends: wine  but it is not installable

libwine-dev:
 Depends: wine-dev  but it is not installable

winetools:
 Depends: wine (>=0.0.20040914) but it is not installable
  Conflicts: xwine  but 1.0.1-1 is to be installed

"

Thanks a lot :)

---

### Post by mustang on 2006-01-14
Ok so you've modified your sources.list already. Good

Now go into your terminal and type in
```
sudo apt-get update
```

Then 
```
sudo apt-get install wine
```

---

### Post by Kindred on 2006-01-14
I'm new to this myself but I don't think wine can work on 64 bit.   And if it did I think it would only work with 64 bit win apps, as far as I know. 

I made a 32 bit chroot to run wine but then I ended up just setting up vmplayer in the end which works out better for me..

---

