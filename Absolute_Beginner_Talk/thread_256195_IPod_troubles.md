---
title: "IPod troubles"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by djcaston on 2006-09-12
I realized that when putting my songs from my iPod onto ubuntu, it wont allow me to play any of the songs. What's up with that? What do I have to do to get it fixed? Also, what do you guys use to change your annoying iTunes m4p files to m4a or other unprotected files? Thanks.

---

### Post by moore.bryan on 2006-09-12
*apple uses aac for many songs... what format's the music you're trying to play and what program did you use to get it into ubuntu?*

---

### Post by djcaston on 2006-09-12
i acually just solved part of the problem. I did get most of my files working, but the m4a and m4p files still dont work. I need to convert them. Any tips?

---

### Post by moore.bryan on 2006-09-12
[I]this is what i have put together from [http://gimpel.gi.funpic.de/wiki/index.php?title=Howto:convert_aac/mp4_to_wav/mp3/ogg_on_Linux](http://gimpel.gi.funpic.de/wiki/index.php?title=Howto:convert_aac/mp4_to_wav/mp3/ogg_on_Linux)... if you save the attached file to your home dir and then:
```
gunzip aac2mp3
sudo chmod +x aac2mp3
./aac2mp3 -h
``` you should see all the commands... if that's not clear, just let me know and i'll help you out.[/I]

---

