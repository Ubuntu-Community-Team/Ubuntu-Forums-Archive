---
title: "gtk-config not found; path problems"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by jason_65c02 on 2005-11-15
Hi all!  first install of linux here... love it!!!! (using KUBUNTU 5.10)

I'm trying to install a program from source, have run up against a few stops and found answers to my issues so far, except... (ie, installed build-essentials and linux-headers-2.6-386)

when i do:
 ./configure
 make 

I get "gtk-config" not found.

The makefile for the program i'm trying to install has vars at the beginning of:
BinDir=/usr/local/bin
'myprog'Dir=/usr/local/share/'myprog'  ('myprog' is really the name of the prog i'm installing...')

I have an idea of what to change the dirs to in the makefile, but I still get 'gtk-config not found' errors.


1) How do I get gtk-config to be found, 
2) what do I change the 'dir' vars to so everyone on my box can run the prog?

The only requirements of the prog are GTK+1.2 or better, and X, so I know it can be compiled on my lovely KUBUNTU!!!

Thanks in advance!!!!!

---

### Post by teaker1s on 2005-11-15
make sure you have build-essential installed any use synaptic for missing dependencies found in ./configure then run ./configure again

---

### Post by jason_65c02 on 2005-11-16
I already installed "build-essentials" (in my orig post) along with just about every other header and development library i could find.

./configure gives "bash: ./configure - no such file or directory"

I used ADEPT for installing build-essentials - was this the problem?  I can't find "synaptic" for installing...

Thanks,
Jason

---

### Post by jason_65c02 on 2005-11-16
update: I don't have a CONFIGURE file for the source prog - it's simple.... INSTALL doc states:
$MAKE
$SU MAKE INSTALL

and the MAKE file under "INSTALL" states:
$gcc 'gtk-config --cflags' xxx.c -o xxxexe 'gtk-config --libs'

I have compiled this successfully almost 6 years ago on mandrake....

---

