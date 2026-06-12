---
title: "Problems with Amarok or K3b"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by nynoah on 2008-02-07
I am having a strange problem with Amarok.  I can not read any files that I have ripped using K3b.  I can play all my other files fine.  I went in an changed the LAME profile in K3b to this......

> lame -h -V 0 --tt %t --ta %a --tn %n --ty %y --tl %m --ty %y --tc %c - %f

I have used those settings before on my K3b to get a better RIP encoding.  I had to reload Ubuntu a month back and now just got around to changing that to the correct VPR encode rate.  But this time, the files I have ripped are not recognized by Amarok.  But I can get them to play under other systems .
So far it will not work on Amarok, Exail, Mplayer,

It will work on Audacious, gxine, Movieplayer, Rythmbox

So any clue why this is happening.  Usually I can play an Mp3 on all of those.  I really like to use Amarok for all my music player needs.   I think there is a problem with the code I put into my K3b.  That is my best guess.  Any clue what I did wrong?

Noah

---

### Post by gn2 on 2008-02-07
Can you play any mp3's in Amarok?

If not and you're using 7.10 try ```
sudo apt-get install kubuntu-restricted-extras
```

---

### Post by nynoah on 2008-02-07
Oh I have no problems playing mp3's in Amarok.  I have had that set up fine.  But for some reason, it will not play those mp3s that I had imported in using K3b.

---

### Post by nynoah on 2008-02-08
Does anyone else have a clue why this would happen?

Noah

---

