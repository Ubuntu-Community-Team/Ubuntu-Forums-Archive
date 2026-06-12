---
title: "Ubuntu 14.04 GNOME on MacBook Air, can't find boot after install"
date: 2016-06-03
forum: Apple Hardware Users
---

### Post by cduston on 2016-06-03
Hey All,
    I am installing Ubuntu 14.04 LTS GNOME on a set of identical MacBook Airs (version 6,2). The first install went very smoothly, the second not so much. I installed over the base OSX using USB flash media, and like I said the first one went swimmingly, even though I didn't really know what I was doing. On this second machine, when I restart I get a flashing directory icon with a question mark on it. So it won't boot - but if I reinsert the USB flash drive at that time, it boots right up into the installer. I'm guessing I screwed something up with the EFI/BIOS, but I can't track it down (and my experience is all Windows/Linux). What I've tried:

1. Reinstall OSX via command-R: This failed because OSX couldn't find any drives to install on (uh-oh).
2. Start live Ubuntu, try for a boot-repair. This didn't work, but here is the pastebin: [http://pastebin.ubuntu.com/16950383/](http://pastebin.ubuntu.com/16950383/)
3. I then tried to reinstall, carefully matching partitions across the two machines (they were different). I wasn't able to do this 100%, the partition tool forced 1 MB of empty space at the beginning of the new machine's partition. Anyway, nearly 100% the same partition structure, same error.
4. I noticed that although the partitions now matched, the new machine was missing the "boot" flag for the first partition. I fixed that (using Gparted), but still nothing.

Anyone have any thoughts?

(Something else I just thought of - for various reasons, I tried to install 16.04 on these computers first, but was forced to go back to 14.04 because of a specific piece of software. Could partitioning with 16.04 first, then reinstalling with 14.04 have done something different then just going straight with 14.04?)

---

### Post by cduston on 2016-06-03
Found my own solution. For whatever reason, the operating systems were booting in the wrong order. I could see this by running efibootmgr -v. I determined what number corresponded to Ubuntu (0000) versus OSX (0080 and 0081) and changed the order via

```
sudo efibootmgr -o 0000,0080,0081
```

worked like a charm. Hope this helps someone else in the future!

---

