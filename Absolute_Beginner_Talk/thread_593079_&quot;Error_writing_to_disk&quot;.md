---
title: "&quot;Error writing to disk&quot;"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-10-26
I'm trying to make a Gusty Live CD.  I downloaded the .iso file, put in a disk, and then right clicked on the iso and selected "Write to disk".  I chose the lowest setting (9.1 I think). but when it had finished, it gave me an error, "Error writing to disk.  Try a lower speed."  Any ideas?

Thanks.

---

### Post by taurus on 2007-10-26
Are you doing that with Ubuntu or Windows?  Do you use CDR or CDRW?

---

### Post by Yes on 2007-10-26
Ubuntu Gusty Gibbon, CD-R.

---

### Post by taurus on 2007-10-26
Another way is to install k3b and see if it writes that .iso to a CD.

```
sudo apt-get update
sudo apt-get install k3b
```
It now should be in Applications -> Sound & Video.

---

### Post by Yes on 2007-10-26
Before I potentialy waste another CD, could it be that there just isn't enough room on the disk?  It's a 700 MB disk, and the .iso is 695.8 MB.

---

### Post by taurus on 2007-10-26
Are you talking about the Gutsy Desktop CD (LiveCD) iso image?  It should be fine because people have been burning it like crazy since it came out last week.

---

### Post by Yes on 2007-10-26
Yeah, the Gusty Gibbon Live CD.  I'll try k3b now.

k3b worked great, thanks!

---

