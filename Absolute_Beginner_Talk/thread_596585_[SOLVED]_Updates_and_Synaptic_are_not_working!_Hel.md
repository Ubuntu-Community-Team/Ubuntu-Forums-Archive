---
title: "[SOLVED] Updates and Synaptic are not working! Help"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2007-10-29
I was trying to install xnview, but to no avail. I then received an update that would give me error messages. I opened up synaptic package manager and was told to do "dpkg --conifigure -a"
Once I did that I opened the update manager again and got this notice:

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package xnview needs to be reinstalled, but I can't find an archive for it.'


How do I fix this so that things are back to normal?

---

### Post by Crafty Kisses on 2007-10-29
> **intense.ego said:**
> I was trying to install xnview, but to no avail. I then received an update that would give me error messages. I opened up synaptic package manager and was told to do "dpkg --conifigure -a"
Once I did that I opened the update manager again and got this notice:

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package xnview needs to be reinstalled, but I can't find an archive for it.'


How do I fix this so that things are back to normal?
You should try what it says:
```
sudo apt-get install xnview
```
Try that.

---

### Post by intense.ego on 2007-10-29
I tried the command you gave me, but after it installed I got this in the Terminal:

E: The package xnview needs to be reinstalled, but I can't find an archive for it.

What do i do?

---

### Post by Maestro23 on 2007-10-29
> **intense.ego said:**
> I tried the command you gave me, but after it installed I got this in the Terminal:

E: The package xnview needs to be reinstalled, but I can't find an archive for it.

What do i do?

I take it things blew up on ya.:)

Try:

> sudo dpkg -P xnview

or
sudo dpkg --remove --force-remove-reinstreq xnview

If one of those works, then

sudo apt-get update

sudo apt-get upgrade


---

### Post by llamakc on 2007-10-29
Where did you find the package "xnview"? It's not in the normal repositories.

Did you download a .deb from somewhere? If so, and you have it on your Desktop (or wherever) open the Terminal, navigate to where it is (or enter the full path) and type:

```

sudo dpkg -i xnview

```

And paste any errors.

---

### Post by Maestro23 on 2007-10-29
> **llamakc said:**
> Where did you find the package "xnview"? It's not in the normal repositories.

Did you download a .deb from somewhere? If so, and you have it on your Desktop (or wherever) open the Terminal, navigate to where it is (or enter the full path) and type:

```

sudo dpkg -i xnview

```

And paste any errors.

He tried installing from source. Didn't work.  He then tried the .rpm using the alien command, and I guess that blew up on him.  It's an old program not in the repos.

---

### Post by intense.ego on 2007-10-29
I tried the two commands maestro23 gave me and i got this back:

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.

---

### Post by Maestro23 on 2007-10-29
> **intense.ego said:**
> I tried the two commands maestro23 gave me and i got this back:

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.

I just checked your other thread, that person came back and posted a link to the .deb.

If you get it, don't try and do anything with it yet, until this is resolved.

---

### Post by intense.ego on 2007-10-29
Thank you. Its nearly 1am here (UK) so I'm off to bed, I will try fixing it tomorrow.

---

### Post by Maestro23 on 2007-10-29
> **intense.ego said:**
> Thank you. Its nearly 1am here (UK) so I'm off to bed, I will try fixing it tomorrow.

Ok man.  I subscribe to this thread and keep track of it.:guitar:

---

### Post by intense.ego on 2007-10-30
Anyone have any solution?

---

### Post by intense.ego on 2007-10-30
Please, someone. This is urgent. I can't update or use synaptic until this is fixed.

---

### Post by intense.ego on 2007-11-04
bump. anyone?

---

### Post by intense.ego on 2007-11-05
bump

---

### Post by Maestro23 on 2007-11-05
So did you try the .deb the other person posted a link to in your other thread?

---

### Post by intense.ego on 2007-11-05
it is locked for use only by the root. assuming it is on my desktop, how would i unpack it?

---

### Post by intense.ego on 2007-11-06
bump. anyone?

---

### Post by Maestro23 on 2007-11-06
> **intense.ego said:**
> bump. anyone?

To install a .deb:

> sudo dpkg -i packagname.deb

---

### Post by intense.ego on 2007-11-06
When I tried that i got:

