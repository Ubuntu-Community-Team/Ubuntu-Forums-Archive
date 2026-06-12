---
title: "Ubuntu adds _, __, ___, etc. to drives"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Ash44455666 on 2008-04-18
I thought I had already posted this, but when I did, I was also in a hurry to pack up and catch the bus for school :neutral:.  (btw.. I didn't actually make it lol, I had to be driven)  Anyways, I'm running Ubuntu 8.04 beta.  My main problem is, in my /media folder, all my drives are having underscores added to them.  So my flash drive (labeled CALEB DRON) now has the folders "CALEB DRON", "CALEB DRON_", "CALEB DRON__", "CALEB DRON___", etc.  This is probably just something silly, but how do I fix this/stop it from doing this?  Thanks in advance!

---

### Post by TeoBigusGeekus on 2008-04-18
You can't fix it - it's a known bug...

[https://bugs.launchpad.net/ubuntu/+bug/212278]("https://bugs.launchpad.net/ubuntu/+bug/212278")

---

### Post by Ash44455666 on 2008-04-18
I see.  Is there any way to even make the folders "go away"?

---

### Post by TeoBigusGeekus on 2008-04-18
I am not sure, but unmount your flash drive first and then delete the folders yourself.

```
sudo rm -r /media/CALEB DRON_
```

for example.

[SIZE="7"]_***[COLOR="Red"]BE EXTREMELY CAREFUL WHEN TYPING THE COMMAND ABOVE OR YOU'RE GONNA HAVE MAJOR SURPRISES[/COLOR]***_[/SIZE]

---

### Post by Ash44455666 on 2008-04-18
aha thanks a lot, although from the warning I don't think I'm going to try this with any of my hard drive partitions :P

---

### Post by TeoBigusGeekus on 2008-04-18
Yeah, do that...
I hope that the bug will be fixed in the final release of Hardy Heron!
Have you installed all the updates by the way?

---

### Post by noynac on 2008-04-18
This bug was fixed in a Hardy update a few days ago:

[https://bugs.launchpad.net/ubuntu/+bug/101845](https://bugs.launchpad.net/ubuntu/+bug/101845)

As noted in the bug report, the extra mount points in the /media directory have to be removed manually.

---

### Post by Ash44455666 on 2008-04-18
Oh sorry, and yes, I check for updates daily.  If I already got the update, in that case, maybe it's not really making anymore of the _, __, ___,  ___ etc. drives.  It's just that I had like 20+ folders for each drive already, so I couldn't really tell, lol.

---

