---
title: "Is there a way for me to set my default speaker volume at login on my laptop?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by diablo75 on 2008-03-13
I have a laptop.  Sometimes I logoff after watching a movie or something and the volume when I shut down is a little high.  Now, some might say, "Turn it down yourself," or "Just remove the startup sound."  But this is Linux.  I should be able to do whatever I want to it, right?

Is there a way to set the default login speaker volume so that when I login to my account, the Ubuntu theme (or whatever startup sound happens to be in use) doesn't come BLARING out of my speakers, making me rush to hit the mute button?

---

### Post by deepclutch on 2008-03-13
well,iirc "alsactl" as "sudo" can store the preferred volume.
u open "alsamixer" from terminal.make the volume etc as per ur preferences.
then 
```

sudo alsactl -d store
```
Hope this works.

---

### Post by konungursvia on 2008-03-13
Also, I prefer speakers with hardware volume control. I have a little thumbox on the cable that I sit right next to the keyboard so that I can use its internal capacitors to control volume more immediately. Have you ever tried that? :)

---

### Post by diablo75 on 2008-03-13
My home PC is attached to a surround sound receiver so I have analog volume control on that thing.  But I'd rather not try to lug external speakers with their own volume control around with my laptop.  The bag I carry it in is already stuffed to the brim with equipment.

I'll try the suggestion for the alsa mention above sometime later today.

---

