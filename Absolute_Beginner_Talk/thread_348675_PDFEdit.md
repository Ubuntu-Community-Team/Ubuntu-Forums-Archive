---
title: "PDFEdit"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by padeco on 2007-01-29
hi there,
i would appreciate some help, if any one has or is currently using pdfedit. i installed the program as recommended (./configure > make > make install). needless to say, prior to all this i had to install a number of dependencies (doxygen, docbook, ...).

now, whe i run pdfedit the following error appears:

 pdfedit
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2:GUI:settings.cc:initSettings:121: No settings found - pdfeditrc

Fatal Error!
Missing item in config:
gui/items/MainMenu
QTextCodec::~QTextCodec() called by application


any ideas, thanks!
padeco

---

### Post by NoNo_231 on 2007-01-29
I have this "deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0" on my sources and pdfedit is there and works fine. 

You can find more info on the repo here [http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/](http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/)

---

### Post by padeco on 2007-01-29
hi there,
thank you for that link, however, i am not sure how it should work. i downloaded your deb pdfedit pack, but it gives me a libc6 error. i have libc6 installed. also i am running dapper. may be that is the issue.

if you have any further advice, please pass it on.
thanks,
padeco

---

### Post by NoNo_231 on 2007-01-29
Sorry my bad! I just now show that u are using Dapper. So the link doesn't help. Also as Isaw there is no package for dapper.

In the procedure ./configure > make > make install did you get any error messages? Or was it clean?

---

### Post by padeco on 2007-01-29
there was no error message, so i assume it was clean.

---

### Post by doundounba on 2007-01-30
FWIW, padeco, I get exactly the same error after compiling (cleanly) from source on Kubuntu Edgy.  I posted a few more details here:
[http://www.ubuntuforums.org/showthread.php?t=345257]("http://www.ubuntuforums.org/showthread.php?t=345257t")

I'd prefer to find the fix rather than installing a deb from an unknown (to me, at least) repository,..

---

