---
title: "How to synchronize Samsung YP Z5 with Ubuntu"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by dannyboy2k on 2007-02-02
Hi,

I'm a new linux convert.

I'm running Ubuntu on my laptop and want to connect my Samsung YP Z5 mp3 player to it.

It comes up as a mass storage device and will copy files from the HD to the player. But because the player picks up the artist name first the songs aren't in the right order. Big issue if you're listening to house music or classic which flows from one 'song' to the next.

I've tried hooking it up to Amarok with no success. Just doesn't connect or show anything. I have libmtb (I think that's the name), but the auto detect doesn't find my player. I have DBUS and HAL daemons (admittedly for Gnome not KDE because I'm running Ubuntu not Kubuntu) There's normally an error sign about a 'malformed url' as well.

Exaile only supports Ipods and Gnomad only support Jukebox (creative works aren't they?)

So, please, could somebody help me to connect the Samsung to Ubuntu so that I can organise my music efficiently. This is quite an important part of why I use my computer for.

Or is there a way that I can get Grip to rip/encode my tracks so that the player will pick up the order of the album? I'm currently ripping to wav and encoding to ogg (cdda2wav and oggenc respectively), but I'm going to try ripping to MP3. BTW a samsung YPZ5 plays ogg files just lovely, even though the manufacturers claim otherwise.

Cheers

Dan

---

### Post by dannyboy2k on 2007-02-03
For anybody who is having the same problem I've sort of figured it out.

I've not used Amarok or anything else.

I ripped the music with Sound Juicer to ogg vorbis format instead of grip and set the preferences to track Artist, Album Title.

**edit>preferences>Track names - folder hierarchy **

When I ripped the music I entered the artist and genre in the applicable boxes.

The one problem I did come across was that one of the tracks wouldn't copy from my music folder, I got an 'invalid parameters' error, but only for one track. However if I moved the directory to my desktop and then copied it to the player it worked fine! Odd.

Oh and make sure your CD drive has DMA turned on so that it doesn't take forever, look in the Ubuntu documentation. If you Google it you will know.

So, after going around the houses with video and audio I've come right back to the programs that come with Ubuntu as standard - Rhythm box, Sound Juicer and Totem movie player, they do everything I need!

One happy camper!! :guitar:

---

