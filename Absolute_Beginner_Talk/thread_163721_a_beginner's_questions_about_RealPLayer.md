---
title: "a beginner's questions about RealPLayer"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by medya on 2006-04-21
I installed realplayer using the .BIN file :
[PHP]cd ~/Desktop
sudo apt-get install libstdc++5
chmod +x RealPlayer10Gold.bin
sudo ./RealPlayerGold.bin[/PHP]

when it asked me , where to install,  I had no idea, and I told it to install in desktop .

1- questions :
why it is not added to the application menu  ? is it because I have installed it on the desktop ?

2-
why it doenst support most medias that it should.... like compressed WMA movies and... and video cds and ... 

3-
if I install codecs using Automatix, where automatix would install the codecs?
will it undrestand that my realplayer is in my desktop ? (so to copy the codecs there?) or it doenst need to copy codecs to realplayer folder.... 
(where the codec would be installed ?)

4- is there any program to record a radio ? (while I am listining to Radio using RealPlayer ?)

5-how to un-install the realplayer ?


thanks in advance. :grin:

---

### Post by localzuk on 2006-04-21
The RealPlayer for linux is not the same as RealPlayer for Windows - there are various codecs missing from it IIRC - so some things like WMA's won't work.

The reason the application didn't appear in your application menu is because no application does unless it is specifically built for Ubuntu as a .deb file.

If it installed realplayer to your desktop, the way to remove it is to delete the folder.

Take a look at [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) for information about getting proprietory formats to work with Ubuntu.

Also, if you use automatix, why not install RealPlayer using that?

---

### Post by medya on 2006-04-21
i hate automatix, it always breaks my system, it is just usefull for codecs...

so If install codecs , with automatix, willl realplayer use that codecs ?
where the codecs are installed in linux on a system folder ?

---

### Post by localzuk on 2006-04-21
I don't think Realplayer would use those codecs - as it is a closed app really. But I am not sure.

The codecs are installed into /usr/lib/codecs IIRC.

Why not use the .deb package available from [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) for RealPlayer?

One question though, why do you need/want realplayer so much? I have always found it to be slow, buggy and annoying - programs such as VLC, Kaffeine and Mplayer are much better I have found.

---

### Post by medya on 2006-04-21
would VLC Kaffine and Mplayer , play those formats that Realplayer do ? 
like .RM .AVI .MPG  .WMA and all music and video clips ?

---

### Post by patrick295767 on 2006-04-21
try to use streamtuner for radio online
 
for the video : 
fast : mplayer 

advanced : totem
and also kaffeine (buggy sometimes)
  
for wma, i use totem & mplayer  & kaffeine 
  
for stream : i can use totem or xmms
based on the streamtuner info
(i change in teh option; mplayer by totem)
very nice
  
For installing codecs & realplayer :
run this multimedia script in my signature 
sudo multimedia.sh

For installing realplayer, it's usually adviced to do it in : 
/opt/RealPlayer

Greetz

Do not hesitate to ask questions ! 

Patrick

---

### Post by localzuk on 2006-04-22
Yes they would play them. For a list of formats that VLC plays go to: [http://www.videolan.org/vlc/features.html](http://www.videolan.org/vlc/features.html)

Mplayer and Kaffeine use the codecs installed (such as any libxine codecs, w32codecs and gstreamer codecs).

---

