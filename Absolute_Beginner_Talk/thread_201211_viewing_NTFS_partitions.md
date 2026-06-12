---
title: "viewing NTFS partitions"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by tokyo on 2006-06-21
is it possible to view my windows NTFS partition from Ubuntu?

if so, how?

---

### Post by Drakkor on 2006-06-21
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
Good Luck !

---

### Post by rowanparker on 2006-06-21
That is only read only.

If you want to write to NTFS then go [here]("http://http://www.ubuntuforums.org/showthread.php?t=142481"). Although it is experimental so do back up important data.

Rowan.

---

### Post by kzip on 2006-06-21
I had the same problem. The first link was great and has half sorted the issue by getting a mount point to my NTFS drives. But I can only access them via root (sudo). I can't access them on my regular user account (In Gnome I get "You do not have the permissions necessary"). 

I've tried setting new permissions on the mount points but it tells me that it's a read only drive and cannot be changed. Is there a way to get a non-root account to be able to read the ntfs drive?

---

### Post by Stealth on 2006-06-21
rowan: the poster originally asked about viewing, not writing. Writing is way to experimental for newer guys to just "try" out.

kzip: Here's the entry I have in MY fstab file, where I can read it with nautilus as a regular user.

```
/dev/hda1       /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```

---

### Post by kzip on 2006-06-21
I should have done a bit more digging! I needed to add the following options in fstab:

nls=utf8,umask=0222

Then I have access from my regular account :)

*edit* thanks Stealth - I just found something similar (see above) not sure what the difference is between your umask and mine and the additional gid=46 entry though?

---

### Post by rowanparker on 2006-06-21
> rowan: the poster originally asked about viewing, not writing. Writing is way to experimental for newer guys to just "try" out.
Sorry, I just thought he might want some more info.

---

