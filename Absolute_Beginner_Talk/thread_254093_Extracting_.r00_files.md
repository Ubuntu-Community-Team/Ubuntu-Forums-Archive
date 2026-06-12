---
title: "Extracting .r00 files"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by D_frag on 2006-09-09
I tried extracting a .r00 archive but i got archive type not supported any specific software to use to solve this ??

---

### Post by jordanmthomas on 2006-09-09
I believe that is part of a mult-part rar file.  So you will need to have something like a .r01 and so on in the same directory.

You need to enable multiverse (you can find out how at [http://www.ubuntuguide.org](http://www.ubuntuguide.org))
Then install unrar from the archives
```

sudo apt-get update
sudo apt-get install unrar
```

---

### Post by kh4nh on 2006-09-09
This is Rar archive, you need to install unrar
```

sudo aptitute install unrar

```

after installing, in the prompt type

```

unrar e "files"

```

---

