---
title: "Burning MP3's to CD"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by Josh1 on 2006-11-30
Hi,
This may seem a newbie question, but I haven't been able to figure out how to burn MP3's -> CD Format.
Using Windows XP I use to use just Nero Express, now I have no ideas.

Anyone know?
- Josh

---

### Post by d3v1ant_0n3 on 2006-11-30
Try using Serpentine Audio CD Creator (should be in Applications>Sound & Video) Alternatively, grab K3B from the repos (from terminal : sudo aptitude install k3b ) or install it using synaptic. It's very Nero-like, although I'd have to say I prefer it. It's cheaper too:p

---

### Post by RMorris78 on 2006-11-30
To get k3b to burn mp3 to CD you need to install an extra package, plugin if you will

depending on distro -> 
Dapper & Edgy -- "libk3b2-mp3"
Breezy -- "k3b-mp3"

you can find those in synaptic or via console "sudo aptitude install *package name*"

---

### Post by CatKiller on 2006-11-30
My other half's been having some success with Rhythmbox's integration with Serpentine - she makes a playlist and then selects Music -> Playlist -> Create Audio CD... Just another option for you.

---

### Post by xyz on 2006-11-30
> **RMorris78 said:**
> To get k3b to burn mp3 to CD you need to install an extra package, plugin if you will

depending on distro -> 
Dapper & Edgy -- "libk3b2-mp3"
Breezy -- "k3b-mp3"

you can find those in synaptic or via console "sudo aptitude install *package name*"

Hi,
Are you sure you'd really need that lib in k3b?
I just opened it and found the option to burn to mp3 (Lame)?
Is "libk3b2-mp3" yet a different thing?
And what do you use to set your encodings to, say, 128, 194 or 320 k?
I can't remember what I used to use under Win to do that...smth like dPower or something.
Thx for reading.

---

### Post by MichaelSM on 2007-05-23
Thank you, RMorris78. It's great to do a quick search for an answer, implement it, and to have it work perfectly first try. :D. Mike.

---

### Post by zerobinary on 2007-05-23
i suggest reading the restricted format on the ubuntu site 
forgot about the url so u find to find it urself sorry

---

### Post by en3rgy on 2007-05-25
> **d3v1ant_0n3 said:**
> Try using Serpentine Audio CD Creator (should be in Applications>Sound & Video) Alternatively, grab K3B from the repos (from terminal : sudo aptitude install k3b ) or install it using synaptic. It's very Nero-like, although I'd have to say I prefer it. It's cheaper too:p

I'm sorry to mention something that's not really a part of this thread but I wanted to mention that I love your slogan. "Microsoft gives you Windows but Linux gives you the whole house." I've never heard that before and I think it is pure genius! Thank you for making my day :popcorn:

---

### Post by en3rgy on 2007-05-25
Anyone know of any Ubuntu compatible MP3 programs that all you to make an audio cd from an MP3 that also has the ability to preview the MP3 before you commit to adding it to the burn list?

---

