---
title: "core.5385"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by Ex-windows on 2007-07-12
[COLOR="Blue"][/COLOR] hi all,
I tried to be a good lil newby and search for an answer, but there doesn
t seem to be one.
 My wifes comp has ubuntu Fiesty, and I noticed a file in the home folder called "core.5385". Here are the "Properties"
program crash data 120.1 MB
home folder
MIME type application/x-core
I was finally able to openit with Office word but the file was encrypted.
Does anyone know what this is?????
Any help would be greatly appreciated

---

### Post by meatpan on 2007-07-12
This file is called a 'core dump'.  There is quite a bit of info describing a core dump here: [http://en.wikipedia.org/wiki/Core_dump](http://en.wikipedia.org/wiki/Core_dump)

Basically, a program tried to access memory that it did not own.  When this happens the kernel will take a snapshot of the program memory image and write it to file.  You can load a core-dump into a debugging program as a useful means to view the state of the program immediately before it was killed by the kernel.  I don't think it is reasonable to try to open the core file with a text editor.

BTW, the number after 'core.' is the process-id (PID) of the program that failed.

Does that help?

---

### Post by Ex-windows on 2007-07-12
> **meatpan said:**
> This file is called a 'core dump'.  There is quite a bit of info describing a core dump here: [http://en.wikipedia.org/wiki/Core_dump](http://en.wikipedia.org/wiki/Core_dump)

Basically, a program tried to access memory that it did not own.  When this happens the kernel will take a snapshot of the program memory image and write it to file.  You can load a core-dump into a debugging program as a useful means to view the state of the program immediately before it was killed by the kernel.  I don't think it is reasonable to try to open the core file with a text editor.

BTW, the number after 'core.' is the process-id (PID) of the program that failed.

Does that help?
YES:) Thank you very much. I was concerned as we just went to ubuntu to get away from spyware, malware etc and my wife is like a magnet to that stuff lol. I will check out the url you gave and as for the text editor, all I can say to that is "hey I am a newby lol lol lol
Thank you again

---

