---
title: "partition problem"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by carverj on 2006-03-12
g'day guys/gals
well, tried to install xp on hda5.
bad idea. first, wouldn't install anyway. restarted, no os. cant be sure if hda6 (home) was deleted accidentally. can't use ubuntu disk as it won't install to unclean target when I try to reinstall on hda5. home partition (hda6) is now
#6 logical 4.8 GB ext3 /media/hda6 so mount point may have changed cant remember what used to be mount point. 
so now I am in live cd wondering what I can do next. any ideas?
If there were just some easy instructions on using vmware or qemu, I could have accessed the couple of windows programs I need access to without fuss. 
Oh, well. just have to hurdle the brick wall sometimes don't you!??!
:-#

---

### Post by thnogueira on 2006-03-12
Please be more specific. What is exactly your problem?

Do you have Ubuntu installed in some partition?
Post the results of the following commands:

```

fdisk -l /dev/hda

```

```

mount

```

---

