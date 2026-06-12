---
title: "Custom command for dumping the contents of one folder into another."
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-17
Does anyone know what the terminal command would be for dumping the contents of /home/rngetter/Shared to /home/rngetter/Music would be? Also, how would I go about turning this into a custom command? I think it has something to do with writing it to a file and naming it .conf, but im' not exactly sure and might be talking out of my a*s. I'd like to make my own command called somethin' like unshare, so that all I have to to is type that into my terminal, hit enter, and have it happen. I think this is called writing a script? IDK please correct my errors and answer my questions. Thanks.

---

### Post by jken146 on 2008-03-17
Are you talking about copying all the files that are in one directory into a directory somewhere else?  If so then:
```
cp -r pathToDirectoryOne/* pathToDirectoryTwo/
```

If you want to move them (deleting the originals), replace *cp* with *mv*.

---

### Post by whoscheesemine on 2008-03-17
now how would I script that to one command?

---

### Post by handydan918 on 2008-03-18
Open an editor (gedit?)
Do
```
#!/bin/bash
cp -r pathToDirectoryOne/* pathToDirectoryTwo/
```

Save as <filename>
Make executable.
If the directory to be written to is owned by root, it will require sudo to work.

---

### Post by whoscheesemine on 2008-03-18
> **handydan918 said:**
> Open an editor (gedit?)
Do
```
#!/bin/bash
cp -r pathToDirectoryOne/* pathToDirectoryTwo/
```

Save as <filename>
Make executable.
If the directory to be written to is owned by root, it will require sudo to work.

How do I make it executable? The only way I knew how to do that was in windows naming something .exe

---

### Post by handydan918 on 2008-03-18
```
chmod 755 <filename>
```

---

