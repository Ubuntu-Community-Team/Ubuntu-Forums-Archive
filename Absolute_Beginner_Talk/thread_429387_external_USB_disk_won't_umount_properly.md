---
title: "external USB disk won't umount properly"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-05-01
I plugged in an external 30GB disk drive, and feisty recognised it, mounted it as /media/disk, and opened nautilus to view it. It also put an icon on the desk top for it.

The problem is that right clicking on the drive in nautilus and choosing unmount, results in an error that it cannot be ejected, and it remounts automatically, opening yet another nautilus window.

The only way to get it unmounted is to use the command line and

```
sudo umount /media/disk
```

Not a very user friendly experience ubuntu :)

---

### Post by vanadium on 2007-05-01
This is a known bug in Ubuntu Feisty. As indeed it is very visible and annoying, I hope it gets fixed quickly.

A workaround currently is to delete a specific file:

```

mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi.backup

```

(this actually renames the file, so you can recover it)

Reboot after that. This will change the Eject right-click command to an Unmount command. For an USB, this probably is just fine and does not make a difference. For a CD-rom, it means that the drive won be automatically ejected.

---

### Post by ubnewbie2 on 2007-05-01
Thank you.  Definitely a preferable workaround. Like you said, I hope it gets fixed quickly too.

btw:  it did the same thing on a memory card from my camera too. This will fix it for both.

---

### Post by lukew on 2007-05-01
> **ubnewbie2 said:**
> Thank you.  Definitely a preferable workaround. Like you said, I hope it gets fixed quickly too.

btw:  it did the same thing on a memory card from my camera too. This will fix it for both.

You can add an entry for the item within your fstab. You wont need to be root to unmount it then.

Luke

---

### Post by ubnewbie2 on 2007-05-01
Another good suggestion, thanks

---

