---
title: "SonicStage / NW-HD5 on Ubuntu"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by loksipan on 2005-09-12
I was introduced to Ubuntu just after buying a Sony NW-HD5.  I love my Walkman, but as a recent convert, I'm equally fond of Ubuntu. I'd give anything to use the two together.

Unfotunately, my "other" computer's a Mac *sigh!*

Is there anything more encouraging in the works besides VMware and Wine as possibles?

---

### Post by Dafydd on 2005-09-12
[QUOTE=][/QUOTE]
 Hi Loksipan,

I have a net md (MZ-N710) and a hi md (mz-nh1). They are both great machines (I used them to record radio interviews). But I'm just too lazy to download stuff or convert to ATRAC and then to use Sonicstage to put them on the minidisc. 

Now I bought an mp3 player to for listening too. I can just download or copy files onto it. It makes Sonicstage seem so useless.

I'd forget Sonicstage! Sony won't change until they go bankrupt. And besides any changes like allowing us  to just download or copy files onto the player will come too late (for my minidisc or  your NW-HD5). I've already 'lent' my net md to my girlfriend. And my hi md is gathering dust (unless I'm doing recordings).

Have you seen the other threads though?

[http://ubuntuforums.org/archive/index.php/t-7913.html](http://ubuntuforums.org/archive/index.php/t-7913.html)

Dafydd

---

### Post by loksipan on 2005-10-02
Removed as inaccurate

---

### Post by Nightwhisper on 2005-10-04
Hello, 

I've read your response in the forum about using this player on ubuntu.

Right now I have the player, I have done what you writed but it is telling me: no database found.

ok so I switched to windows (using it only for play and mp3 is really annoying) then I connected it with the soundthingsony and he created the database.

I've copied the folder.... and... doesnt work. same problem stated above.

Any hint?

thank you!

---

### Post by loksipan on 2005-10-04
I being looking into whether the filesystem can be tricked into accepting mp3 files but found the following: Can anyone add more information that might help?

The track indexing files are very convoluted.  You cannot even swap the
filenames of two oma track files - somehow the system knows.  

i.e if you do the following the tracks will not play.

10000001.oma rename to 1000002tmp.oma
10000002.oma rename to 1000001.oma
10000002tmp.oma rename to 100000012.oma

All that has changed is the music content - the file structure and
everything else remains the same.........but the player knows you have
tampered with it!


If you swap the filenames back then there is no problem - so the file
itself is not corrupted.  You can also completely delete tracks (empty
the trash too) then re-load them to their respective folders and it will
still work, so the file structure is not indexing physical disk
locations, it *is* using the filenames.

But, it seems the system knows when a filename doesn't belong with the
contents of the file - in other words just because you say a track is
Voodoo Child doesn't make it Voodoo Child as far as the player is
concerned - it actually has to be Voodoo Child before the NW-HD5 will
play it!

Perhaps they match a track's file size in the index with the actual
size, or they have some kind of check-sum to make sure a track is what
it is claimed to be.

I don't know if the oma filetype covers only atrac or mp3 files as well.
If it covers both, then the index files must tell the system which is
which.

I was hoping the index files would just be a simple catalogue
(referencing track names, artists & albums to folders and filenames
which we could build artificially - but no such luck
though......bastards.  

If you have the ability to load some mp3 on a windows machine using
SonicStage could you check the filestructure before and after adding mp3
and let me know if the mp3s are stored in a different way or whether
they are adding to the atrac file structure as more .oma files?

Loksipan

---

