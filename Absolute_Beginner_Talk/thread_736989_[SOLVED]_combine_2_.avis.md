---
title: "[SOLVED] combine 2 .avis?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-03-27
I have a movie and it is split into two .avi files. I am wondering if there is anyway i can combine the file to make one .avi without losing quality or anything.


thanks :)

---

### Post by Bachstelze on 2008-03-27
There are plenty of tools to do that, like ffmpeg or mencoder. If you want a GUI tool, try Avidemux (it's very similar to VirtualDub in Windows, if you have used that).

---

### Post by rockinlinux on 2008-03-27
so i got that program, i have never really done any video stuff before. would you mind giving me a basic how to?

thanks for your time

---

### Post by Bachstelze on 2008-03-27
Which one?

---

### Post by jjgomera on 2008-03-27
avidemux graphically: open CD1, append CD2 and save film.

transcode is other option by console, the command would be same like this:

avimerge -i "/directory/CD1.avi" "/directory/CD2.avi" -o "/directory/film.avi"

Avidemux is graphical, but limited in multiaudio videos, transcode is faster and without problem with multiaudio videos

---

### Post by rockinlinux on 2008-03-27
thanks! i just used the transcode and it was super fast and easy! :)

---

