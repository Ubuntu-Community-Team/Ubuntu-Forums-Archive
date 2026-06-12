---
title: "Cube"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by greyash99 on 2006-07-16
How do I install Cube?  I have it downloaded and I tried ./configure, make, make install but it still doesn't work.

---

### Post by Jagot on 2006-07-16
Have you followed this guide:

[http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source)

Are you sure you had build-essential installed?

---

### Post by greyash99 on 2006-07-16
It still didnt work.  I think it said I had to chmod +x the binaries but when I tried "chmod +x file:///home/greyson/Desktop/cube/cube_unix", the terminal acted like it didnt do anything.

---

### Post by Jagot on 2006-07-16
When you chmod +x something you're making it executable - it won't give you any feedback.  Usually after this you will need to run the file:

```
./filename
```

---

### Post by greyash99 on 2006-07-16
It now says no such file or directory when I try ./file:///home/greyson/Desktop/cube/cube_unix

---

### Post by Jagot on 2006-07-16
Is there no readme file in there at all?

---

### Post by greyash99 on 2006-07-16
not one that's helpful............sorry I'm really new at this and thanks for the help so far.

---

### Post by Jagot on 2006-07-16
No need to apologise.  Can you tell me what files are in the directory?  I would download it myself but I'm on a Windows machine at the moment.  Just navigate to the directory in Terminal and use the command ls to list the files in there.

---

### Post by greyash99 on 2006-07-16
this is what the terminal says  "cube_unix  demos  packages     savegames
bin_unix      data       docs   readme.html  screenshots" and the readme is no help.

---

### Post by Jagot on 2006-07-16
Not sure if these might be of any help:

[http://ubuntuforums.org/showthread.php?t=172436](http://ubuntuforums.org/showthread.php?t=172436)
[http://ubuntuforums.org/showthread.php?t=6040](http://ubuntuforums.org/showthread.php?t=6040)

---

