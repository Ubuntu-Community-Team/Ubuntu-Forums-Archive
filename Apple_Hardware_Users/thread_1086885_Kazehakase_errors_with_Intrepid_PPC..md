---
title: "Kazehakase errors with Intrepid PPC."
date: 2009-03-04
forum: Apple Hardware Users
---

### Post by casbahdk on 2009-03-04
I am experiencing a problem with Kazehakase on Ubuntu Intrepid PPC.The browser quits as soon as I try to go to a URL or choose a bookmark. I have tried running the browser from the terminal and get the following error messages:

```
(kazehakase:5686): Kazehakase-Net-WARNING **: IO Condition: 25
Segmentation fault
```

Any ideas?

Cheers

---

### Post by joecefiro on 2009-03-04
Also unstable on my systems, randomly quits.

Perhaps the version in synaptec is outdated?

Perhaps find a newer version .deb or compile if your feeling lucky

Have you tried looking at the Kazehakase main site?

Have you googled the problem?

---

### Post by casbahdk on 2009-03-05
I haven't found anything useful on the issue within the last year or so via Google or Sourceforge. Yes finding a newer .deb or compiling from source are options, but I try to stay in sync with the repositories as much as possible.

---

### Post by cyberdork33 on 2009-03-05
> **casbahdk said:**
> I haven't found anything useful on the issue within the last year or so via Google or Sourceforge. Yes finding a newer .deb or compiling from source are options, but I try to stay in sync with the repositories as much as possible.
well if the version in the repos is broken, there is no reason to do that.

---

### Post by tiresia on 2009-03-05
First of all, you should try to reinstall a package
```
sudo apt-get install --reinstall packagename
```

---

