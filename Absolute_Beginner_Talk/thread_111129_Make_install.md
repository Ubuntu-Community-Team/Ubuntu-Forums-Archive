---
title: "Make install"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by simon_is_learning on 2006-01-01
I have for a while now tried to download a source and compile it, tough I have never succeded i'm now asking for a bit of assistance.

i have dona an apt-get install build-essential

when i'm in the folder i do a ./configure and i see a lot of text...

then trying to do a "make" (becouse that's what the guides i have read has told me) all i get is an error 
I'm using a swedish ubuntu so the error message is:
Inga mål angavs och ingen makefil hittades.  Stannar.
something lie "No target chosen and no makefile found. Stopps" 
(don't know if it's the right translation)

make is installed btw.
What shall i do?

---

### Post by ubuntuuser on 2006-01-01
The problem seems to be with the configure part already. Look through the folder where you extracted the source, there usually are files named README and INSTALL. Check them to see if the program you want to compile needs certain libraries or other stuff. Open synaptic, then search for all the dependencies mentioned in the README and INSTALL files. You need to install the -dev versions.
Let's say you want to compile program ABC, which needs libxyz. Then you install libxyz-dev with synaptic. Then check the output of ./configure for further error messages.

---

