---
title: "Help gxine doesnt seem to play most of media"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by D_frag on 2006-09-15
I installed the gxine package 
then first i tried loading a .rm file
i got an error
then i tried loading an mp3 file i got an error
and when i tried playing an avi file i got sound only no video ??
I am actually running on a 64 bit architecture using ubuntu dapper drake 
i would like to know why is this happening , is it gxine is not yet fully loaded on 64 bit pcs or it could be fixed ?

---

### Post by halcyon on 2006-09-15
Do you have the codecs for what you're trying to play installed?

---

### Post by Najand on 2006-09-15
Do you have:
> libxine-extracodecs
installed?
if not:
```

sudo aptitude install libxine-extracodecs

```

---

### Post by D_frag on 2006-09-15
i didnt have it installed everything is working fine now .. thank you so much for the great support guys , best support i found on the internet for anything so far 

Though there is a slight request i still cant play .rm files any thoughts ?

---

### Post by andiii on 2006-09-15
Search for Real in the repos. I think there are two versions..

Alternatively search for Real-Player here in the forum.

---

