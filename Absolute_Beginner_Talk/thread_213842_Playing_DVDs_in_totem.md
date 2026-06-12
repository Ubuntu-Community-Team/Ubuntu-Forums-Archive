---
title: "Playing DVDs in totem"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by TheFourElements on 2006-07-11
I can't get totem to play DVDs. in always says "Failed to find mountpoint for device /dev/hdc in /etc/fstab". Any help is appreciated. Thanks.

---

### Post by TheFourElements on 2006-07-12
I know this is lame but....bump

---

### Post by SigmaX on 2006-07-12
Do a
```
more /etc/fstab
```

for starters and we'll see what it's got.

SigmaX

---

### Post by TheFourElements on 2006-07-12
this is what it gave me

```

<file system> <mount point> <type> <options>  <dump>  <pass>
proc          /proc         proc   defaults    0      0
/dev/hda1     /             ext3   defaults,errors=remount -ro 0      1
/dev/hda2     /home         ext3   defaults    0      2
/dev/hda3     none          swap   sw          0      0
/dev/hdc      /media/cdrom0 udf,iso9660 user,noauto  0        0

```

---

### Post by shortbus on 2006-07-13
having the same problem, only here is what i get when I go to play a DVD:

Totem could not play 'dvd:///media/cdrom0'
No URI handler implemented for "dvd".

any suggestions?

---

### Post by Orc65 on 2006-07-13
> **shortbus said:**
> having the same problem, only here is what i get when I go to play a DVD:

Totem could not play 'dvd:///media/cdrom0'
No URI handler implemented for "dvd".

any suggestions?

It's not a codecs issue is it, if so look for "libdvdcss2"

should be in one of the repos listed in this thread, probably the plf repo.
[http://kubuntuforums.net/forums/index.php?topic=6817.0]("http://kubuntuforums.net/forums/index.php?topic=6817.0")

---

### Post by shortbus on 2006-07-13
i was able to install libdvdcss2 with apt-get.. however, i am getting this now:
Totem could not play 'file:///media/cdrom0/video_ts/video_ts.vob'.
You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

BUT, i have all the gstreamer0.10 plugins.. am confused.

---

### Post by TheFourElements on 2006-07-13
> **Orc65 said:**
> It's not a codecs issue is it, if so look for "libdvdcss2"

should be in one of the repos listed in this thread, probably the plf repo.
[http://kubuntuforums.net/forums/index.php?topic=6817.0]("http://kubuntuforums.net/forums/index.php?topic=6817.0")

I already have that installed. I don't think that is the problem

---

### Post by shortbus on 2006-07-13
Ok, I did some digging on the forums and found a fairly easy way to get DVD's to play.. w/o using totem mind you.. try here.

[http://www.ubuntuforums.org/showthread.php?t=177646]("http://www.ubuntuforums.org/showthread.php?t=177646")

Just becareful what you download depending on where you are located.

---

