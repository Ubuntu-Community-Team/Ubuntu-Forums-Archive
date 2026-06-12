---
title: "wmv to avi.."
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by Niranjan81 on 2006-06-05
ok...so agreed that Ubuntu has issues with .wmv files but it can certainly play .avi. So is there any .wmv to.avi converter for linux??

---

### Post by Travisty on 2006-06-05
Are you having problems playing WMVs and that's wh you want AVIs? I have had good luck with MPlayer and WMVs.

---

### Post by Niranjan81 on 2006-06-05
so i shud install Mplayer?? not sure what u meant :(

---

### Post by Travisty on 2006-06-05
If you want to watch them, then yes. Instal MPlayer.

---

### Post by Travisty on 2006-06-05
If you want to transcode them then you can use mencoder or Konverter.

---

### Post by Niranjan81 on 2006-06-05
Thanks...,, am gonna give both a try ! :)

---

### Post by honeydew on 2007-01-13
I was looking for a awnser to the same question... I found this juicy little line and it worked for me =]

mencoder stest.wmv -vf scale=720:480 -ofps 30000/1001 -ovc lavc -lavcopts vcodec=mpeg2video:aspect=4/3 -oac lavc -lavcopts acodec=mp2 -o stest.mpg

tryed this one bellow to goto avi, but I ended up getting a jumpy file.. be sure to give it a try anyways though

mencoder infile.wmv -ofps 23.976 -ovc lavc -oac copy -o outfile.avi

enjoy!

---

