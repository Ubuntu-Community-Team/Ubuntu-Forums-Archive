---
title: "file permission"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by wana10 on 2006-06-10
i want to move a tar.gz to a new file and unzip it at that location. When i originally tried to move it it said i dont have permission to write to that location. So i went into the terminal and sudo moved it. Now that its at that location when i try to extract it it tells me once again that i dont have permission to write to that file. so i terminal this
```
sudo tar xjf /usr/lib/win32/file.tar.gz
```
and it extracts to my home folder, not to where the file is
any help would be much appreciated thank you

---

### Post by croak77 on 2006-06-10
You can cd to the directory first.
cd /usr/lib/win32
sudo tar xjf file.tar.gz

---

### Post by wana10 on 2006-06-10
thank you that worked perfectly...but it leaves me with another question.
when i extract the archive it places all the extracted files into their own folder, is it possible to extract into the folder of the archive, instead of into their own folder?
example if not clear:
when i extract the aforementioned file i now have /usr/lib/win32/file/ and in that directory are all of the files
what i want is for all of the files to be in /usr/lib/win32

thanks for the help

---

### Post by taurus on 2006-06-10
[QUOTE=wana10]thank you that worked perfectly...but it leaves me with another question.
when i extract the archive it places all the extracted files into their own folder, is it possible to extract into the folder of the archive, instead of into their own folder?
example if not clear:
when i extract the aforementioned file i now have /usr/lib/win32/file/ and in that directory are all of the files
what i want is for all of the files to be in /usr/lib/win32

thanks for the help[/QUOTE]
Then why don't you move file.tar.gz to /usr/lib.  Extract it.  Then change the whatever name, file, to win32 with
```

mv file win32

```

---

