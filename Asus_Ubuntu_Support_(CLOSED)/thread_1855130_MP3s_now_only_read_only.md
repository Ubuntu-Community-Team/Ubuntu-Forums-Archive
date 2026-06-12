---
title: "MP3s now only read only"
date: 2011-10-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Greenwick on 2011-10-05
I use an Asus EEE PC 1001px have a Sylvania SMP2200-Black, a simple 2 gb MP3 player with no visual display or input - just buttons to play/pause, change volume, and switch between tracks.  Using Rhythmbox, I have been able to transfer files to the MP3 player and also delete them.  It has worked very well up until last night.

-I tried to delete a bunch of MP3 files from my player, but soon discovered they hadn't been removed.  I also tried adding new files, but received the message that the files were read only.  This is the message that popped up:

> Error transferring track:
Error opening file '/media/C8E5-CC11/Brian Dunning - Skeptoid/00 - Skeptoid #152_ Attack of the Globsters!.mp3': Read-only file system-Having ascertained what the problem was, I tried doing an update, since things sometimes go screwy when my computer hasn't updated and I haven't noticed.  This didn't fix anything.  I also looked in the documentation, and in forums to see if anyone else has had a comparable problem.

-I checked out what the permissions are for the files.  All the MP3s give my username permission, and the ones I want to transfer over to the MP3 player are read and write.  The ones in the MP3 player are read only.

-Thinking the problem might be Rhythmbox, I downloaded some other programs to try out:
What I tried installing:
Amarok
MPManManager
Hipo Ipod
(And another program whose name I can't remember, but it starts with GTPK.  It was in another forum topic.)


Any advice? I tried very hard to solve this one myself, but I've hit a wall.  Thanks so much!

---

### Post by geiroffenberg on 2011-11-10
Had this happen. Two mp3 players and two flash drives became read only for some reason. Very annoing.
Apparntly some mp3 players get corrupted enough to become read only, because of not use the safely remove function. Maybe its some kind of data protection thing, i dont know.
I even bought a new one because someone in these forums said when this happens its probably because their old and worn out. THats not true.
I installed win xp trough virtualbox, and reformatted both mp3 players to fat32, and now both works as new. 
I tried reformatting in linux several times first, and tried others things i read in several of these threads, some very complicated terminal stuff - non of those worked. It had to be done in windows. Right click the drive and reformat it to fat 32. done.

BTW, i was afraid to do this, because when i tried it in linux it seemed that the firmware in the mp3 player was messed up. That was also not true. The firmware does not get touched when formatting.

---

### Post by Greenwick on 2011-11-10
I actually was able to reformat it in Ubuntu.  No idea why yours had to be done in Windows.  Mine is a very cheap and recent model, so maybe it was designed with multiple systems in mind?

---

### Post by lisati on 2011-11-10
Sometimes there's a flag that gets set and later causes problems in other OSes when people forget to use the "safely remove" option in Windows. It can usually be reset by mounting the device in Windows, doing a "scandisk" or "chkdsk" as required, and then using "safely remove". I have read of a way of doing this via Ubuntu but a link to a suitable thread eludes me for the moment.

---

### Post by brothergrok on 2011-11-12
I have this problem with my 3rd gen ipod nano (8gb). Everything is read only. How do you reformat using ubuntu? I am not seeing that option.

---

### Post by Greenwick on 2011-12-25
Most of what I've seen on the subject says don't reformat in ubuntu.  If you have a local library with windows computers, try reformatting there.  If you try to reformat in Windows, you'll likely break the iPod.

To change something to Fat32 in Ubuntu, though, you have to go to the disk utility.

---

