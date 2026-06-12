---
title: "Running an .exe file that contains Quicktime?"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by hossiam on 2008-01-01
I looked around and could not find an answer to this....I have training videos(Total Training)  and want to play them in ububtu.  They are .exe files that contain Quicktime files for the video.  I use Wine to strt them and they run fine.  Until  I am prompted to install Quicktime.  Any help would be great!

---

### Post by SOULRiDER on 2008-01-01
Download Quicktime or quicktime alternative (im not sure about how legal the latter is though) and install them using wine. That should make your videos work.

---

### Post by hossiam on 2008-01-01
I ve tried that and Quick time says it doesnt support the OS.   If there is a way to work around that then I think you solution would work.

---

### Post by SOULRiDER on 2008-01-01
Check out quicktiealternative, see if that installs.
[http://www.free-codecs.com/download/QuickTime_Alternative.htm](http://www.free-codecs.com/download/QuickTime_Alternative.htm) Install that one, dont install the lite one.

---

### Post by hossiam on 2008-01-02
No dice......unless there is something i m missing.   It says it needs xp in order to install

---

### Post by SOULRiDER on 2008-01-02
Type wincfg in a terminal and select Windows XP in the applications tab,

---

### Post by LowSky on 2008-01-02
try to find a older version of quicktime (try 5 or 6), and make sure you have the newest version of wine. From what I hear some people have iTunes 6 even running (sort of atleast)

---

### Post by Malta paul on 2008-01-02
Hi, You might like to check out this:[http://wine-review.blogspot.com/2007/08/quicktime-716-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/08/quicktime-716-on-linux-with-wine.html)
Not if this will help, wish you luck anyway  :)

---

### Post by hossiam on 2008-01-02
2000 compatible quicktime.....thanks for the help.

---

### Post by ARhere on 2008-01-02
Note for the future:

Always avoid options from programs that generate a self running executable from a file.  Another example of this is Winzip; it will give you the option to change a zipped file so it will self-unzip.  It does so by generating a tiny version of itself and attaching it to your file.

This may seem like a handy function, but it will bite you in the @ss later as you will lock in that file to a particular program version and locks away the original file.  You might want to open the file in a windows machine and resave it as its original Quicktime file, then bring it back into Linux.

Just some good PC use worth <$0.02
-AR

---

### Post by Paulmd on 2008-01-02
> **hossiam said:**
> I looked around and could not find an answer to this....I have training videos(Total Training)  and want to play them in ububtu.  They are .exe files that contain Quicktime files for the video.  I use Wine to strt them and they run fine.  Until  I am prompted to install Quicktime.  Any help would be great!

I have been where you are. Quicktime just won't install on ubuntu. Period. I've found that vlc is one of the better players for quicktime movies.

The question is will it work with that exe? I have no idea.

It may be possible to extract the video files from the exe, using a zip program, such as 7-zip.

---

### Post by hossiam on 2008-01-02
i managed to intall version 7.1.6 which can be found on the quicktime web site.   thanks everyone

---

### Post by SOULRiDER on 2008-01-02
Its good to see you got this solved. Do you think you can mark the thread as solved? (you can do that fromt he thread options menu thingy in the top of hte page)

---

