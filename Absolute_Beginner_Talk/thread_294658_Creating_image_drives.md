---
title: "Creating image drives"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by thecynicality on 2006-11-06
Does anybody know of a good program for linux to create image drives?

---

### Post by Najand on 2006-11-06
Do you mean some programs like daemon-tools in Windows?
If so, there is no need for them, as the mount command is able to mount almost all CD Images (ISO, BIN, ...)
Hmm, a simple command might be:
```

sudo mount -t iso9660 -o loop <CD IMAGE> <MOUNTPOINT>

```

---

### Post by thecynicality on 2006-11-06
Ok can you explain that a little more, what would i put for the mountpoint?

---

### Post by Najand on 2006-11-06
Hmm... It can be simply the name of directory you like to mount your Device/Image on it. If you make a directory in /media you can even see it on the desktop. To summerize it, if would be:
```

# sudo mkdir /media/<DIRECTORY NAME>
# sudo mount -t iso9660 -o loop <IMAGEFILE> /media/<DIRECTORY NAME>

```
Then if you don't get any error, you can
change directory to the directory you made and find your files inside the image.

---

