---
title: "ipod shuffle - works but doesnt work?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2007-04-23
according to all the apps ive used on ubuntu, my ipod has the music on it and the apps recognize the songs and are able to play it.

but when i move the switch to the shuffle or play position, it never plays music (yes, ive pressed all the buttons and stuff, still dont work)

anyone got any way to make this work?

---

### Post by jfinkels on 2007-04-23
> **Fittersman said:**
> according to all the apps ive used on ubuntu, my ipod has the music on it and the apps recognize the songs and are able to play it.

but when i move the switch to the shuffle or play position, it never plays music (yes, ive pressed all the buttons and stuff, still dont work)

anyone got any way to make this work?

Your iPod may not be able to read your files if they are in .flac or .ogg file format. Apple doesn't support them, I think.

---

### Post by Fittersman on 2007-04-23
they are .mp3 files, as far as i can remember, this happend to an ipod shuffle i had earlier, but that was under windows and i dont remember how i fixed it, are there firmware upgrades (i htink that might have been it, actually im pretty sure, unless that was my psp...)

can you use firmware updates on ubuntu (for the ipod i mean)

---

### Post by risidoro on 2007-04-26
> **Fittersman said:**
> according to all the apps ive used on ubuntu, my ipod has the music on it and the apps recognize the songs and are able to play it.

but when i move the switch to the shuffle or play position, it never plays music (yes, ive pressed all the buttons and stuff, still dont work)

anyone got any way to make this work?

I have an ipod shuffle 2nd gen. and i have a similar issue. The problem is that rhythmbox and exaile (the two progs i've tried so far) do not support ipod shuffle. They can show you the songs in your shuffle and they can even copy your music to the shuffle but, if you do, it won't be able to play anything.

You have to reboot in windows (i hope you still have a copy of it) and reset the ipod using itunes' utility.

I think the only prog we can use so far is [http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/) (but i've not yet tried it so i cannot assure you it'll work).

Bye

---

### Post by olterman on 2007-04-27
I used the rebuild DB and not only does it work like a charm it also simplifies the use of the Ipod shuffle a ton ....

I posted a short tutorial here
[http://warcry.olterman.se/new/2007/04/26/ipod-shuffle-trouble-in-feisty-and-an-easy-fix/](http://warcry.olterman.se/new/2007/04/26/ipod-shuffle-trouble-in-feisty-and-an-easy-fix/)

---

### Post by Fittersman on 2007-04-27
i tried that, but my windows partition is so slow and for some reason it only half works (some things work, others dont, and apparently installing itunes wont work)

so is there any way i can do this without having to use windows?

---

### Post by psycosmyth on 2007-04-27
sometimes when you use itunes for the shuffle it re-adds the lock file in the itunes folder of the ipod. Just delete it.

---

### Post by Fittersman on 2007-04-28
here is what was on it when i got it (i got it from someone else, they couldnt get it to work, so they gave it to me)

ipod_control
--itunes
----itunescontrol
----itunesdb
----itunesprefs
----itunessd
----winprefs
--music
----f00
------(music)
----f01
------(music)
----f02
------(music)

so, which one of the files is the lock file? (unless its not there)

---

### Post by Jefferythewind on 2007-04-29
yeah, i did the rebuild thing and at first i thought it worked perfectly, but i'm having a similar problem.  The ipod sometimes has the songs, all MP3s, but won't play them.  When i switch all the songs sometimes it just plays some of them.  I'm sure they are all MP3s but i can't figure out it won't play all the songs, any ideas?

---

### Post by Jefferythewind on 2007-04-30
O&#65292; i figured out why i wouldn't work, the song names that were in chinese didn't work, the ones that were just letters and numbers worked.  does anyone know why, is there something in the script i can change.   or maybe because i used my windows to format the ipod, and my windows doesn't have chinese font installed maybe that's why... i'll see what i can do.

---

### Post by Fittersman on 2007-04-30
> **Jefferythewind said:**
> O&#65292; i figured out why i wouldn't work, the song names that were in chinese didn't work, the ones that were just letters and numbers worked.  does anyone know why, is there something in the script i can change.   or maybe because i used my windows to format the ipod, and my windows doesn't have chinese font installed maybe that's why... i'll see what i can do.

..in chinese? do you mean the weird names that itunes names files like XZMB and stuff like that? or is it actually like chinese?

---

