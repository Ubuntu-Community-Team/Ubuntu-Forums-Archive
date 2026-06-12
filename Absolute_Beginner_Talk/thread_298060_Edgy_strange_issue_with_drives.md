---
title: "Edgy: strange issue with drives"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by twrock on 2006-11-12
I'm still a newbie trying to figure out Ubuntu/Linux. Too many "little" problems convinced me to do a fresh system install recently and I upgraded to 6.10 hoping some of the hardware issues would be resolved. I don't think my plan succeeded, and I added a new problem in the process.

When I open Places > Computer there are two floppies showing. "Floppy Drive" is my actual floppy disk drive. No problem. But "Floppy 1" doesn't seem to relate to any hardware in my system. If I double click on it, I get the following error popup:
     Unable to mount the selected floppy drive.
And under Show more details:
     mount:/dev/ is not a block device
Clicking on the Properties of that device gives me this info:
     Type:  folder
     Contents:  nothing
     Location:  computer:///
     Volume:  /
     Free space:  6.9 GB
     Modified:  Sat 11 Nov 2006 10:02:16 AM CST

If I were to venture a guess, it looks like it is somehow linked to my first primary partition (10 GB of an 80 GB drive). If so, 6.9 GB free might be about right.

So anything I should do about this?

As long as I'm asking questions, when I installed Edgy, I manually partitioned the drive into three partitions: (according to gparted)
/dev/sda1, ext3, /,/dev/.static/dev, 9.77GiB size, 2.42GiB used, 7.36 GiB unused
/dev/sda3, ext3, /home, 62.75GiB size, 6.02GiB used, 56.72GiB unused
/dev/sda2, extended, 2.01GiB with /dev/sda5 linux-swap 2.00GiB in it

However, as I'm looking at what gparted displays right now, there is a 7.84MiB unallocated space that snuck in there somehow at the beginning of /dev/sda2 in front of the swap file. I'm assuming that happened because the swap file didn't quite fill the total available space. Does that matter? Should I resize that partition?

Incidentally, I'm very willing to simply start over with Dapper if Edgy is still too flakey. This is my "test" box upon which I'm attempting to learn to use Linux and all of my critical data is stored externally.

Thanks in advance.

---

### Post by xpod on 2006-11-12
Hey twrock...you are not alone.

[ATTACH]19215[/ATTACH]

I ended up with the same mess.
I have dapper on hda and edgy on hdb and all was fine at first but when i did a re-install of edgy i got me the 2 floppys for my efforts.

I dont have any other partitions it could be seeing so it can only be the dapper hd it`s getting confused with.....OR should i say "that I`VE confused it with";) 
Fortunately though it aint an issue for me as i dont need to share things back and forward and i have access to edgy from dapper if needs must....
Plus i got plenty other things to keep me occupied with it and both OS`s are working a treat.

I had actually forgot about it till i seen your post.
Now i`ll probably go mess the lot up trying to straighten it out.
Thanks..lol.
I could be wrong m8 but i think it`s just a case of amending the "fstab" although i`d get advice from someone who knows for sure first.

Good luck regardless.
Sorry i cant be of any real help but i just stumble along myself.

---

### Post by twrock on 2006-11-13
Hey xpod, thanks for the "me too". It's always nice to know you're not alone. :) 
Since I had a couple of hours to spare, I finally decided to just kill it (Edgy), and go back to Dapper. Since my goal of installing Edgy was to resolve a few hardware problems, and since it only seemed to exacerbate the problems, I gave up. I guess I should have listened to the sticky post at the top that suggested newbies don't hurry to upgrade.

---

### Post by twrock on 2006-12-03
Ok, I'm back at this same problem because I'm back to using Edgy. (Long story, but basically it was because Edgy solved my Palm hotsync problems.)

So, can anyone tell me what I can safely do to get rid of a strange extra "floppy drive" that isn't a real floppy drive? I did a fresh install of Edgy, so it appears this is going to happen every time for at least me. (And I suspect maybe a few others as well.)

---

### Post by fencemender on 2006-12-03
Hey the floppy thing happened to me too, I made a post about it.  

Floppy 1 seems to be linked to the Floppy drive because when I mount it it tries to access the floppy drive as well.

---

### Post by LDRoamer on 2006-12-03
Mine is the same way. I don't know if this helps at all but I did have a problem with mine where the sound card was using the same dma as the floppy.   When the sound card and the floppy were on the same channel all I had was the "Floppy 1" listed. Floppy 1 did not access the floppy (it returned an error message that it was not a block device).  I had no access to my floppy drive. When I fixed the dma problem I got the icon labeled "Floppy" back and I was able to access the floppy using the icon. The Floppy 1 icon still returns an error message that it is not a block device.

---

### Post by twrock on 2006-12-03
Problem solved. See this thread: [http://www.ubuntuforums.org/showthread.php?t=293332&highlight=floppy+drive+icon](http://www.ubuntuforums.org/showthread.php?t=293332&highlight=floppy+drive+icon)

---

