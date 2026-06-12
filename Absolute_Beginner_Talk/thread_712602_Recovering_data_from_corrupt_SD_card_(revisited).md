---
title: "Recovering data from corrupt SD card (revisited)"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by rua2 on 2008-03-01
(Please forgive my errors... since I'm currently in the grips of a cold, I am of even slower brain than usual.)

I have a similar problem to the concern in this post:
[http://ubuntuforums.org/showthread.php?t=306446](http://ubuntuforums.org/showthread.php?t=306446)

i.e, that I can't get pictures off my card. I can no longer even use the card in my camera.

ddrescue was recommended. Being unable to find it in the synaptic vaults, and apt-get unable to locate it either, I downloaded and opened the program, as instructed. 

I try to unpack the archive following the instructions in the install file, and get this line:
Can't open input file ddrescue[version].tar.bz2: No such file or directory.

I am quite stuck! Can anyone help me?

---

### Post by owbizi on 2008-03-01
Êh... are you sure you are on the correct folder?

You can try to install it via aptitude too:
$ sudo aptitude install ddrescue

That is also a ggdrescue, "GNU data recovery tool"... don't know exactly what is, but it's there:
$ sudo aptitude install gddrescue

---

### Post by rua2 on 2008-03-01
Thanks for the suggestion, owbizi.

aptitude got me nowhere too:
Couldn't find any package whose name or description matched "ddrescue" (or "gddrescue")

Could the server be down?

Oh and that unpacking line should read:
Can't open input file ddrescue-1.8.tar.bz2: No such file or directory.

:)

How do I know what the correct folder is? According to the install notes, running bunzip2 -c ddrescue-1.8.tar.bz2 | tar -xf - is supposed to "create the directory ./ddrescue[version] containing the source from the main archive".

I'm lost. I must keep doing something wrong, because despite my best efforts I've *never* managed to install a tarball successfully. (I used to toy with Mandriva before I tried Ubuntu.)

---

### Post by rua2 on 2008-03-02
Well! I stumbled onto a page about enabling extra repositories. Having enabled said repositories, suddenly ddrescue became available, and was downloaded and installed forthwith.

Now, how to use it! I've found a page... [http://www.cyberciti.biz/tips/how-do-i-save-recover-data-from-crashed-disks-with-dd-and-ddrescue-command.html](http://www.cyberciti.biz/tips/how-do-i-save-recover-data-from-crashed-disks-with-dd-and-ddrescue-command.html)

...on the subject which I'm sure is useful... except I don't know the exact name and location of the file I want to save, which is in a card reader that comes up on the desktop as JYAGARANDY. Now, I can't find any such device listed in /dev. I can see sda, sdb, sdc, sdc1, and sdd, but I can't get into them to see which is the volume I want.

Aaargh this is hard... In Mandriva I always knew the locations of mounted devices because they were on the desktop.

Can anyone help? Or better still, walk me through this maze?

---

### Post by rua2 on 2008-03-02
OK, it's sdc1.

Following instructions found elsewhere ([http://www.backports.ubuntuforums.org/showthread.php?t=617984](http://www.backports.ubuntuforums.org/showthread.php?t=617984)), I entered:  sudo dd_rescue /dev/sdc1 image log

I got a bunch of options in return:
dd_rescue: (fatal): spurious options: log ...

dd_rescue Version 1.10, [email]garloff@suse.de[/email], GNU GPL
 ($Id: dd_rescue.c,v 1.46 2004/08/28 21:45:09 garloff Exp $)
dd_rescue copies data from one file (or block device) to another
USAGE: dd_rescue [options] infile outfile
Options: -s ipos    start position in  input file (default=0),
         -S opos    start position in output file (def=ipos);
         -b softbs  block size for copy operation (def=65536),
         -B hardbs  fallback block size in case of errs (def=512);
         -e maxerr  exit after maxerr errors (def=0=infinite);
         -m maxxfer maximum amount of data to be transfered (def=0=inf);
         -l logfdile name of a file to log errors and summary to (def="");
         -r         reverse direction copy (def=forward);
         -t         truncate output file (def=no);
         -d/D       use O_DIRECT for input/output (def=no);
         -w         abort on Write errors (def=no);
         -a         spArse file writing (def=no),
         -A         Always write blocks, zeroed if err (def=no);
         -i         interactive: ask before overwriting data (def=no);
         -f         force: skip some sanity checks (def=no);
         -p         preserve: preserve ownership / perms (def=no)
         -q         quiet operation,
         -v         verbose operation;
         -V         display version and exit;
         -h         display this help and exit.
Note: Sizes may be given in units b(=512), k(=1024), M(=1024^2) or G(1024^3) bytes
This program is useful to rescue data in case of I/O errors, because
 it does not necessarily abort or truncate the output.

At least I know the program's there!

I have read the readme (the program file took some finding) - it is opaque to me.

:confused:

---

### Post by rua2 on 2008-03-05
So, an update to this bizarre near-monologue...

I couldn't figure out how to make ddrescue work. So I looked back to the world of Windows and was saved by an easy to use shareware program. (Though when I say "saved", I mean the problem was resolved: the card had been corrupted beyond all use and all pictures were gone for keeps. In fact the card fell apart when I pulled it from the reader!)

Now my question is: given there are so many image recovery programs available for Windows (admittedly few, if any, I've seen are free as in speech), why are there practically none for Linux? Memory card corruption is such a common enough problem that I'd have expected it to generate a bothersome enough itch for a developer or two to scratch with something a little more user-friendly than ddrescue.

---

