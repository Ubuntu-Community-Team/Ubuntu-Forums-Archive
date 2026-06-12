---
title: "Listen to online radio?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2007-01-19
I want to listen to online radio from this site: [http://sky.fm/](http://sky.fm/)

Unfortunately Rhytmbox can not handle any format. Only xmms can play *.pls files. But I hate xmms because of its ugly interface. Is there a music player, that can play online radio?

---

### Post by mcduck on 2007-01-19
About every music player in Ubuntu can handle web radios, you just need to install required codecs. See here for more help: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Zdravko on 2007-01-19
[mcduck]("http://ubuntuforums.org/member.php?u=17309"), no - this doesn't help me. Rhytmbox just can't handle pls or asx files.

---

### Post by IT'5Huxley on 2007-01-19
Get Automatix and Easy Ubuntu, they should include all the files you need.

---

### Post by Zdravko on 2007-01-19
[IT'5Huxley]("http://ubuntuforums.org/member.php?u=225179"), I tried Automatix a few months ago... I feel sorry about that, however. It installed a bunch of players... I just wanted to listen to online radio.

---

### Post by Sef on 2007-01-19
Have you tried [VLC]("http://www.videolan.org/vlc/")?  It's in the repositories.  It was recommended by [Sky.fm]("http://sky.fm/help_tunein.php").

---

### Post by Jagermaster on 2007-01-19
> **Zdravko said:**
> I want to listen to online radio from this site: [http://sky.fm/](http://sky.fm/)

Unfortunately Rhytmbox can not handle any format. Only xmms can play *.pls files. But I hate xmms because of its ugly interface. Is there a music player, that can play online radio?

mcduck has it right and rythmbox does play .pls files (I'm doing it now).
I did however try to download a pls from skyfm and it doesn't seem to work...maybe they are down?

All my .pls from **shoutcast.com** work fine.
Hope that helped.
B

---

### Post by Zdravko on 2007-01-19
[Jagermaster]("http://ubuntuforums.org/member.php?u=219267"), with xmms I listen to *.pls file from sky.fmm right now!
[[COLOR=#D40000]**Sef**[/COLOR]]("http://ubuntuforums.org/member.php?u=57646"), I'll give it a try. Remember - VLC is already installed, for Automatix was there too :)

---

### Post by Zdravko on 2007-01-19
[[COLOR=#D40000]**Sef**[/COLOR]]("http://ubuntuforums.org/member.php?u=57646"), VLC works! However its interface it pretty weird and I don't see the name of the currently played track on the title bar :(

---

### Post by TheWizzard on 2007-01-19
strange thing you can't listen to sky.fm with rhythmbox. 

you may want to try amarok. it's the best existing music player imo. 

if you want something more gnomish, you can try listen. 
[http://listengnome.free.fr/](http://listengnome.free.fr/)

---

### Post by kgrr on 2007-01-19
> **Zdravko said:**
> I want to listen to online radio from this site: [http://sky.fm/](http://sky.fm/)

Unfortunately Rhytmbox can not handle any format. Only xmms can play *.pls files. But I hate xmms because of its ugly interface. Is there a music player, that can play online radio?

If you are running windows, Winamp can play .pls streams.  It has loads of skins with which you can change its appearance.

If you are running linux, then xmms is one choice.  Did you try changing the skin?   Also, I don't know if amarok works with .pls

---

### Post by Zdravko on 2007-01-19
I want to try Listen. But how am I supposed to install it?

---

### Post by Sef on 2007-01-19
> Sef, VLC works! However its interface it pretty weird and I don't see the name of the currently played track on the title bar

Glad it worked despite the problems you mention.   Looks the like problems with sky.fm is the way it was coded since others have gotten other sites to work.

---

### Post by davebgimp on 2007-01-19
You could try [Exaile]("http://www.exaile.org/trac"). It has most of the features of Amarok, but uses GTK+, so will perform a bit nicer on Gnome. I use KDE and Amarok, so I've not tried it, but I've heard and read very good things.

---

### Post by TheWizzard on 2007-01-19
> **Zdravko said:**
> I want to try Listen. But how am I supposed to install it?

yuo can add the listen repos to your list. then use apt-get or aptitude. 
if you prefer a graphical interface, you can use synaptic. i'm in kde so i can't help you with synaptic. 

you can install amarok by opening a terminal and typing 
```
sudo aptitude install amarok
```

---

