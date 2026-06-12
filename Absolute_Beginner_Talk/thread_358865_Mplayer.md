---
title: "Mplayer"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by bobbyshafter on 2007-02-11
Have anyone install Mplayer skins from this site 
[http://www.mplayerhq.hu/design7/news.html](http://www.mplayerhq.hu/design7/news.html)

Please help if you got it to work.

---

### Post by Maestro23 on 2007-02-11
> **bobbyshafter said:**
> Have anyone install Mplayer skins from this site 
[http://www.mplayerhq.hu/design7/news.html](http://www.mplayerhq.hu/design7/news.html)

Please help if you got it to work.

Should help you. Includes skin installation: [http://www.ubuntuforums.org/showthread.php?t=336706&highlight=win32+codecs](http://www.ubuntuforums.org/showthread.php?t=336706&highlight=win32+codecs)

---

### Post by bobbyshafter on 2007-02-11
I download and unpack the skin,i then tried to copy it to 

 usr/share/mplayer/skins.
 
I get a deny message

how do i copy the smiles to my message.

---

### Post by taurus on 2007-02-11
Use the sudo command or <Alt>F2 and type **gksudo nautilus**.  Now, you can write to wherever you want to.

Otherwise, install the new skin to ~/.mplayer/Skins.

---

### Post by Maestro23 on 2007-02-11
> **bobbyshafter said:**
> I download and unpack the skin,i then tried to copy it to 

 usr/share/mplayer/skins.
 
I get a deny message

how do i copy the smiles to my message.

[COLOR="Red"]/usr[/COLOR] is owned by root.

you need to use [COLOR="Red"]sudo [/COLOR]in front of your copy command.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bobbyshafter on 2007-02-11
Thanks guys,i got it to work

I am using kde so i use  gksudo konqueror ,i then navigate over usr>share>mplayer>skins.

I copy the file over by drag and drop.....window user yes we can do that in linux.

---

### Post by taurus on 2007-02-11
With KDE, it's better to use kdesu instead of gksudo.

---

### Post by bobbyshafter on 2007-02-11
Thanks again i suspected that .

Can i skin Kaffeine or xine player.

My xp friends brags about there gui

---

