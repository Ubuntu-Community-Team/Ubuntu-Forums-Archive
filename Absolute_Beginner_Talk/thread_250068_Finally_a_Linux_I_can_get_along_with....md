---
title: "Finally a Linux I can get along with..."
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Prosody on 2006-09-03
... mostly.

My only previous experience of Linux was DSL and I just felt like I couldn't do anything on it, Ubuntu however is great and has some usability right out the box.

The main problem I have however is accessing windows drives.



Basically whenever I click a partition wether it be NTFS, FAT16 or FAT32 I get the following :


"Unable to mount the selected volume."

When I click "More Details" it tells me -

error:device /dev/hda8 is not removable
error:could not execute pmount



Anyone tell me what this means in English? :)

---

### Post by mejy on 2006-09-03
> **Prosody said:**
> ... mostly.

My only previous experience of Linux was DSL and I just felt like I couldn't do anything on it, Ubuntu however is great and has some usability right out the box.

The main problem I have however is accessing windows drives.



Basically whenever I click a partition wether it be NTFS, FAT16 or FAT32 I get the following :


"Unable to mount the selected volume."

When I click "More Details" it tells me -

error:device /dev/hda8 is not removable
error:could not execute pmount



Anyone tell me what this means in English? :)

The error is pretty generic afaik.  Have you added the drive to /etc/stab/?  Check out [http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php).

---

### Post by Prosody on 2006-09-03
A little after I posted this thread I was playing round and went into filesystem. Saw the /mnt/ folder and went into that and found the partitions I had tried to access, they can be opened fine from there... it's just the 'HD' icons under "Computer" that give me the aformentioned error... dunno if that's me being dumb or what but as long as I can access the files some how lol.

I think I have some serious reading to do on this whole Linux thing, kinda just decided to try this Ubuntu I'd heard all about on a whim today lol. :)

---

