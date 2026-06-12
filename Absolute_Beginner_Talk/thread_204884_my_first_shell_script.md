---
title: "my first shell script"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by skale on 2006-06-27
> #ripping mp3 cds to music folder
sudo cp -rv /cdrom/* /media/hda1/Music/
echo "Complete"
umount /cdrom && eject

Worked!

Of course, it ejected the wrong cd drive...
How do I fix that?:confused:

---

### Post by xtacocorex on 2006-06-27
I've never tried this before, but from the man page on eject it says that you can use
> The device corresponding to <name> is ejected. The name can be a device file or mount point, either a full path or with the leading "/dev", "/media" or "/mnt" omitted. If no name is specified, the default name "cdrom" is used.

You won't need to worry about unmounting it as it does it automatically.

Hope this helps some. Other than what I have, I'm out of ideas.

---

