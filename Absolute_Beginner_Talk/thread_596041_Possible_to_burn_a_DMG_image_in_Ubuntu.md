---
title: "Possible to burn a DMG image in Ubuntu?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-10-29
Hi, I've got a DMG image witch I want to burn in Ubuntu. Don't have a mac here to convert it.

Do you guys know some software in the repositories?

Thanks!

---

### Post by hyper_ch on 2007-10-29
did you search the repository for it?

---

### Post by Incense on 2007-10-29
Found a prog on this page [http://vu1tur.eu.org/tools/]("http://vu1tur.eu.org/tools/") called DMG2ISO, not in the repo, and I think you may have to compile it, but it's something at least.

---

### Post by Kosimo on 2007-10-29
> **hyper_ch said:**
> did you search the repository for it?

Yes, I did it but with no success

---

### Post by Kosimo on 2007-10-29
> **Incense said:**
> Found a prog on this page [http://vu1tur.eu.org/tools/]("http://vu1tur.eu.org/tools/") called DMG2ISO, not in the repo, and I think you may have to compile it, but it's something at least.

Cool, gonna have a look it now

Thanks

---

### Post by forezt on 2008-06-09
I can't compile dmg2img. What are the dependencies?

Here's my output:

```
lee@suli-pc:~/Downloads/dmg2img$ make
rm -f dmg2img *~ *.o 
gcc -O3 -c dmg2img.c
In file included from dmg2img.c:28:
dmg2img.h:20:18: error: zlib.h: No such file or directory
In file included from dmg2img.c:28:
dmg2img.h:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘z’
dmg2img.c: In function ‘main’:
dmg2img.c:42: error: ‘Bytef’ undeclared (first use in this function)
dmg2img.c:42: error: (Each undeclared identifier is reported only once
dmg2img.c:42: error: for each function it appears in.)
dmg2img.c:42: error: ‘tmp’ undeclared (first use in this function)
dmg2img.c:42: error: ‘otmp’ undeclared (first use in this function)
dmg2img.c:134: error: expected expression before ‘)’ token
dmg2img.c:135: error: expected expression before ‘)’ token
dmg2img.c:177: error: ‘z’ undeclared (first use in this function)
dmg2img.c:177: error: ‘alloc_func’ undeclared (first use in this function)
dmg2img.c:177: error: expected ‘;’ before numeric constant
dmg2img.c:178: error: ‘free_func’ undeclared (first use in this function)
dmg2img.c:178: error: expected ‘;’ before numeric constant
dmg2img.c:179: error: ‘voidpf’ undeclared (first use in this function)
dmg2img.c:179: error: expected ‘;’ before numeric constant
dmg2img.c:206: error: ‘Z_OK’ undeclared (first use in this function)
dmg2img.c:212: error: expected expression before ‘)’ token
dmg2img.c:213: error: expected expression before ‘)’ token
dmg2img.c:216: error: ‘Z_NO_FLUSH’ undeclared (first use in this function)
dmg2img.c:217: error: ‘Z_STREAM_END’ undeclared (first use in this function)
make: *** [dmg2img.o] Error 1
lee@suli-pc:~/Downloads/dmg2img$ 


```

---

### Post by forezt on 2008-06-09
Figured it out. Had to get the package zlibc.

---

### Post by Ptero-4 on 2008-06-09
You seem to be missing the zlib development library.

---

