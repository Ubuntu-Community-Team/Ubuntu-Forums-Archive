---
title: "glibc"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by jsolomon on 2006-09-20
This might sound like a stupid question. I am new to linux and I would like to compile programs that I've written in c. I know how to compile on a unix command using gcc. When I try to compile on my ubuntu box i'm coming up with all sorts of errors and missing dependencies. I believe it might be due to the c library. I downloaded glibc-2.4 and unzipped it and tar'ed it. Do i need to make any changes to the configurations? I'm not sure where to go from here with this. Any help would be great. Thanks.

---

### Post by croak77 on 2006-09-20
Just use the repo's. The package is called libglib2.0-0. But you should install libglib2.0-0-dev if you are compiling something against libglib2.0-0.

---

### Post by skymt on 2006-09-20
> **croak77 said:**
> Just use the repo's. The package is called libglib2.0-0. But you should install libglib2.0-0-dev if you are compiling something against libglib2.0-0.

No, that's glib. glibc is in "libc6".

---

### Post by croak77 on 2006-09-20
Yes. Sorry my bad. I saw glib. Had a brainfart. So install libc6-dev

---

### Post by jsolomon on 2006-09-21
Thank you guys.  This helps out so much.  How did you know to install the package libc6-dev?

---

