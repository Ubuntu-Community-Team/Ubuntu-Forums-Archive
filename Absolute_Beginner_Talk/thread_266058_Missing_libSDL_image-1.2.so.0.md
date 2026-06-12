---
title: "Missing libSDL_image-1.2.so.0"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by docshawnc on 2006-09-26
Hi -
    Important stuff here;)  I'm trying to install a game called Sauerbraten (Cube 2) and have run into a problem - a missing lib.  Here's the msg:
$ ./sauerbraten_unix
./bin_unix/linux_client: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory
    Any help would be greatly appreciated in the getting this game going - tnx in advance:confused:

---

### Post by Dinerty on 2006-09-26
I believe you need all the libSDL -dev packages for that game. Search for "libsdl" in Synaptic Package Manager and install the libsdsl-dev packages, worked for me on that game ;)

---

### Post by DirtDawg on 2006-09-26
EDIT: Nevermind. Damn the posters here are fast!

---

### Post by docshawnc on 2006-09-26
Thanks I'll give that a go.  I was about to try the 'shotgun' approach and install everything that sounded like it might work:)

---

### Post by docshawnc on 2006-09-26
Worked perfectly (60 some-odd files but worth it) - thanks again

---

### Post by pyros on 2006-10-02
> **docshawnc said:**
> Worked perfectly (60 some-odd files but worth it) - thanks again
all that I had to install to get it working on dapper was libsdl-image1.2 and libsdl-mixer1.2

---

### Post by marrabld on 2007-08-03
```
sudo apt-get install libsdl-image1.2 libsdl-mixer1.2
```

Worked for me.

Feisty, AMD64

:)

---

### Post by zhecool on 2007-12-29
> **Dinerty said:**
> I believe you need all the libSDL -dev packages for that game. Search for "libsdl" in Synaptic Package Manager and install the libsdsl-dev packages, worked for me on that game ;)

Thank you so much!
I am playing the game assaultcube!
CS in Linux!:lolflag:

---

### Post by mikerduffy on 2008-01-02
The dev versions are only necessary if you're building from source.  Getting Sauerbraten to work at all seems like a decent accomplishment, though.

---

