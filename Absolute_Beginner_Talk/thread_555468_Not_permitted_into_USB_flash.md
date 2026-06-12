---
title: "Not permitted into USB flash"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by leetrefz on 2007-09-20
Ok, who programmed it like this?

For some reason I can happily & automatically read & write on my USB hard disk, but not my SD card via USB. 

Sorry, there can't be a good reason for this. 

Saw 1 unresolved post on this, what I'd call HOW TO GIVE MYSELF PERMISSION TO USE THINGS THAT BELONG TO ME, for tux's sake. I'm very happy with my OS but this problem is AWESOMELY STUPID and caused me a little business related trouble.

---

### Post by lisati on 2007-09-20
What file system is it using?

---

### Post by leetrefz on 2007-09-20
oh right, FAT16.

---

### Post by tombott on 2007-09-20
I can write to Fat32 SD cards without any issues whatsoever

What version of Ubuntu are you using?

---

### Post by ajgreeny on 2007-09-20
And I can write to fuji xD cards fat32 or fat16 without a problem, but using kubuntu, I have to admit.  Surely, however, things like the mount properties of flash cards should be desktop independent.  Can it be something to do with your particular card; have you tried another?

---

### Post by Bachstelze on 2007-09-20
Thread title edited. Calm down a bit, okay ?

---

### Post by Jeroen Vernooij on 2007-09-20
type
```
sudo chown username mountpoint
```

for example ```
sudo chown jeroen /media/sda1
```

You should've gained permission automatically indeed, maybe it's a bug.

---

### Post by Jeroen Vernooij on 2007-09-20
If you go to 
system->admin-> users and groups, click on your username --> properties, tab 'user privileges' make sure your privileges are check as in attached screenshot

---

### Post by leetrefz on 2007-09-20
Well hey, did nothing, plugged it back in & it works. no more little orange locks on all the contents. Sorry.

---

### Post by steevc on 2007-09-21
I've just had this problem. I have a flash MP3 player that somehow got corrupted. Linux wouldn't see it, so I reformated as Fat32 on Windows. Now I can read it on Linux, but not write.

I've had it working before the corruption, so what's new?

It mounts with my user and group root.

Update: Okay, I now remember that it mounts as read-only if you have the Hold switch on. Just ignore my ramblings ;)

---

