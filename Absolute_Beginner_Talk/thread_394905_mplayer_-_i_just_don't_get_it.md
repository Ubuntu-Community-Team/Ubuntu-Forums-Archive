---
title: "mplayer - i just don't get it"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by fuscia on 2007-03-27
ok, so i want to play all kinds of junk from the cl using mplayer (it's not that i *need* to. i just *want* to). so far, i've only been successful with...

*mplayer whywouldanyonelistentothat.ogg*

...but, i don't know what to do to get a cd or shoutcast station going. i've been staring at the man page, but find myself like so...

[img]http://img.photobucket.com/albums/v342/unknownentity/linuxdeer2.jpg[/img]

---

### Post by newlinux on 2007-03-27
for cds, this should work...

```
mplayer -cdrom-device /dev/cdrom cdda:// 
```

replace /dev/cdrom appropriately.
haven't tried shoutcast...

---

### Post by fuscia on 2007-03-27
hey, that worked! thank you much!

---

### Post by newlinux on 2007-03-27
No problem, you can play a particular track or set of tracks by doing:

```
mplayer -cdrom-device /dev/cdrom cdda://4
```

to play track 4 or:

```
mplayer -cdrom-device /dev/cdrom cdda://4-6
```

to play tracks 4-6. Not exactly sure how to do tracks 5 7 and 9 for instance. Maybe use commas :) Not at my linux box to play with it though...

---

### Post by fuscia on 2007-03-27
good stuff, dude.

*mplayer hxxp://160.79.128.242:8500* got me to the 'ill. st. lounge' station at [http://somafm.com/](http://somafm.com/)
now, all i have to do is figure out how to get ip addresses of online radio stations.

edit: looks like *mplayer hxxp://somafm.com/illstreet.pls* works too.

---

### Post by r4ik on 2007-03-27
> **fuscia said:**
> good stuff, dude.

In the meanwhile minding his own  business..
Seen nicer Avatars.
just my 2...

---

### Post by fuscia on 2007-03-27
> **r4ik said:**
> In the meanwhile minding his own  business..
Seen nicer Avatars.
just my 2...

yeah, she's weird to you now, but pretty soon, 'lipkid' will haunt your dreams.

---

### Post by r4ik on 2007-03-27
It is the avatar that changed not the responses. :)

---

### Post by fuscia on 2007-03-27
> **r4ik said:**
> It is the avatar that changed not the responses. :)

huh? anyway...any mplayer tidbits you'd care to share? i could get hooked on it.

---

### Post by Jose Catre-Vandis on 2007-03-27
For dvb tv card with a channels.conf

mplayer dvb://

To watch BBC1  (assuming "BBC1" is you channle name in channels.conf)

mplayer dvb://BBC1

For analogue tv card (tuned)

mplayer tv://

for any movie you might have:

mplayer mymovie.avi

to deinterlace said movie:

mplayer -vf pp=lb mymovie.avi

I could go on...

Suggest you take a trip here:
[http://www.mplayerhq.hu/](http://www.mplayerhq.hu/)

Also ensure you have installed all the codecs you can to ensure everything is playable

---

### Post by r4ik on 2007-03-27
Nope sorry just had to get it out of my system.

---

### Post by fuscia on 2007-03-27
> **Jose Catre-Vandis said:**
> 
I could go on...

no need to be shy. you're among friends.

> Suggest you take a trip here:
[http://www.mplayerhq.hu/](http://www.mplayerhq.hu/)

been there. i found the docs a bit overwhelming, but after this thread, maybe i'll find it easier going.

> Also ensure you have installed all the codecs you can to ensure everything is playable

got 'em all through automatix, as far as i know. i haven't had any trouble playing anything with kaffeine or kmplayer. but, i've always been in search for a player i could use in console mode and it's looking like mplayer is more than i hoped for. thanks for the stuff.

---

### Post by fenian on 2007-03-27
> now, all i have to do is figure out how to get ip addresses of online radio stations.


You can use gedit to open the .pls or .asx files and see the addresses.

---

### Post by fuscia on 2007-03-27
> **fenian said:**
> You can use gedit to open the .pls or .asx files and see the addresses.

it turns out i had mispelled the name of the station. once i spelled it correctly, it was all viola-esque.

---

