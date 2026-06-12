---
title: "Problem with greek subtitles"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by mike23 on 2007-01-10
hi all! i came across a problem and i would like some help if anyone can!! the problem is with Greek subtitles. when i play a movie, the player shows me subtitles but instead of the greek ones i put, it shows mixed up letters something like that.. i tried maybe 4-5 different players. I have also installed greek in language support, and tried several different fonts from within the players settings and preferences.. i have also tried to search the forum and google also but i havent found a solution... anyone knows whats the mistake im doing? :) 
thanx very much!!

---

### Post by raul_ on 2007-01-10
It must be tough being greek :)   anyway, i use xine and i belive that in "Settings" you can choose the encoding of the subtitles. If you know what encoding supports greek alphabet then you're good to go

---

### Post by mike23 on 2007-01-10
actually it is because u have to use greek in office etc.... anyway! the only thing u can change in xine for the subtitles is the size and the vertical offset(whatever that is!) :(:( any other ideas.....? :confused:

---

### Post by mike23 on 2007-01-10
i had to change the experience level to see more options :P anyway i chose the correct encoding and now all i can see is  '  , ? -     :(:(

---

### Post by vanalex on 2007-01-23
Hello Mike23! There's a solution to your problem that worked fine for me:
Download vlc media player.

sudo apt-get install vlc

then change the encoding of your subtitle file (which i assume was generated from a window user) to utf-8. The subtitle file you have has default encoding iso8859-7 so change it as follows :

iconv -f iso8859-7 -t utf-8 file.srt > file2.srt

iconv changes the encoding of a file from (-f) one to (-t) another and then you have to create another file (file2) that has the desired encoding. The file file2.srt is the file you want. Go to the vlc's menu and click open file. Open the movie file and the subtitle file. In the subtitle file put of course file2.srt and you're ready to enjoy your film. I'm sorry for my english..

vanalex

---

### Post by mike23 on 2007-01-24
thanx! :)

---

### Post by id12586 on 2007-01-31
Yes I had the same problem and till i was able to solve it (with the VLC "trick" ) i had to play it through VMware.. :)

---

### Post by Satanister on 2007-02-14
> **vanalex said:**
> Hello Mike23! There's a solution to your problem that worked fine for me:
Download vlc media player.

sudo apt-get install vlc

then change the encoding of your subtitle file (which i assume was generated from a window user) to utf-8. The subtitle file you have has default encoding iso8859-7 so change it as follows :

iconv -f iso8859-7 -t utf-8 file.srt > file2.srt

iconv changes the encoding of a file from (-f) one to (-t) another and then you have to create another file (file2) that has the desired encoding. The file file2.srt is the file you want. Go to the vlc's menu and click open file. Open the movie file and the subtitle file. In the subtitle file put of course file2.srt and you're ready to enjoy your film. I'm sorry for my english..

vanalex

vanalex You are a STAR...
Worked like a charm
Thanx

---

### Post by solketal on 2007-04-12
I Have the same problem with the greek subs,but isnt out there any simpler method? For example a movie player that converts the *.srt only for the playback :popcorn: ?

---

### Post by id12586 on 2007-09-19
I've forgot to post the (easy) solution to this problem.. 

Anyway, just follow the steps (1, 2 ,3) from the attached image and at the last step choose your encoding.
**ISO-8859-7 is the most usual for greek subtitles**

---

### Post by nvteighen on 2007-09-19
Just a thought: Why is Greek so much trouble in Ubuntu? I use Ancient Greek and have no free (as in freedom) way to type polytonic charcters... I had to import some proprietary fonts I use in Windows, but they are a bit buggy (also in Windows)... Of course, my problem is with a dead language; but I always wanted to know what modern greeks feel...

---

### Post by id12586 on 2007-09-19
To be honest, modern greek in linux, is not difficult to have, at least for the experienced users.

The problem is because of the linux's default encoding UTF8 wich is different from the Windows XP 8859-7.

Hopefully linux have made a huge steps over the years with greek support.
About the ancient greek now, i have no experience, but here are some free ancient fonts you could use:
[http://h69.first.gr/kee-first/html/thematafull.php?&ID=149&topicID=1170](http://h69.first.gr/kee-first/html/thematafull.php?&ID=149&topicID=1170)
(start from the MG014)

Good luck. :)

---

### Post by nvteighen on 2007-09-19
> **id12586 said:**
> To be honest, modern greek in linux, is not difficult to have, at least for the experienced users.

The problem is because of the linux's default encoding UTF8 wich is different from the Windows XP 8859-7.

Hopefully linux have made a huge steps over the years with greek support.
About the ancient greek now, i have no experience, but here are some free ancient fonts you could use:
[http://h69.first.gr/kee-first/html/thematafull.php?&ID=149&topicID=1170](http://h69.first.gr/kee-first/html/thematafull.php?&ID=149&topicID=1170)
(start from the MG014)

Good luck. :)

Thanks, but those are not what I need. I must use fonts for philology that are Times New Roman-like and also include quite a big sort of strange accessory characters: macrons, microns... "spirits" combined with all diacritics... O well... I can ask Ubuntu to fully comply with such a specific demand. I've tried lots of fonts, but I can't get them work... Anyway, thanks!

---

### Post by bayatique on 2008-03-03
> **id12586 said:**
> I've forgot to post the (easy) solution to this problem.. 

Anyway, just follow the steps (1, 2 ,3) from the attached image and at the last step choose your encoding.
**ISO-8859-7 is the most usual for greek subtitles**

Thank you very much! Easily solved! I'm now ready to watch my japanese movies. :)

---

### Post by id12586 on 2008-03-04
I am glad that helped mate! :)

---

