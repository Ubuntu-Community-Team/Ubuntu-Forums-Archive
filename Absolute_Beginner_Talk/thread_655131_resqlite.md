---
title: "re:sqlite"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by muchane on 2008-01-01
I just wanted to know whether there is another way of adding packages apart from the repositories.  Cant I use another os to download a package and then use it on the Gutsy?The sqlite3.bin file lies tantalizingly on the Desktop but I cant use it!

---

### Post by taurus on 2008-01-01
What happens if you run

Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 sqlite3.bin
./sqlite3.bin
```

---

### Post by The Cog on 2008-01-01
Is there any reason you don't want ot use the repositories? It is the recommended way, because the install scripts also do a lot of configuring for you, as well as just installing the correct binaries.

---

### Post by llamakc on 2008-01-01
sqlite3 - A command line interface for SQLite 3

It's in  the Universe repository.

---

