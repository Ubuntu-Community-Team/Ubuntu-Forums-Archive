---
title: "[SOLVED] AVI to MPEG converter"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Bob_12 on 2007-11-23
I want to burn some videos that are in .avi format as video dvds in k3b and I think I need to convert them to mpeg. Any ideas how? Thanks a lot in advance!

---

### Post by MrFSL on 2007-11-23
Install ffmpeg:
```
sudo apt-get update
sudo apt-get install ffmpeg
```

Convert to dvd compliant vob:
```
ffmpeg -i InputFile.avi -target ntsc-dvd -sameq OutputFile.vob
```

---

### Post by lunaluna on 2008-04-21
> **MrFSL said:**
> Install ffmpeg:
```
sudo apt-get update
sudo apt-get install ffmpeg
```

Convert to dvd compliant vob:
```
ffmpeg -i InputFile.avi -target ntsc-dvd -sameq OutputFile.vob
```

"file" i guess it must be the whole path? right
because im dealing with some problems....

---

