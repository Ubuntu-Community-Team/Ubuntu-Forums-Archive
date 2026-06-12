---
title: "zsnes 1.42"
date: 2005-09-01
forum: Apple PPC Users
---

### Post by gumara on 2005-09-01
i wont zsnes but not have in repositories (deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main universe multiverse restricted) . if some repositories have zsnes plese tell me.

and i try to install form source by my self.  

i found some problem in last line on $sudo make

/usr/bin/ld: chips/sfxproc.o: Relocations in generic ELF (EM: 3)
chips/sfxproc.o: could not read symbols: File in wrong format
collect2: ld returned 1 exit status
make: *** [zsnes] Error 1
gumara@apple:~/Desktop/zsnes_1_42/src$

---

### Post by GreyFox503 on 2005-09-02
I was able to compile it from source, but check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=38526](http://www.ubuntuforums.org/showthread.php?t=38526)

It looks like you can install it from a .deb.

(see the bottom of poofys' first post)

---

### Post by gumara on 2005-09-03
[QUOTE=GreyFox503]It looks like you can install it from a .deb.[/QUOTE]

i think i can install from .deb but i found znes.deb for .386 only

i don't found zsnes.deb for ppc

---

### Post by GreyFox503 on 2005-09-05
I just added the repositories found at ubuntuguide.org and I have a zsnes listing in synaptic.  However, It's not the most recent version, so I went and downloaded 1.42.

---

### Post by gumara on 2005-09-07
> #deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release powerpc (20050407)]/ hoary main restricted





deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-security main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main universe multiverse restricted

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-security main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main universe multiverse restricted




deb [http://linux.thai.net/apt/](http://linux.thai.net/apt/) ./




my sources.list but i not found.

---

### Post by GreyFox503 on 2005-09-07
You're right.  I dug a little deeper, and the PPC version is not in the repos.  I also searched google and could not find any pre-compiled binaries for PPC.

I can compile the program regularly, so I had an idea to try to compile it for the PPC architecture, but I'm not exactly sure how to do that.

You could always compile it yourself, of course, but I don't know what that error message you're getting means.

---

### Post by GreyFox503 on 2005-09-07
I just thought of something else.  If there's not some particular reason to use zsnes, there's other emulators available, namely snes9x.  It should be available through synaptic, and there's a ppc version.  If it's not in synaptic here's the link:


[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/snes9x/](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/snes9x/)

---

### Post by chrizel on 2005-09-08
zsnes is mostly written in x86 assembler so it won't run on ppc anyway.

---

### Post by GreyFox503 on 2005-09-08
[QUOTE=chrizel]zsnes is mostly written in x86 assembler so it won't run on ppc anyway.[/QUOTE]

 :| 

Well I guess that kinda kills that, doesn't it.

---

### Post by GreyFox503 on 2005-09-09
Something else I just remembered: I had to install a package called 'nasm' in order to compile zsnes,  I didn't know what it was at the time, I just wanted it to work.  But its description reads:  "general purpose x86 assembler".

---

### Post by SKLP on 2005-09-19
[QUOTE=GreyFox503]:| 

Well I guess that kinda kills that, doesn't it.[/QUOTE]
You can always use snes9x... install **snes9express** from the repos.

---

