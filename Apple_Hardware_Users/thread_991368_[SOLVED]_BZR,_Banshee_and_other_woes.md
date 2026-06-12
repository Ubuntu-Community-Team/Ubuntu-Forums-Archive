---
title: "[SOLVED] BZR, Banshee and other woes"
date: 2008-11-23
forum: Apple Hardware Users
---

### Post by ubuntubrian on 2008-11-23
After upgrading to Intrepid I have numerous problems. 
Any update gets me this error and apt-get -f install doesn't help:
```
dpkg: error processing bzr (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bzrtools:
 bzrtools depends on bzr (>= 1.6~); however:
  Package bzr is not configured yet.
 bzrtools depends on bzr (<< 1.7~); however:
  Package bzr is not configured yet.
dpkg: error processing bzrtools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bzr-builddeb:
 bzr-builddeb depends on bzr (>= 1.2~); however:
  Package bzr is not configured yet.
 bzr-builddeb depends on bzrtools (>= 1.2); however:
  Package bzrtools is not configured yet.
dpkg: error processing bzr-builddeb (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 bzr
 bzrtools
 bzr-builddeb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I tried:

```
:~$ dpkg -l bzr
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
iF  bzr            1.6.1-1        easy to use distributed version control syst

```

and:

```
:~$ bzr --version
bzr: WARNING: bzrlib version doesn't match the bzr program.
This may indicate an installation problem.
bzrlib from ['/usr/lib/python2.5/site-packages/bzrlib'] is version (1, 7, 0, 'candidate', 1)
Bazaar (bzr) 1.7rc1
  Python interpreter: /usr/bin/python 2.5.2
  Python standard library: /usr/lib/python2.5
  bzrlib: /usr/lib/python2.5/site-packages/bzrlib
  Bazaar configuration: /home/brianokeefe/.bazaar
  Bazaar log file: /home/brianokeefe/.bzr.log

```

I had some issues with printing after the upgrade and found this:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/271350](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/271350)

which has a short circuit for pdftopdf that allows for printing. It is this portion of the posts that interests me as it refers to bzr (I am a subscriber to this bugBTW):

> 
 Till Kamppeter wrote on 2008-11-21: (permalink)

Brian, thank you for doing the tests,

This shows exactly, that pdftopdf is corrupting the data. As soon as the data passes pdftopdf, the text cannot be displayed any more, and some PDF renderers (Ghostscript, Adobe Reader) even crash. Only Poppler succeeds to render these broken PDF files. Note that evince and the pdftops CUPS filter (which is used by cpdftocps) are Poppler-based.

 cbpxy wrote on 2008-11-21: (permalink)

I had exactly this problem (no real printing after intrepid upgrade on PPC) and this solution (replacing pdftopdf with the simple short-circuit filtere, above) worked great for me.

Thanks very much!

 Till Kamppeter wrote 1 hour ago: (permalink)

I have got a fix from upstream now and applied it to the Debian BZR repository of CUPS. A fixed package for Jaunty will come soon.
 

So this BZR issue seems larger than my small issue was in my mind.

---

### Post by ubuntubrian on 2008-11-23
I fixed the bzr problem by purging all bzr packages and reinstalling one at a time.

---

