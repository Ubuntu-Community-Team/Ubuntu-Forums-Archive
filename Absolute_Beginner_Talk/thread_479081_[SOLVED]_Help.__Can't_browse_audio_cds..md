---
title: "[SOLVED] Help.  Can't browse audio cds."
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by laptoplinux on 2007-06-19
When I put in an audio cd, Sound Juicer comes up whenever I try to browse the cd contents.  I wanted to try to uninstall sound juicer, but doing so looks like it would also take out ubuntu-desktop, so I can't do that.  How can I make it so that I have the option of browsing an audio cd's contents in Nautilus?

By the way, once the cd "mounts" in sound juicer, it shows up on my desktop, but it doesn't show up under /media/cdrom0 or under /cdrom.

---

### Post by slimdog360 on 2007-06-20
cd's don't actually mount. The easiest way is to open it with soundjuicer (I prefer grip) and rip the tracks you want onto you hdd. If you want to play the cd from the cd it's self then you have to point the player to /dev/cdrom   it could be called something different on your computer though, so maybe take a look in your /dev folder.

---

### Post by atria on 2007-06-20
You can mount the cd manually though. Use the mount command for that.

For example:

```
mount /dev/cdrom /media/cdrom
```

---

### Post by slimdog360 on 2007-06-20
> **atria said:**
> You can mount the cd manually though. Use the mount command for that.

For example:

```
mount /dev/cdrom /media/cdrom
```

they don't actually have a file system so you can't mount them. Trust me I had a big problem with this in zenwalk and it took me a while to figure it all out.

---

