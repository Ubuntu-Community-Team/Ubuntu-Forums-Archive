---
title: "how to remove all sound related package and install them again?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-03-18
Hi
thank you for reading my post.
I made some changes in my linux in order to get better voice,
I removed alsa and installed oss, I blacklist some stuff in a file...
Now my sound system is completely crazy (voices as bad as a voice coming from within an spiral pipe)

I thouht I can remove all sound stuff and install them again on  a clean machine, 
for example I want to remove all codecs, all sound systems,.. but I want to keep players.

Thanks

---

### Post by (((X))) on 2008-03-18
players and sound systems are two different things, you already removed all soundsystems if your sound mixer can''t find any mixer.
When I selected OSS instead of alsa in kubuntu, I got that terrible sound too.

---

### Post by (((X))) on 2008-03-19
open alsamixer
just make sure pcm volume is same as master
Sound should become clear.

Saved me from reinstalling alsa:)

---

### Post by legolas_w on 2008-04-11
Thank you for your suggestion, it does not helps me.
I removed the alsa and install it again based on the documents provided in the ubuntu wiki, it did not help too.


I think I should find a way t remove EDS? OSS? ALSA,..... all together and install them again, do you know a way to do this?

I should mention again that I can hear voices but they are not in correct shape, for example a track which has both singer singing and players play different instruments, I barely can hear the voice of singers but I do hear the instruments.

I should say that instruments sound is not completely clear.

I removed, Amarok, Mplayer, SMplayer, Exaile, .... and install them again and it does not help too.


Thanks.

---

