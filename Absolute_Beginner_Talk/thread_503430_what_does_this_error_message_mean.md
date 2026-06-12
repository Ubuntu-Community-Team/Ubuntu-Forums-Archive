---
title: "what does this error message mean?"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by jakelaptop on 2007-07-17
and how do I fix it?

when i run sudo apt-get upgrade i get this error message at the end:

Unpacking replacement libcurl3-gnutls ...
Setting up libcurl3 (7.15.5-1ubuntu2.1) ...
ldconfig: /usr/lib/libSDL_ttf-2.0.so.0.6.2 is not an ELF file - it has the wrong magic bytes at the start.

the last line repeats itself a dozen or so times.

---

### Post by sab0403 on 2007-07-17
ELF is the [Executable and Linkable Format]("http://en.wikipedia.org/wiki/Executable_and_Linkable_Format"). What this error message is telling you is that the file that was downloaded is not an executable one - hence it cannot be installed.

As to *why* it comes up, probably some error in the repositories...

---

### Post by davidjmayo on 2007-07-18
>  libcurl3 (7.15.5-1ubuntu2.1) ...

This was an update package yesterday (17 Jul)

Seems like it didn't go correctly.

look in synaptic (System==>administration==>synaptic package manager) and see if there are any broken packages. If there are then edit menu==>fix broken packages

---

### Post by Jimmyfj on 2007-07-18
> **davidjmayo said:**
> This was an update package yesterday (17 Jul)

Seems like it didn't go correctly.

look in synaptic (System==>administration==>synaptic package manager) and see if there are any broken packages. If there are then edit menu==>fix broken packages

I got that update just yesterday and it went through just fine - It installed as it should without any errors. My update held two different files with that name and they were, as I said, installed correctly. So I'd say you had a download error of some kind.

---

### Post by davidjmayo on 2007-07-18
thanks Jimmyfj

I should have mentioned that too. I had no problems with the update and yes it was 2 files.

---

