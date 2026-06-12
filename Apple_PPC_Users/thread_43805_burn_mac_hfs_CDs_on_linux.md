---
title: "burn mac hfs CDs on linux"
date: 2005-06-23
forum: Apple PPC Users
---

### Post by HRonzani on 2005-06-23
Hi,

I want to make a copy of an HFS Mac CD. My mac  doesnt have a CDR.
I have a box with linux and CDR.

I could mount the hfs CD on linux, and then, I use mkhybrid to generate the mac iso and burn it.

The problem is that Mac 9.2.2 does not recognize file types burned on CD from linux. It doesnt know wich application use to open some program.

The syntax I use is:

mkhybrid -o /tmp/testhfs.iso -r -J -hfs -V MacPrograms -map /tmp/maphfs  .

maphfs is one I found on man mkhybrid plus other extn I found on net.

# Example filename mapping file
#
# EXTN   XLate   CREATOR   TYPE     Comment
.tif     Raw     '8BIM'    'TIFF'   "Photoshop TIFF image"
.hqx     Ascii   'BnHq'    'TEXT'   "BinHex file"
.doc     Raw     'MSWD'    'WDBN'   "Word file"
.mov     Raw     'TVOD'    'MooV'   "QuickTime Movie"
*        Ascii   'ttxt'    'TEXT'   "Text file"


Any help is welcomed.
Thanks in advance

---

