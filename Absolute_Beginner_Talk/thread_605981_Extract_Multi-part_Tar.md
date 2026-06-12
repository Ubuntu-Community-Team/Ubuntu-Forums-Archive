---
title: "Extract Multi-part Tar"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Raptor45 on 2007-11-07
I created an uncompressed tar using 7zip so I could easily transfer a bunch of files to my laptop. Now I can't figure out how to get Ubuntu to extract them from the .001 to .004 files. Can anyone help?

---

### Post by kellemes on 2007-11-07
[http://unixhelp.ed.ac.uk/CGI/man-cgi?tar]("http://unixhelp.ed.ac.uk/CGI/man-cgi?tar")

It's probably the -M switch you're interested in..

---

### Post by mali2297 on 2007-11-07
> **Raptor45 said:**
> I created an uncompressed tar using 7zip so I could easily transfer a bunch of files to my laptop. Now I can't figure out how to get Ubuntu to extract them from the .001 to .004 files. Can anyone help?

I don't use 7zip, but in the terminal you could try
```

tar -xvM -f archivename.tar.001 -f archivename.tar.002 -f archivename.tar.003 -f archivename.tar.004

```

---

### Post by bigdidz on 2008-01-12
I figured it out!!  I don't know if there's a visual way to do it but if I did it; it's because is easy.

first, install 7-zip

> sudo apt-get install p7zip-full

after, browser into the correct directory:

> cd /the_place

than, use 7-zip to untar it.

> 7z x file.tar.001

N.B.: only write the first one even if you have tons on them.

So, this is how it did worked for me

---

### Post by mohaakilla51 on 2008-03-22
So, yeah, if you used 7zip to compress, it seems the linux tar command won't recognize the next file, even if you use the -M switch, so use the above method

---

