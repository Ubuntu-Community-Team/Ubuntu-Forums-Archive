---
title: "Changing Mount Permissions via root"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Azslande on 2007-08-11
I have my Windows C partition mounted so that linux can see it. The problem is, I cant access the partition, because it says I dont have the right permissions. I know I can change these permissions by going root and then using Chmod to change the permissions (I believe, right?). So my question is, where do I want to change the permissions. Should I change it under here ```
/mnt/windows_c
``` or should I go into ```
/dev/
``` and change the drive? Yes I am a bit of a noob so If I just totally made a fool of myself its ok lol.

---

### Post by BitTorrentBuddha on 2007-08-11
You should change the permissions of the mount point (/mnt/windows_c). ```

sudo chmod 777 /mnt/windows_c
```
Or you can change the owner to yourself, which I recommend over leaving the permissions open to anyone.```

sudo chown $USERNAME:$USERNAME /mnt/windows_c
```

---