> Selecting previously deselected package xnview.
(Reading database ... 
dpkg: serious warning: files list file for package `xnview' missing, assuming package has no files currently installed.
170055 files and directories currently installed.)
Preparing to replace xnview 1.70-2 (using xnview.deb) ...
Unpacking replacement xnview ...
dpkg-deb: unexpected end of file in between members in xnview.deb
*** glibc detected *** dpkg: double free or corruption (fasttop): 0x09a2f640 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e417cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e44e30]
dpkg[0x806402e]
dpkg[0x8058fd0]
dpkg[0x804b348]
dpkg[0x8055aae]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7defebc]
dpkg[0x804ab51]
======= Memory map: ========
08048000-0809b000 r-xp 00000000 08:02 639201     /usr/bin/dpkg
0809b000-0809c000 rw-p 00052000 08:02 639201     /usr/bin/dpkg
0809c000-09a4e000 rw-p 0809c000 00:00 0          [heap]
b7700000-b7721000 rw-p b7700000 00:00 0 
b7721000-b7800000 ---p b7721000 00:00 0 
b78a4000-b7b0d000 rw-p b78a4000 00:00 0 
b7b0d000-b7b2d000 r--p 00000000 08:02 1032454    /usr/share/locale-langpack/en_GB/LC_MESSAGES/dpkg.mo
b7b3c000-b7b47000 r-xp 00000000 08:02 327744     /lib/libgcc_s.so.1
b7b47000-b7b48000 rw-p 0000a000 08:02 327744     /lib/libgcc_s.so.1
b7b48000-b7c7a000 rw-p b7b48000 00:00 0 
b7c7a000-b7c83000 r-xp 00000000 08:02 361747     /lib/tls/i686/cmov/libnss_files-2.5.so
b7c83000-b7c85000 rw-p 00008000 08:02 361747     /lib/tls/i686/cmov/libnss_files-2.5.so
b7c85000-b7c8d000 r-xp 00000000 08:02 361751     /lib/tls/i686/cmov/libnss_nis-2.5.so
b7c8d000-b7c8f000 rw-p 00007000 08:02 361751     /lib/tls/i686/cmov/libnss_nis-2.5.so
b7c8f000-b7ca2000 r-xp 00000000 08:02 361741     /lib/tls/i686/cmov/libnsl-2.5.so
b7ca2000-b7ca4000 rw-p 00012000 08:02 361741     /lib/tls/i686/cmov/libnsl-2.5.so
b7ca4000-b7ca6000 rw-p b7ca4000 00:00 0 
b7ca6000-b7cad000 r-xp 00000000 08:02 361743     /lib/tls/i686/cmov/libnss_compat-2.5.so
b7cad000-b7caf000 rw-p 00006000 08:02 361743     /lib/tls/i686/cmov/libnss_compat-2.5.so
b7cc4000-b7cc6000 rw-p b7cc4000 00:00 0 
b7cc6000-b7d01000 r--p 00000000 08:02 689438     /usr/lib/locale/en_GB.utf8/LC_CTYPE
b7d01000-b7dd8000 r--p 00000000 08:02 689437     /usr/lib/locale/en_GB.utf8/LC_COLLATE
b7dd8000-b7dda000 rw-p b7dd8000 00:00 0 
b7dda000-b7f15000 r-xp 00000000 08:02 361730     /lib/tls/i686/cmov/libc-2.5.so
b7f15000-b7f16000 r--p 0013b000 08:02 361730     /lib/tls/i686/cmov/libc-2.5.so
b7f16000-b7f18000 rw-p 0013c000 08:02 361730     /lib/tls/i686/cmov/libc-2.5.so
b7f18000-b7f1b000 rw-p b7f18000 00:00 0 
b7f1b000-b7f2e000 r-xp 00000000 08:02 361756     /lib/tls/i686/cmov/libpthread-2.5.so
b7f2e000-b7f30000 rw-p 00013000 08:02 361756     /lib/tls/i686/cmov/libpthread-2.5.so
b7f30000-b7f32000 rw-p b7f30000 00:00 0 
b7f36000-b7f37000 r--p 00000000 08:02 689443     /usr/lib/locale/en_GB.utf8/LC_NUMERIC
b7f37000-b7f38000 r--p 00000000 08:02 689446     /usr/lib/locale/en_GB.utf8/LC_TIME
b7f38000-b7f39000 r--p 00000000 08:02 689441     /usr/lib/locale/en_GB.utf8/LC_MONETARY
b7f39000-b7f3a000 r--p 00000000 08:02 704553     /usr/lib/locale/en_GB.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f3a000-b7f3b000 r--p 00000000 08:02 689444     /usr/lib/locale/en_GB.utf8/LC_PAPER
b7f3b000-b7f3c000 r--p 00000000 08:02 689442     /usr/lib/locale/en_GB.utf8/LC_NAME
b7f3c000-b7f3d000 r--p 00000000 08:02 689436     /usr/lib/locale/en_GB.utf8/LC_ADDRESS
b7f3d000-b7f3e000 r--p 00000000 08:02 689445     /usr/lib/locale/en_GB.utf8/LC_TELEPHONE
b7f3e000-b7f3f000 r--p 00000000 08:02 689440     /usr/lib/locale/en_GB.utf8/LC_MEASUREMENT
b7f3f000-b7f46000 r--s 00000000 08:02 1016043    /usr/lib/gconv/gconv-modules.cache
b7f46000-b7f47000 r--p 00000000 08:02 689439     /usr/lib/locale/en_GB.utf8/LC_IDENTIFICATION
b7f47000-b7f49000 rw-p b7f47000 00:00 0 
b7f49000-b7f62000 r-xp 00000000 08:02 327701     /lib/ld-2.5.so
b7f62000-b7f64000 rw-p 00019000 08:02 327701     /lib/ld-2.5.so
bfeda000-bfeef000 rw-p bfeda000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)


---

### Post by intense.ego on 2007-11-07
bump

---

### Post by intense.ego on 2007-11-07
bump

---

### Post by intense.ego on 2007-11-07
bump

---

### Post by por100pre1 on 2007-11-07
What about force removing it:

```
sudo dpkg --remove --force-remove-reinstreq xnview
```

---

### Post by intense.ego on 2007-11-08
It says:

>  Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `xnview' missing, assuming package has no files currently installed.
170056 files and directories currently installed.)


---

### Post by intense.ego on 2007-11-08
it works again! thank you so much por100pre1. I thought i tried your solution before but perhaps not. thank you everyone once again.

---

