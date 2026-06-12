---
title: "cdrom ownership"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by mar225 on 2007-01-18
When I insert a data cd on the drive and try to copy a file to my /home dircetory it fails and says read only. When I check the permissions it says root.

I tried to change ownership by doing a sudo chown mar225 /media/cdrom
It appears to take but the permissions are still the same and so is ownership. 
What do I have to do to copy the files on a cd

Thank You..

---

### Post by taurus on 2007-01-18
You cannot change permissions on files on CD-ROM since it's a read-only media!  What happens when you try to copy it from a terminal?

Applications -> Accessories -> Terminal
```
cp /media/cdrom/**filename**  ~
```

---

### Post by mar225 on 2007-01-18
It says permission denied 
I cant even open it to read on the cd.

---

### Post by taurus on 2007-01-18
```
sudo ls -la /media/cdrom
```

---

### Post by mar225 on 2007-01-18
This is ridiculous. Still says permission denied.

CD is in the trash and so is Umbungo   This reminds me of my last boyfriend

---

### Post by floke on 2007-01-18
You needed permission to access your boyfriend?
Have you tried using gksudo nautilus to change the settings through there?
I had permission issues a few days ago and no amount of chmodding or chowning would do it. In the end I get to use the file manager in root mode to manually tick the boxes to give me my permissions back.

Not sure if your supposed to do this, but it worked for me!

---

### Post by taurus on 2007-01-18
> **Steve.K said:**
> 
Have you tried using gksudo nautilus to change the settings through there?
I had permission issues a few days ago and no amount of chmodding or chowning would do it. In the end I get to use the file manager in root mode to manually tick the boxes to give me my permissions back.

Not sure if your supposed to do this, but it worked for me!

But you cannot change permissions or ownership of files on CD since it's a read-only media.

---

### Post by mar225 on 2007-01-18
If you can't read them, copy them off, use them what good are they. you can't run a pdf file. Adobe can't get to it to open it. 
Something is wrong with this picture.

---

### Post by taurus on 2007-01-18
And you still get the permission problem even with the sudo command!

```
sudo ls -la /media/cdrom
```

---

### Post by floke on 2007-01-18
True enough about the read-only media - but the problem might be with ownership of the cd-rom access itself (this is what seemed to happen to me) - i.e. I had no right of access even to use the CD-rom - which you could change through using gksudo nautilus (??)

Sorry for causing confusion here ! :confused:

---

### Post by mar225 on 2007-01-18
I'm not confused. I just don't know what I'm doing. 
The message I get no matter what I try is that I don't have permission to read the disk. Apparently not to copy or do anything else with it either. I do know it works in windoze. 
I have wasted enough time confusing myself. Guess I'm just not ready for the big leagues yet.

Thanks to all who took the time to help.

---

### Post by floke on 2007-01-18
That's what I'm trying to say - what are the permissions for the actual CDrom drive itself?
If you go to it - its in the media directory - and right click on the CDrom icon - then what are the permissions for it - not the disc, just the actual drive?

---

