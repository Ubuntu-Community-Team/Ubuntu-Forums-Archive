---
title: "ELF Classes and mupen64"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-10-29
Hello!

I downloaded the tar.gz package for mupen64 from [their website]("http://mupen64.emulation64.com/"), and I'm having trouble installing it.

I had tried this before, and I was getting nowhere, so I decided to redownload it and try this on edgy.

I downloaded all of the SDL packages from synaptic, as this package requires them. However, I'm receiving this errorwhen I use ./mupen64 in the mupen64 path:

```
grant@Grant:~/Desktop/mupen64-0.5$ ./mupen64
./mupen64: error while loading shared libraries: libSDL-1.2.so.0: wrong ELF class: ELFCLASS64

```

I don't know what an ELF CLASS is, so I don't know how to fix this problem.

I did find [this]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fsupport.esri.com%2Findex.cfm%3Ffa%3Dknowledgebase.techarticles.articleShow%26d%3D26850&ei=1ghFRcudM5byoQKx5_zqCQ&usg=__ju4WmVtakJz-NOGNNNvisLwE7ew=&sig2=QbZ6-QrSsOE1GWjaQ1Co4Q") web article that says that their are 64 bit apps getting in the way of installing it, as I have a 64-bit architecture. Any ideas here?

Thank you!

---

### Post by ChekhovTheAnton on 2007-08-17
I had the same problem.  Thanks to your link, I was able to find something that helped.

Go to Synaptic and install ia32-libs-sdl.  It allowed mupen64 to open for me, at least.

---

