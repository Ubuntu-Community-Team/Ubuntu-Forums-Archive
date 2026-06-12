---
title: "how to install stardict from tarball"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by zooey on 2006-11-27
i unpacked stardict-2.4.8.tar.gz to /home/lumpy/stardict-2.4.8:

tar -xvjf stardict-2.4.8.tar.gz

then i moved to directory:

/home/lumpy/stardict-2.4.8

than i typed in the console:

./configure

this print me in terminal:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gconftool-2... /usr/bin/gconftool-2
checking for intltool >= 0.22... 0.34.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

and than i wrote:

make

in terminal printed me:

command not found

how can i install it from tarball?

in readme file it's just this:

 ./configure --prefix=/usr --sysconfdir=/etc --mandir=/usr/share/man
make
make install

i tried even this but it was with the same result

---

### Post by polly1 on 2006-11-28
Hi

Try this link for help

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by squidward_tentacels on 2006-11-28
satisfy the missing dependencies with;

"sudo apt-get install libxml-parser-perl"

---

### Post by david_kt on 2006-11-28
and than i wrote:

make

in terminal printed me:

command not found


DK:
First of all, please check whether or not you have install "make":

sudo apt-get install make


Regards,
DK

---

### Post by squidward_tentacels on 2006-11-28
You should 
"sudo apt-get install build-essential"

Before trying to compile from source, I believe make, and a few other goodies like compilers are included, that should do it.

---

