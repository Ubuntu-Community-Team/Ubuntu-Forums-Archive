---
title: "mkswap - is there a undo option"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by mrspoons on 2007-02-06
Made a big mistake and ran mkswap on my main partition

sudo mkswap /dev/sda2 instead of sudo mkswap /dev/sda3. Is there a way of resetting this back to ext3???

---

### Post by kidders on 2007-02-06
Hi there,

You can turn the filesystem back into an Ext3 one by formatting it again, but if you want to recover your data, you really _should not_ do that. In the interest of data recovery, the less writing you can do to your partition the better. For example, if /dev/sda2 has been actually mounted and used for swapping purposes, you may be in trouble. :-(

Assuming again that you want to get your data back, I would do the following:

[LIST=1]
[*]Stop using /dev/sda2 immediately.
[*]Install a new Linux, and abandon all hope of recovering your *entire* filesystem in its entirety.
[*]Dump an image of the garbaged filesystem to a file, for safe keeping.
[*]Work your way through a few file recovery applications, and concentrate on your personal files (ie the stuff in /home).
[/LIST]

With luck, your /dev/sda2 will be sufficiently undamaged to recover everything. In the worst case scenario, you'll be able to recover files that have not been overwritten, based on their metastructure (I'll get back to that). Basically, you should feel free to try anything you think might work. If you make the situation worse, you can always use **dd** to dump your filesystem image back onto your hard disk, and try again.

**A note on metastructure-based recovery**
Many files have a kind of predictability to the way they're laid out inside ... certain audio, images, documents, compressed archives, etc. This makes them recognisable, no matter how badly chewed up a filesystem is. In the very, very worst case, you will at least be able to recover these, minus their filenames. I'm willing to bet you can do better though. :-)

**Another possibility**
I'd have to look this up to be sure, but it strikes me that it's at least possible you might still have an intact superblock on your /dev/sda2. Much about the Extended filesystems depends on being able to lay hands on a filesystem superblock. If you don't know what I'm talking about, I'd be happy to walk you through trying ... but it's a bit of a long shot.

**Two suggestions**

[LIST]
[*]Keep your backup disk dump for a few months. No matter how successfully you recover it, you may discover something in April that can help you do better!
[*]Next time, consider splitting your Linux install over multiple filesystems. In the event of a corruption (or another accident), much of your data will come out of it completely unscathed.
[/LIST]

---

### Post by kolesarm on 2007-02-24
mrspoons, i had the [same problem]("http://www.ubuntuforums.org/showthread.php?t=366912") - wiped out my main partition four days ago. tried a lot of stuff until i came across [this thread]("http://www.ubuntuforums.org/showthread.php?t=300885"), which solved it - run ```
sudo e2fsck -b 32768 -p /dev/[the partition].
```

---

### Post by kidders on 2007-02-24
Be careful with that one... It would format the partition, potentially making it even more difficult to recover data.

---

