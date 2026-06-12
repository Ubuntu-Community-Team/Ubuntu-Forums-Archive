---
title: "vlc sound problem"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by ferronica on 2007-06-01
whenever i play MP3 using VLC it produces Crackling sound, when i tried to play mp3 in Rhythmbox  
 it works good no problem, what setting should i require in vlc, i am using creative sound card no motherboard sound.

---

### Post by Inxsible on 2007-06-01
Do this to fix your problem:
 
1) Stop playback (changing some preferences in VLC while playing can cause it to freeze).
2) Go to Settings > Preferences.
3) Click the drop arrow next to Audio.
4) Select Output modules.
5) On the lower right corner, click the advanced options checkbox.
6) Select Linux OSS audio output (ALSA is broken in VLC).
7) Click save.
8 )Restart VLC (fix won't work until VLC is restarted).
 
That should work. Post back if it doesn't and we will try to see what else we can do :)

---

### Post by ferronica on 2007-06-01
okay thnx your idea works for me no crackling sound, one thing i wanna know before that i  am using ubuntu 6.10 and others i got no problem with VLC, but why in ubuntu 7.04 Fiesty Fawn ???
And  i am  using creative sound blaster Audigy card on both Releases never faced this strnage problem :( :( Anyway i am new in linux and i love ubuntu :) :) :):)
 i have just added tag of screenshot what changes i did thanx for your help

---

### Post by ferronica on 2007-06-01
okay thnx your idea works for me no crackling sound, one thing i wanna know before that i am using ubuntu 6.10 and others i got no problem with VLC, but why in ubuntu 7.04 Fiesty Fawn ???
And i am using creative sound blaster Audigy card on both Releases never faced this strnage problem Anyway i am new in linux and i love ubuntu
i have just added tag of screenshot what changes i did thanx for your help

---

### Post by bluehue on 2007-06-02
> **Inxsible said:**
> Do this to fix your problem:
 
1) Stop playback (changing some preferences in VLC while playing can cause it to freeze).
2) Go to Settings > Preferences.
3) Click the drop arrow next to Audio.
4) Select Output modules.
5) On the lower right corner, click the advanced options checkbox.
6) Select Linux OSS audio output (ALSA is broken in VLC).
7) Click save.
8 )Restart VLC (fix won't work until VLC is restarted).
 
That should work. Post back if it doesn't and we will try to see what else we can do :)Thanks! :)

---

