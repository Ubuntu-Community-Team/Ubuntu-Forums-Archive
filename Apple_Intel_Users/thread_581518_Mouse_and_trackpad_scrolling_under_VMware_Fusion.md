---
title: "Mouse and trackpad scrolling under VMware Fusion"
date: 2007-10-19
forum: Apple Intel Users
---

### Post by mcvaughan on 2007-10-19
I'm wanting to get mouse and trackpad scrolling working on Gutsy under VMware Fusion.  I tried by simply adding the VertTwoFingerScroll and HorizTwoFingerScroll, but the problem may just be that I'm running it all under a VM.  

Anyone?

---

### Post by eodchop on 2007-10-19
Try VMware Fusions support forum. I know there is a command that you have to run in a terminal in OS X.

---

### Post by Encore1974 on 2008-02-24
I found this in another forum 
[http://benkreeger.com/blog/?p=12](http://benkreeger.com/blog/?p=12)

simply change in the file /etc/X11/xorg.conf the line
Option    "Protocol"    "ps/2"
Option    "Protocol"    "imps/2"

I did it and it works!

Oscar

---

