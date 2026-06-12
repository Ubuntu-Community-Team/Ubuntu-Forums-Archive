---
title: "playing music over my home network"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by benfindlay on 2006-08-31
Hey guys, been looking for this topic for a few days now and can't quite find exactly what I'm looking for, so I've decided to just post it.

Anyways I want a music player for my ubuntu box that is either able to access a network shared music folder conveniently, or one that can detect an itunes shared music collection. Anyone know of any?

Cheers in advance!

---

### Post by telegramsam on 2006-08-31
If you have Samba installed (which allows cross platform networking), you will be able to play your music.  I do it with mp3's.  There is the DRM issue, however, which may stop them from playing.  But several people on this forum have imported and exported their Ipods, so I'd be willing to bet that any Linux media player will do the job for you.

Just get the workgroup name from your Win network (or run the network set up wizard), and you'll be all set to configure Samba.

---

### Post by benfindlay on 2006-08-31
Hey, cheers for the response.

Yeah I've got samba on and can connect by accessing my pc via networks etc, but was ideally looking for one where I can set the library of the media program to permanently look at that location, or one that will detect the sharing that itunes does on my other pc.

Cheers

---

### Post by telegramsam on 2006-08-31
I think any app will keep the settings you put in there.  I don't know if any of them will hunt them down over a Win network.  Any time I make changes, I import the folders again.

Maybe another forum user has done this???

---

### Post by benfindlay on 2006-08-31
Alrighty then! Cheers for your response. Think I'll give some of them a try and see how they all perform!

Laters

---

### Post by FuriousLettuce on 2006-09-03
It's possible to use fstab to mount samba drives as local drives - for example in /mnt/windowscomp. This will allow any player to bypass any complications stemming from network file handling. Search for 'mount samba local' or similar to find a solution :)

---

### Post by benfindlay on 2006-09-03
Genius! ;)

---

