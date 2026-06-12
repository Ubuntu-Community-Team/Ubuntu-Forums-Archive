---
title: "Sync songs to iPod with Amarok"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2008-03-27
I have a 80gb iPod Classic Black
Using Ubuntu Gutsy
Using Amarok 1.4.8

I have found Amarok to be a very useful program, except for two MAJOR issues I am having.

1. Lets say I have 10 songs: a, b, c, d, e  (all from the album NEW), f, g, h, i, j (album OLD). Now lets say I add a, b, f, g, h to a playlist called MIX. Upto now everything is fine. Lets say later I decide to delete song a, the issue is it remains in the playlist and causes errors when syncing to the iPod (as it naturally says song not found) or even just playing (on the computer). This isn't an issue if the playlist has few songs were they can be easily deleted, but if there are numerous songs that have been chopped and changed this could be a problem. What iTunes would do is simply delete that song automatically from the playlist. How does Amarok handle this situation?

2.  Lets say I have 10 songs: a, b, c, d, e  (all from the album NEW), f, g, h, i, j (album OLD). I sync them to my iPod, by just right clicking and doing transfer to iPod (this is when the iPod is completely clean and empty). Later I decide to remove song a, b, and instead add song x, y. So I do that in amarok. I also edit some meta data of song c. Now when I go to playlists and synchronise the "All Collection" playlist with device. The songs that were deleted in amarok still remain on the iPod, but the new ones sync just fine. The problem here is that I made massive changes to my collection. But I'd say about half the music is still the same. So I can do the easy thing and erase EVERYTHING from the iPod and add it all again. Or I can do what iTunes would do very easily and just sync with EXACTLY what I have in amarok.

Just to make it more clear: I had the a song by the band "A-Ha!" i changed their name to "a-ha" now on my iPod I have both "A-Ha!" and "a-ha", as you can see a bit irritating! Also if I had lets say the song Comfortably Numb on my iPod, but deleted it from amarok, and then synced, it remains on the iPod.

Any thoughts?

---

### Post by sirgogo on 2008-03-28
Hey,

Alright so heres my diagnosis:
Apple iPods have their own file-system that Amarok tries to copy. So basically, it doesn't use the original folder system that is in place on the iPod. Instead, it makes its own folders with similar properties. You can fix the problem of repeated songs by going into your iPod (hard disk mode), and going to iPod Control, then to Music. Here, clean out all the folders. Now, re-sync to Amarok and things *should* work. Sometimes Amarok/Rhythmbox will put files into the original Apple-folders, and when you change the tags, put them into new folders--- thus giving you the repeat-songs on your iPod.

Take it for what its worth. I used to have that same problem, got fixed after I did a little discovering with my ipod. Good luck.

---

### Post by abhiroopb on 2008-03-28
Don't see what this would do expect just erase ALL the songs, and then I have to re-upload everything anyway

---

### Post by rune0077 on 2008-03-28
Under the "Playlist" menu, there's an option called "Remove dublicates and dead entries". I think you need to first select the playlist in question, then use this option. I'm not sure, though, but it's worth a try. And let us know if it works.

---

### Post by abhiroopb on 2008-03-30
hey it worked thanks :)!

Still unsure about the fix that sirgogo suggessted.

---

### Post by sirgogo on 2008-03-31
Hmmm. Let me explain:

The iPod filesystem is set up into folders that iTunes directs. So when you use Rhythmbox or Amarok, it will read all your songs as they appear in the iTunes/original Apple folder format. When you change tags, sometimes Rhythmbox and Amarok will make a new copy of the song into another new folder. For example, the song "Shambala" by Three Dog Night:

```
Title: Shambala
Artist: 3 Dog Night
Album: The Best of Three Dog Night
Location: "ipod/iPod Control/Music/F55/Shambala.mp3"
```

When you change the tag, the "Artist" lets say, to "Three Dog Night" instead of "3 Dog Night", your location may be **changed** to:
```
Location: "ipod/iPod Control/Music/**f57**/Shambala.mp3"
```
This is what was causing repeated songs on my iPod.

Anyhoo, I'm glad you fixed your problem! :).

(Mark thread at [Solved])

---

### Post by abhiroopb on 2008-03-31
Thanks, so your suggestion is I delete the entire folder structure (i.e. everything under ipod/iPod Control/Music). And then re-upload everything?

---

### Post by sirgogo on 2008-03-31
Yeah, thats exactly what I did.

---

