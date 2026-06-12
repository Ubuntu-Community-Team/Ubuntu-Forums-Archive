---
title: "How to read an EXT format flash memory in windows XP"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by hotbrainz on 2006-06-21
I have a problem here people.

Well I write embedded software in open source. Now as I use Flash memory for storing this software and it happens to be in EXT format as it works with Linux systems. Now how can i make windows to read this flash memory?

I tried using this [http://www.fs-driver.org/index.html]("http://www.fs-driver.org/index.html")

which happens to be a good method to access ubuntu drives from XP. But it does not work for flash memory unfortunately. Please help, I am a bit desperate here.
Thanks for any suggestions.

---

### Post by richbarna on 2006-06-21
Just a suggestion,
Can't you format it in Fat32 so that it can be read and written to from both windows AND linux?

---

### Post by hotbrainz on 2006-06-21
Well thats a good idea, thanks. but, i have very essential data on it and my boss has a windows system :) I need it bad just this once!

---

### Post by anaconda on 2006-06-21
Have you tried:

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

(I haven't, but it may work.)
Just google "ext3 windows" there are several ext3 reading tools for windows.

And are you sure that
[http://www.fs-driver.org/](http://www.fs-driver.org/)
cant read from flash-memory? I remember reading, that it doesn't support plug-and-play, but if you map a drive-letter to it, then you can accerss your ext3 removable disk.. Just remember to unmap it before you remove it.  And I also remember, that there was a workaround for that, so that you dont have to map/unmap it manually...

Yep here is a link:
[http://www.fs-driver.org/relnotes.html](http://www.fs-driver.org/relnotes.html)
IT is about USB-hard-drives, but I suppose your flash-memory works the same way. (maybe it is a good idea to test if it works somewhere else before going to your bosses windows machine......)

---

### Post by hotbrainz on 2006-06-21
Many thanks anaconda. I got it working !

---

