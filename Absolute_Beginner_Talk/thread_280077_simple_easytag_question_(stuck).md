---
title: "simple easytag question (stuck)"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-10-18
I have tried many different masks for Easytags' "fill tag" feature, but I can't really figure it out. There doesn't seem to be any documentation anywhere for it also. All I want to do is fill the tags with artist, album, disc#, track#, and title. I think I am overthinking things, but the legend doesn't make sense to me. a good documentation site or hint would be great!! thanks in advance!

---

### Post by BitTorrentBuddha on 2006-10-18
I assume you've seen the legend, so I suppose the best way to convey the usage is through examples. 

Okay, say all my songs are labeled as 01 - This is the name of my song.ogg. To fill the tag with track number and title I would simply select all songs to be filled, right click and select fill tag(s). In the dialog, I would type: "%n - %t" without quotes. This would make the track number 01 and the track title "This is the name of my song". 

Now, assume I had the each respective artist with its own folder and in each artist's folder I had subfolders for each of their albums (ie. under ~/Music I have a folder called "The Doors," and in that folder there is a folder called "Morrison Hotel," and one of the tracks in that folder is "04 - Peace Frog.ogg.") To fill the Artist, Album, Track, and Title for any number of tracks (assuming all are organized in the same fashion), I would select my songs that I want to fill the tags of, and then I would put "%a/%b/%n - %t" without quotes (instead of just %n - %t.) This would tag the example track as such; Title: Peace Frog, Artist: The Doors, Album: Morrison Hotel, Track: 04.

You can infer several other ways to do this through experimentation, there will always be a preview of the first song selected's tag should it be filled with the directions directly below the text box so you can be sure. If you need any more help just ask and I'll respond tomorrow (probably.)

---

### Post by shanepardue on 2006-10-22
awesome! that really helped!! i appreciate your assistance!!

---

