---
title: "Problem with Korean characters from OS X"
date: 2006-06-07
forum: Apple PPC Users
---

### Post by &#12465;&#12452;&#12488; on 2006-06-07
I mounted my music directory with the command ```
sudo mount -w -t hfsplus /dev/hdb7 /media/COWBOY/
```, but it didn't mount in read/write mode. Being lazy, I decided to do a recursive chmod on the whole mount. That's when I discovered this problem.

```
chmod: cannot access `/media/COWBOY/Music/BoA/Girls on Top/04 &#50724;&#45720; &#44536;&#45832; &#48376;&#45796;&#47732;(If you were here).mp3': No such file or directory
chmod: cannot access `/media/COWBOY/Music/BoA/Girls on Top/06 Addiction(&#51665;&#52265;).mp3': No such file or directory
chmod: cannot access `/media/COWBOY/Music/BoA/Girls on Top/08 &#44277;&#51473;&#51221;&#50896; (Garden In the Air).mp3': No such file or directory
```

All filenames with Korean characters in them didn't work. I tried entering the directory above with Nautilus, and once I clicked on the file, it disappeared. Doesn't Mac OS X write Korean characters compatible with UTF-8? I know OS X uses a modified version of UTF-8, but it's supposed to work the same way, from what I've read.

Have anyone bumped into the same problem? Are there any good solutions? I want to listen to my Korean music!

---

### Post by morequarky on 2006-06-07
"chmod"

Is there a permission issue?

When I am using English windows I can't access my Korean PDA's korean named flash card folder.  SO frustrating.

---

### Post by &#12465;&#12452;&#12488; on 2006-06-08
[QUOTE=morequarky]Is there a permission issue?[/QUOTE]
I am quite sure it is an encoding issue. When I mount the partition, the files aren't readable nor writeable, but all files without Korean characters work after chmoding (which includes several Scandinavian languages, Japanese and Chinese).

Ah, also, files and folders with Korean names don't work before the chmodding either. I added a few folders with hangul characters in OS X earlier today, and they show up with the same GNOME foot icon that the files in the BoA folder had.

I guess I'll have to copy my Korean stuff into Ubuntu via SMB or something, but that is just *so* inconvient, having to duplicate everything!

---

### Post by morequarky on 2006-06-08
I am guessing your ubuntu can type korean.

Definitly an encoding thing.  Have you tried a Korean Forum in Korea? They probably have a solution.

---

