---
title: "Amarok and Rockbox'd Ipod"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2007-01-11
I'm wanting to use amarok to transfer files to my rockbox'd ipod...is that possible?

---

### Post by Albi on 2007-01-11
Have you tried just following the same procedures as if it were just a regular ipod?

---

### Post by shanepardue on 2007-01-11
Yes. Acts as an ipod. Doesn't transfer .ogg

---

### Post by shanepardue on 2007-02-02
Is this not possible?

---

### Post by oranguman on 2007-02-04
if I remember correctly the new distro of rockbox supports ogg vorbis. you should try it.

---

### Post by shanepardue on 2007-02-04
Ohh I've had Rockbox for a very long time and it's had ogg for awhile. My problem is that Amarok sees my ipod as a regular ipod and doesn't have a plugin for rockbox'd ipods. Therefore, I can only transfer to my ipod as it were in it's factory state. (no ogg)

---

### Post by mrqcho on 2007-02-06
> **shanepardue said:**
> Ohh I've had Rockbox for a very long time and it's had ogg for awhile. My problem is that Amarok sees my ipod as a regular ipod and doesn't have a plugin for rockbox'd ipods. Therefore, I can only transfer to my ipod as it were in it's factory state. (no ogg)
Just set the player as a generic audio device (since a rockbox'd ipod it's not really an ipod in a way)
by that I mean... Amarok transfers music to a regular (non-rockboxed) Ipod by adding it to the same database that itunes creates on it and so that the original firmware recognizes that music.

rockbox doesn't need to read files through that database as it has its own, so on the rockboxk'd either your are browsing the files in an browser like manner, or you are using the rockbox database.

setting the ipod as a generic device brings a menu on the device properties that lets you choose which file types to transfer.

that being said, I just transfered to linux (and rockbox on my ipod) about a month ago, and I haven't played with it that much on amarok, though I did try it and I found it somewhat slow to transfer music to my ipod.

I'm playing with it right now, as that's how I found this post, but I'm currently using this to sync my files:

```
rsync -arvu /dev/hda2/music  /media/ipod/music
```

/dev/hda2/music being the drive where I have all my music
/media/ipod/music being the ipod of course.

it takes it's time to run it the first time, but after that it just updates whatever is added or deleted onto your ipod

note that this will keep the directory structure of your music in the same way you have it on your drive (not the way iTunes does it, so you'd be creating another copy of your files on your ipod).

---

### Post by shanepardue on 2007-02-06
Cool, I usually just transfer in the file browser,but i like how amarok has the queue so you can see how much space you have then click tranfer songs

Thanks for your help

---

### Post by mrqcho on 2007-02-07
yeah in that case, just set the ipod in amarok as a generic audio player, instead of an ipod, and it will give you an option of which file extensions to transfer on the configuration menu of the device

---

### Post by aleska on 2007-04-15
Just in case you still have problems...when your player is connected, go to Settings > Configure Amarok > Media Devices then click on the Configure Device Settings icon (crossed wrench and hammer).  
Be sure that in the "Transferring files to media device" section, all the file formats you want are listed.  For me, this is ogg, mp3 AND m4a.  If ogg and m4a are not there, then you won't be able to drag and drop those type of song files onto your device through amarok.  
Hope that helps.

---

