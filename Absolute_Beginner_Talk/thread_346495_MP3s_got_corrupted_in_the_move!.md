---
title: "MP3s got corrupted in the move!"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by k1001001 on 2007-01-25
Hey guys. When I transferred from Windows to Ubuntu a couple of months ago, I put all of my files from Windows on my iPod, then transferred it to Ubuntu once it installed. However, I think quite a few of them got corrupted. There's this low rumbling and popping noise in the left channel, and as a recording student, hearing this rumble drives me nuts!

Has this happened to anyone else? Any clues as to how to fix it? I can send a sample to you if you like.

---

### Post by meng on 2007-01-25
> **k1001001 said:**
> Hey guys. When I transferred from Windows to Ubuntu a couple of months ago, I put all of my files from Windows on my iPod, then transferred it to Ubuntu once it installed. However, I think quite a few of them got corrupted. There's this low rumbling noise in the left channel, and as a recording student, this drives me nuts!
Has this happened to anyone else? Any clues as to how to fix it? I can send a sample to you if you like.
Are you sure it's the file and not the hardware?

---

### Post by k1001001 on 2007-01-25
> **meng said:**
> Are you sure it's the file and not the hardware?
Some of the files were corrupted, some weren't. I imagine the iPod did this, but I'm just wondering if this happened to anyone else, and if there was a possible solution. If the iPod did it though, there really isn't much I can do except re-download the songs.

---

### Post by Tomosaur on 2007-01-25
Do they sound ok on the iPod? If so, it could just be a matter of dodgy sound-card support within Ubuntu or something, I would avoid re-downloading until you get to the bottom of this. If it was the iPod then yeah, I don't know what else you could do - but if they play fine on the iPod and not on Ubuntu then all may not be lost.

Thinking on though, I'm not sure exactly how the iPod works. If you move a track from computer to iPod, is it just copied, or does the computer version get removed?

---

### Post by k1001001 on 2007-01-26
> **Tomosaur said:**
> Thinking on though, I'm not sure exactly how the iPod works. If you move a track from computer to iPod, is it just copied, or does the computer version get removed?
Usually when you move a song to the iPod, it just makes a copy on the iPod, and remains on the computer as well.

As for how they sound on the iPod, it was actually a friend's iPod, and I'm sure he's long deleted the stuff by now. It was about 20 gigs of information.

---

### Post by irish_flu on 2007-01-26
I would be surprised if that were corrupted files, just because it doesn't sound like the sort of problems you'd get from corrupted audio files.  I'd expect data to be missing or jumbled, but not to have extra sound coming from anywhere.

Any chance those files all share something in common, like they were encoded with a different app than the others, or they're a different file format (mp3 vs vs mp3pro vs aac vs ogg vs wma, etc), or that there's something else different (maybe the bitrate or something)?

Have you tried them with more than one media player in Ubuntu?  I'd be inclined to see how they sound somewhere else, too (burn them to a data disc and take them to a friend's house, buy a small and cheap USB key, etc).

---

### Post by xhaan on 2007-01-26
I have mp3s that do this also which I know are not corrupted because they're on my XP partition and they sound perfect in XP but get distortion in Ubuntu... not many of them do this, just a few out of hundreds but when they do it, it sounds terrible.

---

### Post by k1001001 on 2007-01-26
> **irish_flu said:**
> Have you tried them with more than one media player in Ubuntu?  I'd be inclined to see how they sound somewhere else, too (burn them to a data disc and take them to a friend's house, buy a small and cheap USB key, etc).
Huh yeah. I normally use Rhythmbox, which was the media player with the problems. It plays perfectly on VLC though. Strange.

---

### Post by Tomosaur on 2007-01-26
If it's not too much trouble, please verify that it's ryhtmbox causing the issue and then check on their bug report page [here](http://bugzilla.gnome.org/browse.cgi?product=rhythmbox) to see if it's already been reported. If so, there may well be a workaround. If the bug isn't there, please take the time to report it.

---

### Post by Rhubarb on 2007-01-26
Just for some background info about corrupted mp3s:-
Way back in the early days of mp3's and dialup internet access, it was quite common to come in contact with a corrupted mp3 (or cooked mp3).
These mp3's had popping, swishing, rumbling and all sorts of other distorted noises.  All of these could be cleaned up with a (windowz) program called uncook.

So maybe (a big maybe here) some of your mp3s are cooked, and the gstreamer plugin that handles mp3s (that Rhythmbox uses) plays the corrupted data, whereas vlc somehow uncooks the mp3s.
I know it's possible to include a checksum in an mp3.

These are only my ideas and experiences, and there's a good chance I could be completely wrong.  Just a few ideas you can throw up into the air :)

---

