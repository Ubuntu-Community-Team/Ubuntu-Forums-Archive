---
title: "Multimedia - Install pkg question"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by byebillgates on 2006-08-17
Newbie to Ubuntu, but not Unix. First on my list of "To Do's" is to configure my Totem Movie Player. (To eliminate my no decoders message) I downloaded the following files: (These files might not be what I need???) 

Ugly file format here...

gstreamer0.10-pitfdll_0.9.1.1+cvs20060515-1_i386.deb
gstreamer0.10-pitfdll_0.9.1.1+cvs20060515.orig.tar.gz

The deb installer stated I needed a lib.c package when I executed it,..and when I uncompressed the other file and ran the install-sh file, it asked me for a input file. I also tried a "sudo apt-get" followed by various guesses at the package name in the syntax but that obviously failed. Apologies, if this was already posted elsewhere...

---

### Post by it.henrik on 2006-08-17
to search for packages in a GUI way .. I would recommend you use synaptic.

System-Administration-synaptic

there you can search for gstreamer0.10

good luck

---

### Post by byebillgates on 2006-08-17
Thanks for the reply. I could not find the gstreamer files in earlier search attempts in Synaptic, but when I cut and pasted "gstreamer," using the search dialogue box, it found a bunch of gstreamer plugins. I loaded them all, but I'm still receiving a decoder error. I tried playing a DVD, but it didn't work. I believe Totem Movie player will also play wmv, mpg formats as well? Is that correct?

---

### Post by PriceChild on 2006-08-17
Check out [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) for info on installing all the multimedia codecs you should need.

---

### Post by byebillgates on 2006-08-18
The Restricted format URL is helpful, but some of the links just go in a circle and/or refer to a verbose multimedia product homepage. By any chance, does anybody have a quick and dirty syntax cheatsheet on how to install and configure Totem movie player using the apt-get install method? (With all the software package names and plugins) Thanks in advance!!

---

