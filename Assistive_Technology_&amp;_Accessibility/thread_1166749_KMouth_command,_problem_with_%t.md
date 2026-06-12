---
title: "KMouth command, problem with %t"
date: 2009-05-22
forum: Assistive Technology &amp; Accessibility
---

### Post by mirosol on 2009-05-22
Hi.
I'm doing a work project with Ubuntu 9.04 and kmouth. Version from official ubuntu repos is compiled against qt4 and I'm using proprietary speech synthesis software called Mikropuhe. Speech synthesis daemon is running and everything is ok, when i give this command to terminal:
"echo this is the text i want to be spoken | iconv -f UTF-8 -t ISO-8859-1 - > /tmp/mikropuhe".
Now, i give same command to kmouth, only with %t variable..
"echo %t | iconv -f UTF-8 -t ISO-8859-1 - > /tmp/mikropuhe"
And nothing comes out.

Also, everytime i restart kmouth, the command has changed itself to "%25t".

This same command worked fine with qt3 version on ubuntu 8.04.

The %f variable seems to be working..

Are there some changes between qt3 and qt4 versions of kmouth, or am i missing some library or just my mind?

---

