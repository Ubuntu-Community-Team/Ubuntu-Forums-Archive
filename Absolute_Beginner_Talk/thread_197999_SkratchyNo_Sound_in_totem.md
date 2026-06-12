---
title: "Skratchy/No Sound in totem?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2006-06-16
I just got done transfering some movies and music from my windblowz machine to my LiNuX box.

I just tested my vidoes and the .mpg files don't have sound and the .avi vid's sound it do scratching that you can't hear anything else.

Could someone recomend a player that supports all media types (including m4a)?
Also
Does anyone know if Mplayer is in the repository? I can only find Kmplayer and that is for Kubuntu.

I have Mplayer Essentials installed in my /usr/lib/win32 folder. I also have w32codecs installed  (from repository).
I also been to the RestrictedFormats page and install basically everything from there as far as media codecs.

---

### Post by Jagot on 2006-06-16
VLC supports pretty much everything and is in the universe repo.

MPlayer is in the multiverse repo so if you haven't enabled that already you need to do so.

---

### Post by nitricacid on 2006-06-16
[QUOTE=Jagot]VLC supports pretty much everything and is in the universe repo.

MPlayer is in the multiverse repo so if you haven't aenabled that already you need to do so.[/QUOTE]

I have anabled Universe and Multiverse and still can't find Mplayer, Only Kmplayer.
I am going to go look for VCL rite now.

update:
I just looked up VCL in synaptic but the only thing i found was for Evolution... urgg.. why can't I find anything in Synaptic anymore?

---

### Post by nitricacid on 2006-06-16
I am having such a horrible day...
I just searched for VCL in synaptic for the 3rd time after finding out what VCL actually stood for (VideoLAN Client) I finally find it and am now installing the little B@$+4RD.
Hopefully this will end some/all my media problems.

---

### Post by Jagot on 2006-06-16
The package you need is just called vlc - not vcl - swap the c and the l.

You should just be able to:

```
sudo aptitude update
sudo aptitude install vlc
```

---

### Post by nitricacid on 2006-06-16
[QUOTE=Jagot]The package you need is just called vlc - not vcl - swap the c and the l.

You should just be able to:

```
sudo aptitude update
sudo aptitude install vlc
```[/QUOTE]

Just one of the Brain Fart kind of days.
Got everything installed and the movies work great. 
Thanks for helping a mindless fool when he needed it.

---

### Post by nitricacid on 2006-06-16
ignore

---

