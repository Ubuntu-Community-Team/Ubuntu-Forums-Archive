---
title: "transcode package in hoary-extras broken"
date: 2005-07-26
forum: Bug Reports / Support
---

### Post by theantix on 2005-07-26
I have apt configured to use hoary-extras but not hoary-backports, as I would like to have access to some of the nice extra that ubuntu cannot ship but not replace my stable ubuntu packages.  This generally works quite well, but currently there is a problem with the transcode package.  The apt error message is as follows:

-----
The following packages have unmet dependencies:
  transcode: Depends: libgcc1 (>= 1:4.0.0-7) but 1:4.0-0pre6ubuntu7 is to be installed
E: Broken packages
-----

The correct (matching) libgcc1 package that is required does exist but only in the hoary-backports database.  This means that functionally, one must have both hoary-extras and hoary-backports enabled in order to install this program.  Is this an intentional decision to require both repositories to function or was it just an oversight for this one package?

This isn't a bug report, as I overcame the problem simply by downloading the libgcc1 package from hoary-backports and using dpkg -i to install it, I'm just curious about the intended policy and if something is broken.

---

