---
title: "Encrypted Disc?"
date: 2005-08-23
forum: Absolute Beginner Talk
---

### Post by Ubunut on 2005-08-23
Is there any way of installing an encrypted disc program the same as PGP Disc? In Mandriva they have something called Drakloop, that I think does the same thing, but there does not seem to be anything in Ubuntu for encrypted discs.

---

### Post by amastronardi on 2005-08-23
I would suggest EncFS, it runs really good and you don't need to create a fixed size file. It is a really transparent encrypted filesystem.

It uses fuse (filesystem in userspace).

I compiled it by hand in my ubuntu notebook, but I did using packages in a debian box. You should need to install: libfuse2, fuse-source and fuse-utils packages and recompile the kernel to get fuse running. Later you will need to install encfs package too.

You can find more information here: [http://arg0.net/wiki/encfs](http://arg0.net/wiki/encfs)

Let me know if you need more information/help.

Cheers, Adrian.

---

### Post by Ubunut on 2005-08-24
[QUOTE=amastronardi]I would suggest EncFS, it runs really good and you don't need to create a fixed size file. It is a really transparent encrypted filesystem.

It uses fuse (filesystem in userspace).

I compiled it by hand in my ubuntu notebook, but I did using packages in a debian box. You should need to install: libfuse2, fuse-source and fuse-utils packages and recompile the kernel to get fuse running. Later you will need to install encfs package too.

You can find more information here: [http://arg0.net/wiki/encfs](http://arg0.net/wiki/encfs)

Let me know if you need more information/help.

Cheers, Adrian.[/QUOTE]

Thanks Adrian, sounds good! But maybe a little complicated for a noob like me? Recompiling kernels is something the clever guys do! Besides, I have an nVIDIA card, which has certain kernel needs as well, won't recompiling affect the graphics driver too?

---

### Post by amastronardi on 2005-08-24
[QUOTE=Ubunut]Thanks Adrian, sounds good! But maybe a little complicated for a noob like me? Recompiling kernels is something the clever guys do! Besides, I have an nVIDIA card, which has certain kernel needs as well, won't recompiling affect the graphics driver too?[/QUOTE]

Don't think so, it depends on the method you have used to compile it.
How have you done it?

Cheers, Adrian.

---

