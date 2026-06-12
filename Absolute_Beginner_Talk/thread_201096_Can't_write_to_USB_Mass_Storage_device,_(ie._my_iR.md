---
title: "Can't write to USB Mass Storage device, (ie. my iRiver iFP-895 .mp3 player)"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by n00b@linux on 2006-06-21
Yo dudes!
 
I've got a problem trying to transfer podcasts from /home to /media/IRIVER.
Everytime I try I get an error saying the device is read only.  Here's the deal: similar transfering works flawlessly in M$ XP so I must be doing something insanely stupid in Ubuntu.
 
Can anyone please tell this numb-nuts what I need to do?
 
Thanks, and, yo-later dudes!

---

### Post by %hMa@?b&lt;C on 2006-06-21
sudo chmod 777 /media/IRIVER

---

### Post by n00b@linux on 2006-06-21
[quote=jeffc313]sudo chmod 777 /media/IRIVER[/quote]
 
Thx jeffc313.
 
A 7-minute turn around.  Man, this forum is awesome.

---

### Post by n00b@linux on 2006-06-21
Hmm.
I tried as you suggested and all I got was:

chmod: changing permissions of `/media/IRIVER': Read-only file system

Any further ideas?

---

### Post by rowanparker on 2006-06-21
Make sure there isn't a lock on the MP3 player (i have seen one with a lock and you can only write when it's unlocked).

Rowan.

---

### Post by bigbird_594 on 2006-06-27
Hi - my apologies if this is the wrong place for this question - but how did you get your iFP-895 to mount in the first place.  My device manager sees it, but I can't work out how to mount it.

Please point me in the direction if this is the wrong place.

Many thank,

bird

---

### Post by rotten777 on 2006-06-28
[QUOTE=n00b@linux]Hmm.
I tried as you suggested and all I got was:

chmod: changing permissions of `/media/IRIVER': Read-only file system

Any further ideas?[/QUOTE]


Read only filesystem means its either NTFS or mounted as read only FAT32. You need to unmount it and remount it as RW. Good luck.

---

### Post by scotsboyuk on 2006-06-28
@rotten777

  How do you do that exactly? I'm having a similar problem writing to my Sony Ericsson W900. Ubuntu recognises it and I can read from it fine, I just can't write to it.

---

### Post by Coralin on 2008-01-27
> **rotten777 said:**
> Read only filesystem means its either NTFS or mounted as read only FAT32. You need to unmount it and remount it as RW. Good luck.

Don't mean to bump this ancient thread, but I'm having exactly this issue; when I connect my unlocked Iriver IFP-899, with the UMS firmware, it mounts, showing an iPod-ish icon on the desktop, and claims to be a read-only filesystem. I can unmount it no problem, but don't know how to remount it as writable... Any suggestions?

[Edit] Oh- this is in Gutsy. [/edit]

---

