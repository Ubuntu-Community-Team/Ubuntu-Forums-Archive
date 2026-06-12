---
title: "What is the usr/bin/play (default) ???  Need help bad"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Atomic Dog on 2007-07-03
I have been put to a task to convert a few more workstations to Ubuntu boxes but they have to play .gsm files.  I can't find a player that will handle .gsm files, but when I browse the list of .gsm files in Firefox (the server has a web interface) and click on one it asks me if I want to save it or "open With:  /usr/bin/play (default).  This actually works and the sound file plays!  The problem is no player pops up, nor can I stop the sound file playing once it starts.  This is a problem.

This is a good sign as I now know that I can play ,gsm files, but I'd like to know what this default player is, and if there is a GUI interface that it will run in. 

Please, if you can help me with this I'd really appreciate it because I'm getting pounded on my management to get these up and running asap (don't get me started).

---

### Post by jfinkels on 2007-07-03
> **Atomic Dog said:**
> I have been put to a task to convert a few more workstations to Ubuntu boxes but they have to play .gsm files.  I can't find a player that will handle .gsm files, but when I browse the list of .gsm files in Firefox (the server has a web interface) and click on one it asks me if I want to save it or "open With:  /usr/bin/play (default).  This actually works and the sound file plays!  The problem is no player pops up, nor can I stop the sound file playing once it starts.  This is a problem.

This is a good sign as I now know that I can play ,gsm files, but I'd like to know what this default player is, and if there is a GUI interface that it will run in. 

Please, if you can help me with this I'd really appreciate it because I'm getting pounded on my management to get these up and running asap (don't get me started).
Have you tried VLC player?

All I know in this area is that the package 'sox' installs the program 'play'. For more info, look at the man pages, or do ```
aptitude show sox
```

---

### Post by AdamG51172 on 2007-07-03
GSM is audio for phone,  the QuickTime player supports it in Windows/Mac.  xine supposedly has some support too.  

See this page for more:

[http://kbs.cs.tu-berlin.de/~jutta/toast.html]("http://kbs.cs.tu-berlin.de/%7Ejutta/toast.html")

---

### Post by Atomic Dog on 2007-07-03
> **AdamG51172 said:**
> GSM is audio for phone,  the QuickTime player supports it in Windows/Mac.  xine supposedly has some support too.  

See this page for more:

[http://kbs.cs.tu-berlin.de/~jutta/toast.html]("http://kbs.cs.tu-berlin.de/%7Ejutta/toast.html")

I looked at that page, but it gave me little info as far as an integrated, GUI app that will play these .gsm files.  tride the xine players, audacity, vlc and more.  I can use the SoX play feature, but this is not viable for a desktop user.  Audacity will open them but the sound is just a horrid screeching sound.  So far it seems there is no GUI app that can play these dang files.

If you want to try to play it yourself here is a small sample file:  [http://noforclosures.com/gsm/test.gsm](http://noforclosures.com/gsm/test.gsm)

---

