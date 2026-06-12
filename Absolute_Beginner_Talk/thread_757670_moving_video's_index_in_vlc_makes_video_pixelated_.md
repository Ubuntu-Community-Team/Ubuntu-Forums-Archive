---
title: "moving video's index in vlc makes video pixelated for few seconds"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by PetePete on 2008-04-17
when ever I change the movies location, (use the slider to skip forward) the movie becomes pixelated for a few seconds (5?) then goes back to normal.

how can  I stop this? i think it only happens with wmv

ps. i already have w32codecs installed

thanks

---

### Post by northern lights on 2008-04-17
I think you'll have to live with that for now...

... not the answer you expected, for sure.

---

### Post by sayakb on 2008-04-17
> **PetePete said:**
> when ever I change the movies location, (use the slider to skip forward) the movie becomes pixelated for a few seconds (5?) then goes back to normal.
 
how can  I stop this? i think it only happens with wmv
 
ps. i already have w32codecs installed
 
thanks
 
Which media format are you trying to play. I guess avi and divx do not have such kind of problem but wmv files often have that.

---

### Post by northern lights on 2008-04-17
Indeed. If it was happening with avi or comparable formats also, I'd say it's fixable, but wmv are problematic by nature.

It's "windows media" afterall...

[EDIT]If it's really important to you to see that one file smoothly, you might be able to convert...[/EDIT]

---

### Post by PetePete on 2008-04-17
> **LinuxIsInnovation said:**
> Which media format are you trying to play. I guess avi and divx do not have such kind of problem but wmv files often have that.

like i said, only appears to happen in wmv, avi/mpg/mov are all fine


[edit] not important enough to convert, just annoying[/edit]

---

### Post by sayakb on 2008-04-17
@OP
Sorry for the careless reading. I discovered that you already mentioned wmv in your post :)
So this is not actually a problem with VLC. Windows Media Video formats and Audio formats often do not work correctly when seeked at a custom position. Though you might try playing it on Totem Movie Player.

---

### Post by aeiah on 2008-04-17
its the nature of the codec. i think wmv stores certain information in keyframes (which only occur every so often) and so you have to wait for another keyframe before it has all the correct information. something like that. other codecs do it too but dont have all the problems of wmv

---

### Post by PetePete on 2008-04-17
ok, as long as its a known issue.

i just hope someones trying to fix it, instead of one of these issues which everyone knows about but no one can be bothered to find a fix (acceptence is a bad thing)

thanks.

---

### Post by PetePete on 2008-04-17
> **aeiah said:**
> its the nature of the codec. i think wmv stores certain information in keyframes (which only occur every so often) and so you have to wait for another keyframe before it has all the correct information. something like that. other codecs do it too but dont have all the problems of wmv

hmmm i thought it might be something like that, data reduction/compression

but does this same activity happen in XP/Vista? ... i wouldn't know lol

---

### Post by northern lights on 2008-04-17
I've seen similar behavior in VLC (not in Windows media player...) under Windows, but certainly less severe,

It could very well be, that the Windows codec can sort of access keyframes in the background without the movie actually being at that exact position. Somehow windows algorithms get the required info faster, anyways. Which is not the fault of whoever wrote w32codecs, but Macrosh*t not releasing enough information...

---

### Post by sayakb on 2008-04-17
> **PetePete said:**
> hmmm i thought it might be something like that, data reduction/compression
 
but does this same activity happen in XP/Vista? ... i wouldn't know lol
 
Yes it is the same when you play a WMV file on VLC Media Player under Windows. But I don't remember having such problems with Windows Media Player (and you can aleast expect the default player to play it correctly) :D.

---

