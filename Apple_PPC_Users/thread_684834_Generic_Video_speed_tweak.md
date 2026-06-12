---
title: "Generic Video speed tweak"
date: 2008-02-01
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-01
I just applied a kernel parameter to my yaboot.conf with Feisty and it seems to make the video a *little* more snappy.

Since I'm using the generic nv driver, I thought I'd try the following by adding it to the "append=" line in /etc/yaboot.conf and reapplying the file with ybin -v:

relevant section of /etc/yaboot.conf:

```
append="**fb=false**"
```

**I removed quiet and splash** parameters since I like to see what's going on at boot time, and don't care for the distorted splash.  

Then, made the system aware of the change with
```
sudo ybin -v
```
and rebooted.

Video seems a tad snappier, although I'm hoping it's not just a placebo. :)

---

