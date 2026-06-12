---
title: "how do I determine the installed utilites? (already read other posts on this)"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by rv2internet on 2007-07-21
How do I determine which utilities I have installed?

I looked though Synaptic Package Manager and I'm sure some have been installed as I hacked my way though terminal, yet I don't see them...

I'm looking for those on the list below:

fakeroot
gcc
binutils
patch
sed
tar
gzip
bzip2
lzma
flex
bison
make
autoconf
gettext
pkg-config
unzip
libz-dev 
libc headers

---

### Post by koganinja89 on 2007-07-21
by default all of those except fake root should be installed already

---

### Post by Mr. C. on 2007-07-21
Use the locate or find commands:

```
locate gcc
find / -name gcc
```

MrC

---

### Post by rv2internet on 2007-07-21
Great responses, I tried that and for some of the searched was overwhelmed with responses. I couldn't be sure that they were relevant...

(Just trying to follow directions of a system developers kit)

It would seem I have another problem.

---

### Post by Mr. C. on 2007-07-21
Some utilities will help identify themselves:

```
gcc --version
```

Most programs are stored in some bin directory.  To weed out the extraneous files, use:

```
locate bin/gcc
```

To see if a utility is in your PATH somewhere, and where:

```
which gcc
```

MrC

---

