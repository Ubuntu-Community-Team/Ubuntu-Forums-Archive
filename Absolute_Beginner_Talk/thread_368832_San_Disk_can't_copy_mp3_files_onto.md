---
title: "San Disk can't copy mp3 files onto"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by hodad on 2007-02-23
I just bought a sandisk sansa 1 GB stick.  I bought it because I have had months of trouble trying to get my Creative Zen V to work. Finally got it to work - for 10 hours - then the battery burned out for good (but since I had it for months... oh well!)

So I looked on the posts for an mp3 player that even an idiot such as myself could configure. Sounded like the sandisk was just a drag and drop ... but NOT FOR ME!!!

I can see the file directories on the sandisk, but when I try to copy mp3's onto it from my pc hard drive, I get 

"Error "I/O error" while copying "/home/mydir...y_Car.mp3"."

I've been trying all kinds of suggestions from the forum, including changing the permissions for the directories to belong to me, but nothing works when I try it.  I evidently need to have someone tell me each step in detail, because I AINT SMART ENOUGH!!

THanks for any help anyone can provide.  I want to listen to music, but it seems all I do it beat my head against the keyboard!

---

### Post by crispy_420 on 2007-02-23
Here is what I found via our good friend google:

[http://en.wikibooks.org/wiki/Sandisk_Sansa_MP3_players/m200#Driver_for_Linux](http://en.wikibooks.org/wiki/Sandisk_Sansa_MP3_players/m200#Driver_for_Linux)

Not exactly Ubuntu but linux: (looks like a setting on the actual player)
[http://gentoo-wiki.com/HARDWARE_SanDisk_sansa](http://gentoo-wiki.com/HARDWARE_SanDisk_sansa)

Mention of how-to for linux:
[http://search.reviews.ebay.com/SanDisk-Sansa-e280-8-GB-MP3-Player_W0QQfvcsZ2809QQsoprZ55382611QQucptZ1QQupvrZ4QQuvidZ10000000002678758](http://search.reviews.ebay.com/SanDisk-Sansa-e280-8-GB-MP3-Player_W0QQfvcsZ2809QQsoprZ55382611QQucptZ1QQupvrZ4QQuvidZ10000000002678758)

Hope this gets you moving in the right direction! Good luck!

---

### Post by hodad on 2007-02-23
... Looks like some good suggestions, I'll give them a try tomorrow.   Thanks a bunch!

---

### Post by Fittersman on 2007-02-23
try Grsync, its in add and remove programs, works for my mp3 player

---

### Post by hodad on 2007-02-24
Tried all suggestions, no luck.   Changed to USB type MSC (whatever that is), and I can see the device, and it's subdirectories, but when I drag a file to it, it won't play it.   

Don't know what grsynch is, and couldn't find it in syaptic, which is the only way I now load anything into Ubuntu, because I've gotten in trouble before.

Tried using Amarok, but it won't see the device.  Tried Amarok Setup, but didn't know what to type into "plugin" or "mount point" fields.

Tried creating #EXTM3U ... file in "text editor" as suggested in the Wiki reference, but that didn't do anything (though the directions were incomplete, i.e., what file format to save the file in ).

THere are some canned songs on the player (which came with it), and they play, so the player is OK.  

THanks for your patience and help](*,) ](*,) ](*,) ](*,) .

---

### Post by hodad on 2007-02-24
!!!!!!!!!! I just got it working !!!!!!!!

I right clicked on one of the songs listed on the sandisk after I copied it onto the device, and chose "Properties - Open With" and chose Amarok.

Don't ask me why this worked, because Amarok is obviously not loaded on the sansa device, but something happened, so I guess I'm alright for now (at least until I turn it off and turn it back on again).  

Situation Normal - Nothing Makes Sense!

THanks for your help; if you have any further insights, I'm all ears.

---

### Post by timcredible on 2007-02-24
grsync is a gui for rsync, which syncs 2 directory's files. in amarok, you'll need to 'detect device' or whatever the wording first, then 'connect to device', then you can create playlists and 'transfer' playlists.  not very easy, but it works with ipods, which are a pain because they have a database file and do not keep filenames after they are transferred.

not sure which model you have, but i bought my granddaughter a 256mb "M" model, and i just copy file onto it from the file browser.

---

