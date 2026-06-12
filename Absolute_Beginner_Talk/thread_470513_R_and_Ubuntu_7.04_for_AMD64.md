---
title: "R and Ubuntu 7.04 for AMD64"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Alunah on 2007-06-11
Hi!

I'm absolutely new at Linux.  I've been trying to install R in my PC over Ubuntu 7.04 for AMD64.  I just can't do it.  I want to know if the package is available for this version, because in the FAQ appears only the 

               CPU   Versions                 Provider  

Ubuntu  i386  dapper/edgy/feisty  Vincent Goulet  

version.  If it exists, where can I download it?


Thanks in advance. 

Angela

---

### Post by Pragmatist on 2007-06-11
What is "R"?

---

### Post by ugm6hr on 2007-06-11
> **Pragmatist said:**
> What is "R"?

I believe it's a powerful open source statistical program.  I should really try and use it some day.....

---

### Post by Dedoimedo on 2007-06-11
Are you talking about the R language? 

Here's the page, tons of mirrors.
[http://www.r-project.org/](http://www.r-project.org/)

Dedoimedo

---

### Post by vanadium on 2007-06-11
This will most likely work

[http://packages.debian.org/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Ff%2Ffoptions%2Fr-cran-foptions_240.10068-1_amd64.deb&md5sum=734a12068dd573f78843812f17b0481b&arch=amd64&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Ff%2Ffoptions%2Fr-cran-foptions_240.10068-1_amd64.deb&md5sum=734a12068dd573f78843812f17b0481b&arch=amd64&type=main)

Tip: all I did was type r-cran amd64 in google.

---

### Post by Alunah on 2007-06-11
> **vanadium said:**
> This will most likely work

[http://packages.debian.org/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Ff%2Ffoptions%2Fr-cran-foptions_240.10068-1_amd64.deb&md5sum=734a12068dd573f78843812f17b0481b&arch=amd64&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Ff%2Ffoptions%2Fr-cran-foptions_240.10068-1_amd64.deb&md5sum=734a12068dd573f78843812f17b0481b&arch=amd64&type=main)

Tip: all I did was type r-cran amd64 in google.

Thanks... this is my problem, It seems like the binaries sources and the packages are available and tested, for AMD64 architectures, only for Debian and I'm working with Ubuntu 7.04 (feisty)...

Do you think it's better for me to move from Ubuntu to Debian?

Thanks

---

### Post by Terl on 2007-06-11
Ubuntu is based on Debian.  Have you tried to install the deb package?  It should work.

---

