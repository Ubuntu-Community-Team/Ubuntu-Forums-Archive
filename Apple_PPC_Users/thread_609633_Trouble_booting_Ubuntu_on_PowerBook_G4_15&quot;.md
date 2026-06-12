---
title: "Trouble booting Ubuntu on PowerBook G4 15&quot;"
date: 2007-11-11
forum: Apple PPC Users
---

### Post by marinus on 2007-11-11
I have installed Ubuntu onto my PowerBook G4 (using the alternate install disk, because the livecd doesn't boot). The install went fine, but when I try to boot it, it hangs on the splash screen for a few minutes, the progress bar stays empty. After about five minutes, I get a prompt that says (initramfs).

If I type 'modprobe ide_disk; exit' it starts booting normally (but without the splash screen). Afterwards, the system works fine, but booting it takes five minutes this way and it requires me to manually load the drivers for the hard disk, while it boots in under a minute once the drivers are loaded.

Is there any way for me to get it to load the drivers automatically?

---

### Post by pxwpxw on 2007-11-11
> **marinus said:**
> I have installed Ubuntu onto my PowerBook G4 (using the alternate install disk, because the livecd doesn't boot). The install went fine, but when I try to boot it, it hangs on the splash screen for a few minutes, the progress bar stays empty. After about five minutes, I get a prompt that says (initramfs).

If I type 'modprobe ide_disk; exit' it starts booting normally (but without the splash screen). Afterwards, the system works fine, but booting it takes five minutes this way and it requires me to manually load the drivers for the hard disk, while it boots in under a minute once the drivers are loaded.

Is there any way for me to get it to load the drivers automatically?

update-initramfs

After you exit (initramfs) and start ubuntu,

Add your module names to the file 
```

/etc/initramfs.tools/modules

```
Then run 
```

sudo update-initramfs

```

More discussion on this thread:
[http://ubuntuforums.org/showthread.php?t=581280](http://ubuntuforums.org/showthread.php?t=581280)

---

### Post by marinus on 2007-11-11
It works! Thank you!

---

