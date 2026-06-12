---
title: "jigdo first DVD"
date: 2011-06-14
forum: Any Other OS
---

### Post by MichaelBurns on 2011-06-14
Apparently, the first Debian Squeeze DVD is larger than 4 GB, and apparently this is a problem for various downloaders.

I first tried wget, but it stopped at 4.0 GB.

Then, I tried curl, but apparently they moved the image somewhere to which I cannot connect.  Perhaps they are still in the process of setting up this new mirror, and I will try curl later.

So, I tried the upcoming jigdo program touted by Debian as the solution to all of my problems (sorry for the hyperbole).  It seemed straightforward enough: download the tarball, extract the single directory with contents, navigate to the directory where I want the image to download, invoke the script (by specifying the full path), and then enter the required information at the jigdo command prompts.  I got as far as downloading the template files.  Then, jigdo complained that the file (debian-6.0.1a-i386-DVD-1.iso.tmp) is too large.  I am assuming that this is the same 4 GB limit issue as with wget.  Any ideas?

---

