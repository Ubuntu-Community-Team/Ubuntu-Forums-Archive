---
title: "[SOLVED] quod libet problems"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by chessercizes on 2008-02-23
Hey everyone. So recently, my quod libet just hasn't been starting up at all. I'll click it and it just won't work. I ran "quodlibet" through terminal, and here is the output that i got:
```

me@plutoisaplanet:~$ quodlibet
Supported formats: mod, mp3, mp4, mpc, spc, trueaudio, wav, wavpack, wma, xiph
Traceback (most recent call last):
  File "/usr/bin/quodlibet", line 304, in <module>
    main()
  File "/usr/bin/quodlibet", line 33, in main
    library = load_library()
  File "/usr/bin/quodlibet", line 258, in load_library
    lib = library.init(const.LIBRARY)
  File "/usr/share/quodlibet/library/__init__.py", line 38, in init
    library.load(cache_fn, skip=formats.supported)
  File "/usr/share/quodlibet/library/_library.py", line 124, in load
    try: items = pickle.load(fileobj)
EOFError

```

does anyone know what the problem is? any help would be greatly appreciated.

thanks!

---

### Post by hugmenot on 2008-02-23
```
    try: items = pickle.load(fileobj)
EOFError
```

It looks like trying to load the database, but it gets an end of file error.
Perhaps your database becamne corrupted?

If you move the file ~/.quodlibet/songs out of the way, does it start up then?

---

### Post by chessercizes on 2008-02-23
thanks dude!!
that solved it.

are there any consequences though, by moving the songs file?

---

### Post by hugmenot on 2008-02-23
Well, you lost the volatile tags like playcount, rating or lastplayed.

---

### Post by chessercizes on 2008-02-23
ooh ok. thats fine =D

thanks a lot!!!

---

### Post by Drpat on 2008-02-28
this just happened to me.  since my database is huge, its having to rescan my entire external HD again, which takes hours.  I never thought about backing up this file, but I think I may save a copy of it weekly now.

---

