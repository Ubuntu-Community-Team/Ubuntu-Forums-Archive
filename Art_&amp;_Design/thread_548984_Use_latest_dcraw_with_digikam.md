---
title: "Use latest dcraw with digikam"
date: 2007-09-12
forum: Art &amp; Design
---

### Post by rcoconnell on 2007-09-12
I'm trying to use the CHDK firmware with a canon A620 powershot to take RAW pictures.  The good news is that dcraw 8.77 supports the A620 RAW files.  The bad news is that this version doesn't come with Ubuntu.

I managed to compile it, following the instructions at [http://cybercom.net/~dcoffin/dcraw/](http://cybercom.net/~dcoffin/dcraw/) (with the  -DNO_JPEG -DNO_LCMS options), and copied the resulting binary to /usr/bin/dcraw.  If I run dcraw from the command line, 8.77 is the version that runs.  I ran find / -name dcraw, and the only hit was /usr/bin/dcraw.  Sounds good, right?

The last thing I want to do is use develop the RAW files within digikam.  I thought that installing the latest dcraw would let digikam use it.  Nope!  If I go to the "RAW Conversion" part of the digikam settings, there's a link in the upper right to "dcraw 8.41" -- is dcraw built in?  Is there any decent GUI which uses the latest dcraw?

-ross

---

### Post by Oki on 2007-09-12
Almost all programs for Linux that converts RAW files use dcraw. I would not use dcraw but programs with the same engine. You could try UFRaw. Its a stand alone program for converting, or you could use the plugin for Gimp. Rawstudio is another option, see here; [http://www.getdeb.net/app.php?name=Rawstudio](http://www.getdeb.net/app.php?name=Rawstudio)

There are also others, like RawTherapee, Lightzone, Google Picasa, Bibble and so on.

---

### Post by rcoconnell on 2007-09-13
Thanks for your reply!

RawStudio works, and I'll take a look at the gimp plugin.  What I really want, of course, is to just use digikam, not make a major change in my workflow.  From poking around the digikam forums, it sounds like most dcraw updates break compatibility with a given version of digikam, so I'll have to wait for Gutsy.

Actually, what's involved in installing Gutsy's digikam package?

-ross

---

### Post by kayosiii on 2007-09-13
digikam uses libkdcraw rather than dcraw directly  (this is a recent change) you can get this from kde subversion I think extra libs but check the digikam website to be sure.

I have successfully compiled this lib and dropped it over the existing one without any problem.

---

