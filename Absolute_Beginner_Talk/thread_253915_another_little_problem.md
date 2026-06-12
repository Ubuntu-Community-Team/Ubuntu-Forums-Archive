---
title: "another little problem"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-09-09
Hi all! :) 

I am trying to install Cinelerra and the ./configure seemed to go OK but when I typed in **make**, I got this

[B]Configured successfully.  Type 'make' to build it.
russty@russty-desktop:~/Software/cinelerra-2.1$ make
make -f build/Makefile.cinelerra
sh: -c: line 1: syntax error: unexpected end of file
make[1]: Entering directory `/home/russty/Software/cinelerra-2.1'
gcc -c -O2 -fomit-frame-pointer -falign-loops=2 -falign-jumps=2 -falign-functions=2 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -I../../freetype-2.1.4/include -I../../ -DHAVE_OSS -DHAVE_FIREWIRE  soundtest.c -o i686/soundtest.o
Assembler messages:
FATAL: can't create i686/soundtest.o: No such file or directory
make[1]: *** [i686/soundtest.o] Error 1
make[1]: Leaving directory `/home/russty/Software/cinelerra-2.1'
make: *** [all] Error 2
russty@russty-desktop:~/Software/cinelerra-2.1$[/B]


What does it mean and is there anything I can do about it?

Russty.

---

### Post by Russty of Oz on 2006-09-09
Is anyone there?

---

### Post by Perfect Storm on 2006-09-09
[http://doc.gwos.org/index.php/Cinerella](http://doc.gwos.org/index.php/Cinerella)

---

### Post by Russty of Oz on 2006-09-09
OK, I will give that a try.

Thanks very much.

Russty:)

---

### Post by Russty of Oz on 2006-09-09
cant download the .rpm file at the moment, the site is not responding, so I will have to try later or tomorrow.  Will post again with what (if anything) happens.

Russty.

---

### Post by Russty of Oz on 2006-09-09
The site where the .rpm package is still does not respond, so I did a google for the cinelerra.rpm and found this there which sounds like it does a .deb install of cinelerra. [http://www.kiberpipa.org/~gandalf/ubuntu/README]("http://www.kiberpipa.org/~gandalf/ubuntu/README")

Now what does this all mean?  I think I have to edit the sources list or something, but how?  And does "uncomment" mean delete?

Any help here?

Russty.

---

### Post by Russty of Oz on 2006-09-09
The site where the .rpm package is still does not respond, so I did a google for the cinelerra.rpm and found this there which sounds like it does a .deb install of cinelerra. [http://www.kiberpipa.org/~gandalf/ubuntu/README]("http://www.kiberpipa.org/~gandalf/ubuntu/README")

Now what does this all mean?  I think I have to edit the sources list or something, but how?  And does "uncomment" mean delete?

Any help here?

Russty.

---

### Post by Russty of Oz on 2006-09-09
Just thought I would bring this back up the list.

---

### Post by missmoondog on 2006-09-09
uncomment means to just remove the "#'s" in front of the repo listing.

---

### Post by Russty of Oz on 2006-09-09
**I DID IT!!!!**:grin: 

I found how to get into the sources list to edit it, and after a few errors, (fortunatly I wrote down what I did so I could put things back the way they were) I got it to work.  And it was really easy too!!!  **HORRAY!! ** 

So you can easily install Cinelerra in Ubuntu very easily without having to use the .rpm things.

Now to see how it works.

Russty. :D

---

