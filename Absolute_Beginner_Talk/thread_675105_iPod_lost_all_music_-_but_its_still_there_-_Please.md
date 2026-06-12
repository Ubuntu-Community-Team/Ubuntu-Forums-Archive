---
title: "iPod lost all music - but its still there - Please help!"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by chaulkster on 2008-01-22
Good day,

I have an iPod that I got for Christmas - the device itself is still foreign to me so excuse me if I’m doing something blatantly stupid.

Here's the deal. (I dual boot) I updated and initialized my iPod in WinXP. I then took all my music from the XP OS and copied it to my iPod. From there I went back into Ubuntu (gtkpod) and tried to load just a couple more songs on it. The iPod mounts. Great. I start up gtkpod and I get an error message (something to do with Itunes.db or something?), apparently that’s normal. So I proceeded to load the iPod (all the songs were recognized by gtkpod) and add several more .mp3s.  It did its thing and I ejected the iPod. Rock on iPod.

Unfortunately, it seemed to have wiped clean my iPod. Disappointed, I connected my iPod back up with gtkpod and tried to see if I can rectify my problem. Here's the low down. All the music is still on the iPod but the iPod won't recognize it at all.

I tried the whole thing again - and the result was the same. Touché Apple… Touché.

Can someone PLEASE point me in the right direction?

P.S I've only had Ubuntu for a month - so go easy

Thanks guys

---

### Post by JackS on 2008-01-22
It sounds like your ipod may need to update it's database index.

I know that on my Sandisk Sansa e250r, if I add more mp3 files
they may not be found unless I do an update.  The OEM software
on the Sansa does this automatically upon bootup, with Rockbox
software I tell it to update the index and everything is found.

I know little about ipods.  Perhaps it wants it's 'mommy' - have you
connected it to itunes lately?  Wouldn't that force an update?

---

### Post by lintoon on 2008-01-22
Stupid question but did you click "Save changes" after you added the songs to your ipod in gtkpod.

If you plug it back in with iTunes, iTunes will synchronize it's files to your ipod and you should have it back to the way it was prior to adding the extra songs in gtkpod

---

### Post by furball_1185 on 2008-01-22
If the music files have gone out of sync with the ipod's database, there is no easy way to recover the loss. The ipod is unaware there is any music on it because of the way the songs are stored (not by file name but hashed based on time/date added), and therefore without rewriting the database you can't fix it. Try adding or removing a file using gtkpod, then "Save Changes" to force the database file to update. If that doesn't work, recover your music using gtkpod and load it back on again. I looked for a utility to rebuild the database for you, but i couldn't find anything after a few minutes of looking. From experience, plugging this back into iTunes will probably not yield any results (you won't see music).

---

### Post by chaulkster on 2008-01-22
Thanks for the ideas guys. Ok heres the status.

I can go into my Winbox and run Itunes - which now hates my iPod - and do a system restore only. This is because it says it has been corrupted.

 Ok, so I'm back to step one. I have an empty iPod. This time, thinking I'm the alpha male, I skip Windows music and go right to gtkpod. I load a couple of songs and the same thing happens - nothing. The songs are on the iPod but it blindly looks onward towards whatever little gremlin lives in there. So. Still no music.  Maybe the problem lies within gtkpod?

Bueller? Bueller? Anyone? Anyone?

---

### Post by Nevemind on 2008-01-25
Hi, I'got the same problem!
When I unplugged my ipod, it seems to be empty! It can't read even the song that i put on with Itunes! 
I saw that gparted doesn't recognized it as a device....why?
Is it a File system problem????

---

### Post by dpantell on 2008-01-25
The problem is due to file encryption from Apple.  Go [here]("http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/") and follow the instructions to install the latest libgpod.

This worked for me, I hope it helps

---

### Post by Nevemind on 2008-01-26
yeahhhh it works!!!!
Great thank's a lot, I'm gonna translate it for the italian forum right now!!!!

---

