---
title: "[SOLVED] How Do I Find All Files on my File System That Contain A Given Word?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by MountainX on 2008-04-04
I want to do a search for files that contain a certain word (in the content inside the file, not in the filename). I would like to search everywhere except on network shares. How can I do that? Thanks.

---

### Post by Inxsible on 2008-04-04
I think, and I could be wrong, but the find command does search within files too. don't rbr the exact flags needed. :(```
man find
```

---

### Post by wolfen69 on 2008-04-04
```
locate name_of_file
```

---

### Post by herbster on 2008-04-04
```
grep -lir 'texttofind' *
```

Might work.

---

### Post by MountainX on 2008-04-04
It turns out that I was able to do this:

sudo updatedb
locate /path string

---

### Post by MountainX on 2008-04-04
> **herbster said:**
> ```
grep -lir 'texttofind' *
```

Might work.

Thanks. I had been trying to use either find (man find was no help) or grep. I ended up using locate, but I'll try grep next time.

---

