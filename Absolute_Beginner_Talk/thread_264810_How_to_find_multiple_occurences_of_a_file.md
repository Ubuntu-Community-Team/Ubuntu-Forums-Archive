---
title: "How to find multiple occurences of a file"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by DOD1951 on 2006-09-25
Anyone know of a program that actually finds all occurences of a given file name please? When I first installed Ubuntu there was this neat search program that did the job. Somewhere along the line it has been replaced by another search program that is not very useful. Im looking for something that tells me where all files with the same name are located so I can delete them i.e I want to delete all the Thumbs.db files that were loaded when i copied my music folders from windows. I know I have around a 1000 of these and don't want to manually go into each directory to find it and delete it. Oh and before anyone mentions it the search function in file browser only tells me size, type, date modified, date accesed and owner but no location.

---

### Post by lamego on 2006-09-25
It is easy to do that from the terminal:
```
sudo find / -name "filename" -exec ls -la {} \;
```

If you want to remove them (IF YOU PUT THE WRONG NAME IT WILL BE DELETED).
```
sudo find / -name "filename" -exec rm -f {} \;
```

---

### Post by mitch.c on 2006-09-25
> **DOD1951 said:**
> I want to delete all the Thumbs.db files that were loaded when i copied my music folders from windows.
```
find /path/to/music/folders -name "Thumbs.db" -print0 | xargs -0 rm -f
```
As for duplicate files, I don't know what program/script you had before, but a quick Google should find one.

---

