---
title: "Rhythmbox Ipod Classic playlists"
date: 2014-04-02
forum: Apple Hardware Users
---

### Post by padnoter on 2014-04-02
Hi,

I'm running 12.04 and having problems with playlist syncing on my Ipod Classic (160gb) with Rhythmbox.

If I create a playlist in Rhythmbox, in the "Playlists" section choosing music from the "Library", & then "Sync with Library" with Ipod, it is not copied over.

If I create a playlist in Rhythmbox, in the "Devices > Ipod" section, choosing music from the "Devices > Ipod", and do _not_ "Sync with Library", the playlist is copied over and I can play it on the Ipod.

But, as soon as I next "Sync with Library", all these playlists are wiped off, leaving only the "Recently Added" playlist.
:(

I've tried creating duplicate playlists in the "Playlists" section & in the "Devices > Ipod" section, but any "Sync with Library" wipes off the playlist from the Ipod. Any lists in the "Playlists" section are left - but these never sync.

Any help would be greatly appreciated.

I've read lots of posts, but not found a solution, other than not pressing "Sync with Library" again!

[btw, I keep my whole music collection on the Ipod, so in sync with rhythmbox library, so when i add new music to the rhythmbox library, i just click the "Sync with Library" to keep everything in line... this solved my older issue of losing album-artwork]

Cheers
Padnoter

---

### Post by padnoter on 2014-04-03
I also can't drag'n'drop playlists between the ipod & library, or  save the ipod created playlists to a file, so everytime I lose them by syncing, I  have to recreate from scratch - it's a problem

---

### Post by padnoter on 2014-04-03
ok, I've found a solution through trial & error, which I hope will help some others having problems with this...
Rhythmbox>Ipod>Properties>Sync

Here's what works for me.
1. start rhythmbox, attach Ipod
2. create a playlist in library (menu>Music>Playlist>New Playlist   or Ctrl-N)
3. rename the playlist if you want
4. add tracks to the playlist from the library (search,drag/drop etc)
5. I'd recommend saving the playlist (as a backup) (menu>Music>Playlist>Save to file)
6. Right click on the "Ipod" in Devices & select "Properties"
7. In pop-up window, click the "Sync" tab
8. expand the "Music" item in "Sync preferences" & tick all the playlists you want to sync. (I tick everything apart from "Recently Played"). Then "Close" the window.
9. Devices>"Ipod", click "Sync with Library"

- that's it. :D

The weird thing is, if you tick the high level "Music" in "Sync preferences", which ticks everything underneath (i.e. all the playlists) and then "Sync with Library", all the playlists are wiped off from the Ipod !! So make sure you tick them individually - you can even tick everything - just make sure you don't have a tick in the high level "Music" - only a dash "-"  - see attached picture. Seems like a stupid frustrating bug to me. But just pleased playlists are working for me.

cheers
padnoter

---

### Post by andrew.46 on 2014-04-20
Hmmm.... creating a playlist and then saving the playlist to my own ipod classic 160 seems a lot more straightforward using amarok :)

---

### Post by geek-virus on 2015-03-03
I've tried what you say but my in the sync rythmbox proposes me only Music or Podcast. So it doesn't work for me. Also musics from playlist i've achieved to add to my ipod classic this summer ( 08/2014) are duplicating since i try to add a new playlist.

---

