---
title: "VLC skins"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Michaelt74 on 2007-03-25
I'm trying to install a new skin for the VLC player. I downloaded the file from the VLC website and followed the instructions, but when I try to copy the file into the folder (Linux users: Put it in ~/.vlc/skins2), I get the following error:

Error while copying to "/usr/share/vlc/skins2". You do not have permissions to write to this folder.

Any ideas on how to write to this folder?

Thanks!

---

### Post by chewearn on 2007-03-25
> **Michaelt74 said:**
> I'm trying to install a new skin for the VLC player. I downloaded the file from the VLC website and followed the instructions, but when I try to copy the file into the folder (Linux users: Put it in ~/.vlc/skins2), I get the following error:

Error while copying to "/usr/share/vlc/skins2". You do not have permissions to write to this folder.

Any ideas on how to write to this folder?

Thanks!

"~/.vlc/skins2" actually means "/home/youruser/.vlc/skins2"

I checked on my system, where vlc has never been using custom skins.  There is actually no "~/.vlc/skins2" directory, so I have to create one:
```
mkdir ~/.vlc/skins2
```

Then copy the skin file there; e.g.
```
cp ~/vplayer.vlt ~/.vlc/skins2/
```

---

### Post by Obor on 2007-03-25
you need to use sudo i.e. sudo cp /path/to/file/filename /path/to/where/
 (if are are copying using the terminal) 
or start nautilus (file manager) with
gksudo nautilus
and it will work.

---

### Post by Michaelt74 on 2007-03-25
Thanks for the assistance, got it working.

---

