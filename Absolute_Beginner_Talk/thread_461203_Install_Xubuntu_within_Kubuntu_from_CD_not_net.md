---
title: "Install Xubuntu within Kubuntu from CD not net?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Buzz_in_RI on 2007-06-01
I am trying to install the Xubuntu desktop from within Kubuntu but would like to use the files off of the Xubuntu CD because of bandwidth limitations. I tried to point the package managers to the CD but no luck. I'm not that familiar yet with the Linux filesystem yet and couldn't seem to locate the package files on the CD, or else I would have attempted to find the appropriate command line utility. Any help would be appreciated.

Thanks,

Brian Allen
Woonsocket RI, USA

---

### Post by Outrunner on 2007-06-01
Try 

```
sudo apt-cdrom add
```

and insert the Xubuntu CD when asked

---

### Post by ajgreeny on 2007-06-01
Sorry, I don't think it will work unless you have the Alternate Install CD.  The live CD will not do what you want as far as I know.

---

### Post by Outrunner on 2007-06-01
> **ajgreeny said:**
> Sorry, I don't think it will work unless you have the Alternate Install CD.  The live CD will not do what you want as far as I know.

I think that's only for upgrading.

---

### Post by Buzz_in_RI on 2007-06-01
Outrunner - thanks for the quick response earlier. I added the cdrom and it found two lists on the disk, but when I went back into Adept Manager and de-selected the internet repositories xbuntu dissapeared as an available package. I was able to select the disk under Third Party Software sources but to no avail. I can always wait out the download, but hoped that there was a way to use the CD.

Thanks again

---

