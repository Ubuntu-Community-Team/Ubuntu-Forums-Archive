---
title: "New Metapixel GUI in Mono/C#"
date: 2008-12-14
forum: Art &amp; Design
---

### Post by gerbman on 2008-12-14
Hello,

I've released a GUI front-end for the [Metapixel]("http://www.complang.tuwien.ac.at/schani/metapixel") photo mosaic creator. It's written in C# and runs on Mono. You can read more about it [here]("http://links.cse.msu.edu:8000/members/matt_gerber/index.php/Software#MetaPixel_GUI").

I'm working on getting it into the repos, but that might take a while. In the meantime, I've provided a compiled binary that runs directly on Mono.

Cheers!

---

### Post by directhex on 2008-12-14
Screenshots would be nice

---

### Post by gerbman on 2008-12-14
> **directhex said:**
> Screenshots would be nice

Done.

---

### Post by eightmillion on 2008-12-14
Very cool. Thanks. Pfind is interesting also. I've always thought that the find command was overly complicated.

---

### Post by gerbman on 2008-12-14
> **eightmillion said:**
> Very cool. Thanks. Pfind is interesting also. I've always thought that the find command was overly complicated.You're welcome  :)

---

### Post by exactt on 2011-02-19
hi gerbman,

are you still maintaining the program? i get an error message running the programm under Ubuntu 10.10. just when i hit the button "create mosaic".

"Failed to produce mosaic. Error message: height of small images must be positive."

cheers

---

### Post by gerbman on 2011-02-19
> **exactt said:**
> hi gerbman,

are you still maintaining the program? i get an error message running the programm under Ubuntu 10.10. just when i hit the button "create mosaic".

"Failed to produce mosaic. Error message: height of small images must be positive."

cheers

Hi exactt,

Yes, I still keep an eye on that software. I just tried it again with with Ubuntu 10.04 and Mono 2.8. Everything seems to be working fine. I have two questions:

1) What version of Mono are you using? (mono --version)

2) Can you send me a screenshot of the settings you used on the GUI? Maybe I can track down the problem.

Best,
gerbman

EDIT:  I also tried it with Ubuntu 10.04 and Mono 2.4.4 - worked fine.

---

### Post by exactt on 2011-02-20
hi gerbman,

thx for your reply:

Mono JIT compiler version 2.6.7 (Debian 2.6.7-3ubuntu1)
Copyright (C) 2002-2010 Novell, Inc and Contributors. [www.mono-project.com](www.mono-project.com)
	TLS:           __thread
	GC:            Included Boehm (with typed GC and Parallel Mark)
	SIGSEGV:       altstack
	Notifications: epoll
	Architecture:  amd64
	Disabled:      none

I am running ubuntu 10.10 amd64.

I used the default settings: picked a picture. created a library(133 JPEGs). hit "create mosaic(s)".

anything else i can provide?

---

### Post by exactt on 2011-02-20
p.s. all my JPEGs have been resized to PNGs in the library folder. is this conversion to a different file format happening on purpose?

p.p.s. would be great if the image conversion for the library would use multiple cores...

---

### Post by gerbman on 2011-02-20
> **exactt said:**
> hi gerbman,

thx for your reply:

Mono JIT compiler version 2.6.7 (Debian 2.6.7-3ubuntu1)
Copyright (C) 2002-2010 Novell, Inc and Contributors. [www.mono-project.com](www.mono-project.com)
	TLS:           __thread
	GC:            Included Boehm (with typed GC and Parallel Mark)
	SIGSEGV:       altstack
	Notifications: epoll
	Architecture:  amd64
	Disabled:      none

I am running ubuntu 10.10 amd64.

I used the default settings: picked a picture. created a library(133 JPEGs). hit "create mosaic(s)".

anything else i can provide?

I really don't see anything there that would be causing problems. I haven't tested the program on a 64-bit system. If you can try the same thing on a 32-bit system that might be helpful. Also, can you post a screenshot of the final screen (the one with the size options)?

---

### Post by gerbman on 2011-02-20
> **exactt said:**
> p.s. all my JPEGs have been resized to PNGs in the library folder. is this conversion to a different file format happening on purpose?

Yes, metapixel (the program that actually does all the work) converts the images to PNG files first.

> p.p.s. would be great if the image conversion for the library would use multiple cores...

Yup, that would be nice. My program is just a front-end for metapixel, which doesn't seem to be actively developed. Who knows if multiple cores will be supported at some point.

---

### Post by exactt on 2011-02-20
here you go with the screenshot. same problem on 32-bit installation of ubuntu maverick..

---

### Post by gerbman on 2011-02-20
> **exactt said:**
> here you go with the screenshot. same problem on 32-bit installation of ubuntu maverick..

Everything looks fine there. Have you tried used different dimensions for the mosaic width/height and sub-image width? Same result?

I'm out of ideas, sorry. If you really want to know what's wrong, you can download the source code and debug it. Or you can provide me with your images and I'll debug it myself.

---

