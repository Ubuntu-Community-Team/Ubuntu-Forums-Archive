---
title: "gnome baker error"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-06-03
```
Executing 'genisoimage -gui -V GnomeBaker data disk -A GnomeBaker -p zerobinary -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-zerobinary/gnomebaker-TSPBTT | builtin_dd of=/dev/hdb obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using 01__CELLO___DAINICHIGEN000.FLAC;1 for  Death/01. Cello - Dainichigen Chôgen.flac (01. Cello - Dainichigen ChÃ´gen.flac)
Incorrectly encoded string (für Violoncello Solo Nr.1 G-dur.flac) encountered.
Possibly creating an invalid Joliet extension. Aborting.
:-( write failed: Input/output error
```
what does that error means i can't burn the disc

---

### Post by 67GTA on 2007-06-03
I am not sure what that means. I used to get errors from Gnomebaker all the time and started using K3B. It is a KDE app, but will run fine in Gnome and is the best I've seen. Just my 2 cents.

---

### Post by Iokua on 2007-06-03
> **zerobinary said:**
> ```
Executing 'genisoimage -gui -V GnomeBaker data disk -A GnomeBaker -p zerobinary -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-zerobinary/gnomebaker-TSPBTT | builtin_dd of=/dev/hdb obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using 01__CELLO___DAINICHIGEN000.FLAC;1 for  Death/01. Cello - Dainichigen Chôgen.flac (01. Cello - Dainichigen ChÃ´gen.flac)
Incorrectly encoded string (für Violoncello Solo Nr.1 G-dur.flac) encountered.
Possibly creating an invalid Joliet extension. Aborting.
:-( write failed: Input/output error
```
what does that error means i can't burn the disc

I'm assuming this error occurs only with this disc? It appears to me that the character encoding in the filename is preventing the application from reading the file. You may have to burn the disc with a different character encoding, although I'm honestly not quite sure how to do that. You might want to try a workaround though: try ripping the disc to your hard-drive and then modifying the filenames to something simpler, although I can't guarantee that this will work.

My guess is that this is something internal with GnomeBaker. By the way, I think you should [file a bug report for this]("https://bugs.launchpad.net/ubuntu/+filebug").

---

