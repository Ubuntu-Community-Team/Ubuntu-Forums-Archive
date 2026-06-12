---
title: "tarball not compiling! pls help."
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by paulgault on 2007-09-25
Hi, 
i'm trying to install the latest stable version of the usenet reader pan as [this forum]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/578168.html") says it is "much more advanced than the one in the Ubuntu repository".
i'm a linux noob and i'm having trouble compiling the source etc.
as far as i understand it the basic procedure is to unzip the .tar.gz file and type the following into a console once you've changed into the directory that was unziped.
```
./configure
make
sudo make install
```
i had to run the ./configure command several times as it would halt saying i needed a certain package so i would go get it and install it. 
i think the ./configure was ok. it didn't display any confirmation or anything at the end, just this
```
Configuration:

        Source code location:   .
        Compiler:               gcc
        GtkSpell enabled:       no

```

when i try to run the make command to compile it i get a load of error messages 

```
msort.c:68: error: invalid lvalue in increment
msort.c:69: error: invalid lvalue in increment
msort.c:74: error: invalid lvalue in increment
msort.c:75: error: invalid lvalue in increment
make[3]: *** [msort.o] Error 1
make[3]: Leaving directory `/home/paul/pan-0.14.2/pan/base'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/paul/pan-0.14.2/pan'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/paul/pan-0.14.2'
make: *** [all-recursive-am] Error 2
```

i've not got a clue as to what they mean or what i need to do to get the thing up and running.
any help would be much appreciated!
thanks,
Paul.

---

### Post by master_kernel on 2007-09-25
Try running sudo make.

---

### Post by master_kernel on 2007-09-25
It seems like an error in the program itself, but try running everything as root.

---

### Post by reckless2k2 on 2007-09-25
in the tar file it should have a README file or on the site will talk about dependencies. you see when you install via the package manager it resolves the dependencies. if you install from source you will have to manually add things. find out the dependencies and add them via synaptic. 

also, make sure you have build-essential installed via synaptic. looks like you might though.

---

### Post by reckless2k2 on 2007-09-25
um..yeah ignore me. i didn't read this right. hahaha. try sudo and the program then. hahaha.if it works then you would SUID the program.

---

### Post by qamelian on 2007-09-25
The post that say thlatest stable version is more advanced was made over a year ago. a lot of things can change in a year!:)

Exactly what functionality ar you missing that leads you to think you need something newer than the version included in the Ubuntu repos? The forum thread you linked to was specifically talking about nzb support in Pan. The version in the Ubuntu repos has had nzb file support for a while.

---

### Post by paulgault on 2007-09-25
the readme says the dependencies are 
REQUIREMENTS

    Pan requires three libraries:
    * gtk2 2.2.0 or higher <http://www.gtk.org>
    * GNet 1.1.8 or higher <http://www.gnetlibrary.org>
    * libxml2 2.4.22 or higher <http://www.xmlsoft.org>

and i'm pretty sure i've got those already

i'm trying to get download with nzb files (i'm also a usenet noob!) i tried the repository version of pan. i downloaded my nzb, went to file -> import nzb, selected the .nzb file, it asked me where it should save the atachments and then done nothing!

i scratched my head and [googled it]("http://www.google.co.uk/search?hl=en&q=nzb+pan&btnG=Google+Search&meta="). i came across the forum i linked above (i didn't notice that it was old). i just assumed that it wasn't working because the repo version didn't support nzb's.

maybe i'm not using the nzb properly!!

---

### Post by qamelian on 2007-09-25
> **paulgault said:**
> the readme says the dependencies are 
REQUIREMENTS

    Pan requires three libraries:
    * gtk2 2.2.0 or higher <http://www.gtk.org>
    * GNet 1.1.8 or higher <http://www.gnetlibrary.org>
    * libxml2 2.4.22 or higher <http://www.xmlsoft.org>

and i'm pretty sure i've got those already

i'm trying to get download with nzb files (i'm also a usenet noob!) i tried the repository version of pan. i downloaded my nzb, went to file -> import nzb, selected the .nzb file, it asked me where it should save the atachments and then done nothing!

i scratched my head and [googled it]("http://www.google.co.uk/search?hl=en&q=nzb+pan&btnG=Google+Search&meta="). i came across the forum i linked above (i didn't notice that it was old). i just assumed that it wasn't working because the repo version didn't support nzb's.

maybe i'm not using the nzb properly!!
That's strange. I'm using the version of Pan from the Ubuntu repos and it handles nzbs just fine for me, following the same procedure you described. 

Have you opened the Pan task manager to see if anything has been queued?

---

### Post by paulgault on 2007-09-25
i've just tried a different .nzb on the repository pan and it worked fine. after a little digging it looks like only the nzb was posted at alt.binaries.documentaries (it's a michael palin travel documentary i'm after) but the actual files are on alt.binaries.tv 
alt.binaries.tv does not show on my list (only using my isp usenet server at the mo) so maybe pan can't find anything in the nzb file and doesn't bother with an error message and just does nothing!
maybe...
looks like i don't need latest version after all!!
thanks guys

---

