---
title: "Perlmagick trouble on Dapper"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by mr fuzzy on 2007-06-13
Hello everyone.  
I'm very new to Ubuntu and am trying to get perlmagick working.  I used it ages ago on redhat.

I installed imagemagick and perlmagick with apt-get and it seemed to work fine.  Now, when I try to run a perl script using Image::Magick I get the error:

Can't load '/usr/lib/perl5/auto/Image/Magick/Magick.so' for module Image::Magick: libMagick.so.9: cannot open shared object file: No such file or directory at /usr/lib/perl/5.8/DynaLoader.pm line 225.
 at ./imageMagickTest.pl line 2
Compilation failed in require at ./imageMagickTest.pl line 2.
BEGIN failed--compilation aborted at ./imageMagickTest.pl line 2.

A quick net search found a post about the same problem on an imagemagick user group that said it was a problem with Debian.

please let me know if there is more approprate forum for this question.
Any help will be appreciated

---

### Post by Skrynesaver on 2007-06-13
If you do a locate for libMagick.so what does it find?

---

### Post by mr fuzzy on 2007-06-22
Thanks for replying, sorry I took so long to get back.

When I try to locate libMagick.so locate returns without finding anything.

When I do a locate for Magick I get lots of hits but only one .so file at:
/usr/lib/perl5/auto/Image/Magick/Magick.so

---

### Post by mr fuzzy on 2007-06-23
I've been fiddling with things this weekend and I've managed to fix it. I used the Synaptic Package Manager to reinstall three packages (it said they were already installed):

libmagick9
imagemagick
perlmagick

In that order and it works now.

They were not visible from the add/remove programs panel so I had to use the advanced options.


Thanks for looking at the problem.

---

