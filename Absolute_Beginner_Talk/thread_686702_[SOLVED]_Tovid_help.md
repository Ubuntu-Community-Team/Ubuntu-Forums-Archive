---
title: "[SOLVED] Tovid help"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-02-03
I have an avi movie file that I want to put onto a dvd with tovid. Everything is fine till i get to the encoding stage. The file is 696.9 MB and it says (it is still encoding right now btw) 1283 MB written to video.m2v. I don't know if this is right or not as I can't find an estimate on how long it takes. Please help.

---

### Post by Fraser from Scotland on 2008-02-03
> This is the guide I've used to convert an avi file to .iso, which I can then burn to a DVD. I wrote a script based on it.

You'll need to do this:
Code:

sudo apt-get install ffmpeg dvdauthor mencoder

The script:
/usr/bin/convertdvd
Code:

echo "Converting avi.  This shouldn't take too long." &&
ffmpeg -i *.avi -y -target ntsc-dvd -sameq -aspect 16:9 finalmovie.mpg &&
dvdauthor --title -o dvd -f finalmovie.mpg &&
dvdauthor -o dvd -T &&
mkisofs -dvd-video -o dvd.iso dvd/ &&
echo "Conversion complete.  Time to burn."

All you is place that script into your /usr/bin/ directory, chmod +x it, then execute it while in the folder containing the avi.

Ex:
Quote:
[13:43:35 loke]$ cd ~/Movies/Click
[~/Movies/Click]
[13:43:37 loke]$ convertdvd
Converting avi. This shouldn't take too long.

I found this, can someone tell me what i've to at this bit; All you is place that script into your /usr/bin/ directory, chmod +x it, then execute it while in the folder containing the avi.

I don't kow how to get to that directory

---

### Post by obscur156 on 2008-02-03
You can use the .deb package of tovid that you can find here.
[http://www.getdeb.net/release.php?id=1460]("http://www.getdeb.net/release.php?id=1460")

Easy to do,take aproximatly 1 hour or 1:30 depends of your computer speed.

Good luck ,best regards.

---

