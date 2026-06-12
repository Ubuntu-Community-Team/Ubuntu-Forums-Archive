---
title: "How do I get Streamtuner to use VLC player"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2007-03-31
Hi,
I am trying to set up streamtuner to use VLC player.
I go to edit>preferences and try to put VLC %q  under "listen to a stream" but all i get is error messages when I try to listen to a stream
I am trying to eventyally set this up to rip streams, so does nayone know what I am doing wrong?
thanks

---

### Post by Maestro23 on 2007-03-31
Googled this, don't know if it's what you are looking for: [http://software.newsforge.com/article.pl?sid=05/03/23/1911207](http://software.newsforge.com/article.pl?sid=05/03/23/1911207)

Good luck.

---

### Post by Obor on 2007-03-31
I use beep-media-player to play streams from streamtuner but I tried to change it to *vlc %q* and it opened fine in vlc. Make sure you use small letters.

Also to rip streams I find the best to just use streamripper and in preferences set 
```
x-terminal-emulator -e streamripper %q -d /folder/to/ripto -r -q
```

---

### Post by zazen666 on 2007-03-31
Thanks so much!!!
I was using CAPS instead of lower case. Seems to work fine now!!
Will try the code next and see if I can get the ripping to work.
Thanks again---you guys rock!

---

