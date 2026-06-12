---
title: "Music player help..."
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by Narpas on 2006-04-09
I've installed Totem, Rythembox and vlc. I've got my Music in a seperate hard drive partition than /usr (where each of the programs are installed), in the location /home/narpas/Music.

Just as when I ran it under Windows, vlc doesn't seem to ever be hindered by anything - it works. The other media players, however, return the message when I try to play music, "Could not open resource for writing." The permitions for my music are 777 (that is, -rwxrwxrwx).

What am I missing, here?

---

### Post by PhoenixP3K on 2006-04-09
Perhaps, your codecs are not installed... still it's hard to understand why you have that problem. I run my music from an other NTFS hard drive that is read only and I never had that problem. Then again if it was a codec problem it would of told you it can't read that file...

---

### Post by Narpas on 2006-04-09
I've gotten any relevent gstream plugins, but it's still a no-go. Any other ideas?

---

### Post by eriefisher on 2006-04-09
I have'nt tried Rythombox but Totem keeps crying about not finding a mount point for my dvd player. Vlc just plays everything without issue and you can stream with it. Amarok does a good job of playing my mp3s, I like it. 

I would try using different engines with different players and see what happens.

eriefisher

---

### Post by Narpas on 2006-04-10
I've got Amerok to run well with my music folder, but I've still got the trouble of not being able to write to the MP3s (for editing tags, changing titles, etc.)

I figure it doesn't have the authority to write accross partitions. How do I give it this ability?

---

