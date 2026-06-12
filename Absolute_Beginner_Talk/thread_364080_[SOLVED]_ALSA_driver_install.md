---
title: "[SOLVED] ALSA driver install"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by jrlii on 2007-02-17
I am trying to install the ALSA drivers for my old 20-bit Layla audio adapter. This is an audio adapter with 8 analog channels in,  10 analog channels out and a pair of SP-DIF ports for two digital channels each direction.

I'm trying to follow the instructions at:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Layla.&chip=Motorola+56301%2C+FPGA&module=layla20](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Layla.&chip=Motorola+56301%2C+FPGA&module=layla20)

When it get down to where I put in sudo ./configure --with-cards=layla20 --with-sequencer=yes;make;make install

The ./configure script seems to run OK 'till it gets down to:

checking for kernel linux/version.h... no

At which point this message appears:

The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

The subsequent make fails big time.

This suggests I need to load the Kernel source code, but I'm running "Dapper Drake" 6.06 which is kernel 2.6.something and all the kernel stuff Synaptic shows is 2.4.something.

SO. . . where do I go from here?

---

### Post by jrlii on 2007-02-17
Well, I think I found the answer to this one: 

sudo aptitude install linux-source

At least it looks like it is working. It'll take another hour or two to complete the download on dialup. 

Anyone else have one of these contraptions?

- John.

---

### Post by jrlii on 2007-04-29
That was in fact what was missing.

---

