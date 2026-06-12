---
title: "MEncoder AcidRip DeVeDe"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by SomethingCronic on 2007-08-07
When I upgraded to Feisty some time ago I had a problem with MEncoder and DeVeDe, however I managed to get this fixed however yesturday for the first time in a long time I went to use Acid RIP and my videos came out very choppy and unviewable.

Anyone else had this problem, how can I resolve it - I don't want to break anything else - it also seems I can't view DVDs using MPlayer anymore (missing codec?). This is really annoying as I got Edgy working fine, I don't have the patience like I used to have when I first migrated lol.:)

If anyone can help it'll be much appreciated

---

### Post by svega85 on 2007-08-07
when you fixed your devede did you reinstall mplayer and mencoder?

---

### Post by svega85 on 2007-08-07
try starting mplayer like this see if it helps 
```
gmplayer -ao sdl
``` 
it will start it with a different sound driver and somtimes that will fix the choppy video

---

### Post by svega85 on 2007-08-07
for the dvd problem i need to know if you built mplayer from the svn. 
or can you play dvd's from any other player?
if you can't play them from any other player try this in your terminal
```
sudo apt-get install libdvdread3
```
then
```
/usr/share/doc/libdvdread3/install-css.sh
```

---

