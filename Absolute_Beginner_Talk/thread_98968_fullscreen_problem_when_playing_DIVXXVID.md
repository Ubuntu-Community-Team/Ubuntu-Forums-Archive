---
title: "fullscreen problem when playing DIVX/XVID"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by ashrack on 2005-12-04
I installed all the neccesary codecs for multimedio. So DIVX/XVID and MP3s all play fine. But the problem is that when I watch a DIVX/XVID movie fullscreen the picture is interlaced and not very smooth. I have the same behaviour in MPLAYER and in the default GNOME player, can't remember the name of it.

Am running it on my laptop: CELERI 2400, 256RAM, GEFORCE FX5500 GO

btw. Checked with HDPARM and DMA is enabled.

---

### Post by ashrack on 2005-12-05
Cmon anyone?
Realy want to switch to UBUNTU to be my mainstream os, but there are some problems I must fix. So pliz anyone help me

---

### Post by patrick295767 on 2005-12-05
Hi Ashrack,
  
I got similar problem with xine.
try kaffeine:
```
 sudo apt-get -f install kaffeine 
```
it solved this problem for me

kind regards, 

patrick

---

### Post by Gray. on 2005-12-05
Do this:
sudo apt-get install totem-xine
Then it should be installed as:
Applications > Sound & Video > Totem Movie Player
When you open the movie go to:
View > Deinterlace
Voila!

---

### Post by ashrack on 2005-12-05
[QUOTE=Gray.]Do this:
sudo apt-get install totem-xine
Then it should be installed as:
Applications > Sound & Video > Totem Movie Player
When you open the movie go to:
View > Deinterlace
Voila![/QUOTE]

Alreadz tried that it doesn't help

---

### Post by ashrack on 2005-12-07
[QUOTE=patrick295767]Hi Ashrack,
  
I got similar problem with xine.
try kaffeine:
```
 sudo apt-get -f install kaffeine 
```
it solved this problem for me

kind regards, 

patrick[/QUOTE]

Still the same error. This really troubles me, since I like to watch DIVX movies and it's also the only reason to go to Win2k. I hope some1 can help out with this. Since I fixed all the problems I was having with UBUNTU except this one.

ps. **How od I take a screenshoot while in FullSreen mode, so U would have a better understanding how it plays in fullscreen? Tried to screenshot with TOTEM but apperantly it is only possible when in windowed mode but not in FS**

---

### Post by Perfect Storm on 2005-12-07
try with
```

sudo apt-get install avifile-divx-plugin

```

make sure that your repo. is setup with multiverse.

---

### Post by ashrack on 2005-12-07
[QUOTE=Artificial Intelligence]try with
```

sudo apt-get install avifile-divx-plugin

```

make sure that your repo. is setup with multiverse.[/QUOTE]
Installed them but didn't fix the problem. 
What else can I do?

---

### Post by ashrack on 2005-12-07
Fixed the problem. Apperantly I had to install NVIDIA drivers. Got info from here:
[http://ubuntuforums.org/showthread.php?p=551553#post551553](http://ubuntuforums.org/showthread.php?p=551553#post551553)

---

