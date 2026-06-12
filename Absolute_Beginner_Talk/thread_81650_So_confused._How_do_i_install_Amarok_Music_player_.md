---
title: "So confused. How do i install Amarok Music player or some similar??"
date: 2005-10-24
forum: Absolute Beginner Talk
---

### Post by dbzzx on 2005-10-24
I really need a mp3 player on this operating system
I need one that can rip cd's
                                play mp3's
                                and burn cd's
In other words something like Windows media player.:) 

I downloaded 3 Amorok .deb files but dont know how to install them, please help.:confused:

---

### Post by aysiu on 2005-10-24
You don't need to download .deb files. You can install it from the repositories. Type this in a terminal ```
sudo apt-get update
sudo apt-get install amarok
``` That's it. You now have Amarok installed. There's a graphical way to do this, too (see the second link in my sig).

MP3 support is something extra you have to add because it's a proprietary format (and Ubuntu is totally free--nothing proprietary). First, add extra repositories by following these instructions:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

Then, add the appropriate codecs (everything with the word *lame* in it) following some of these instructions:

[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

---

### Post by La1nE on 2005-10-24
[QUOTE=dbzzx]I really need a mp3 player on this operating system
I need one that can rip cd's
                                play mp3's
                                and burn cd's
In other words something like Windows media player.:) 

I downloaded 3 Amorok .deb files but dont know how to install them, please help.:confused:[/QUOTE]

First of all, check you repositorys, just follow the guide at ubunutguide.org if you havn't done this already. 

Second, open a terminal and type:

```
sudo apt-get install amarok
```

Thats it, i think. ;)

---

### Post by dbzzx on 2005-10-24
Ok installed amarok, it opens fine, i installed all Lame files but i dont know what to do with [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

The mp3's work in xmms

---

### Post by La1nE on 2005-10-25
[QUOTE=dbzzx]Ok installed amarok, it opens fine, i installed all Lame files but i dont know what to do with [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

The mp3's work in xmms[/QUOTE]

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html) was just an url for a howto with your repositorys. So, if amaroK starts ok, whats the problem? No sound? 

I have also had som problems playing mp3's in amarok. 

Open your terminal, type: ```
killall esd
``` 

That worked for me, at least. Since i'm still new at linux, i don't really know how to fix it permanently, but i'm sure the forums know. :)

---

### Post by ineptuser on 2005-10-26
quick thanks for the link to the how-to for adding more repositories....i was able to get gnucash and wine installed and running in minutes

---

