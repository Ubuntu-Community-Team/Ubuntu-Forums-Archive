---
title: "How to convert an AVI to DVD"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by cleverselfreferentialname on 2006-04-23
I'm looking for a way I can append video compressed with the AVI codec to a DVD.

Can anyone help?

---

### Post by Nikusan on 2006-04-23
[QUOTE=cleverselfreferentialname]I'm looking for a way I can append video compressed with the AVI codec to a DVD.

Can anyone help?[/QUOTE]

You could try [Q DVD-Author]("http://qdvdauthor.sourceforge.net/").

```
sudo apt-get install qdvdauthor
```

It seems to have transcoding abilities, but they might only be for MPEG. Hope this helps.

---

### Post by bionnaki on 2006-04-23
sudo apt-get install tovid
sudo apt-get install tovid-gui

tovid rocks

---

### Post by cleverselfreferentialname on 2006-04-23
Thanks gentlemen. Ended up using the any2dvd script from sourceforge.

EDIT: It was doubleplusungood. I decided to use tovid instead, but it refused to acknowledge that I satisfied the dependencies. I tried DeVeDe, and it is converting right this moment. Thanks.

---

### Post by joshrobinson on 2006-04-24
[QUOTE=cleverselfreferentialname]Thanks gentlemen. Ended up using the any2dvd script from sourceforge.

EDIT: It was doubleplusungood. I decided to use tovid instead, but it refused to acknowledge that I satisfied the dependencies. I tried DeVeDe, and it is converting right this moment. Thanks.[/QUOTE]

devede gave me horrible audio sync problems when i fast fowareded and jumped chapters

tovid is the way to go.. after you installed the dependencies you have to refresh them

tovid -refresh-deps

if nothing pops up.. you are good to go
and launch it with tovidgui

---

### Post by jtpratt on 2006-04-25
There are so many programs, and it's so hard to find the best ones without trial and error.  Because of the multitude of problems I've had with the gui based apps, I use ffmpeg or tovid from the command line - which is very easy.  I explain what works for me in my [Ubuntu Video Conversion Guide]("http://smorgasbord.net/convert_video_linux").

---

