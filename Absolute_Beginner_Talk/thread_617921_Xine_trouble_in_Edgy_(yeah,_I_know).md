---
title: "Xine trouble in Edgy (yeah, I know)"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Canew on 2007-11-19
Hi:

I installed Edgy a while ago and haven't had properly-working sound since. I know Edgy is an older version, but until I find a way to backup my data, I can't upgrade, which leaves me stuck with this for now. 

Anyway, for some reason the xine library doesn't appear to be present in my system, so I go to xinehq and download it. I open the package with the package manager, leaves a file folder on my Desktop. I go into terminal, go into the file, type ./configure, and I get this:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking build system type... (cached) i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

Huh? This is really frustrating. I never got DVDs to work right, and now this. Now I have no sound at all, and when I try to fix it... :(

---

### Post by Abild on 2007-11-19
Why don't just install xine from the repositories?
sudo apt-get install xine-ui libxine-extracodecs

---

