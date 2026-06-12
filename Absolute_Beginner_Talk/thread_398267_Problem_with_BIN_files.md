---
title: "Problem with BIN files"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-03-31
I have a file, called "Mangos" when I open a Shell, and change the dir to the dir of the file and run it, it says "./mangos-realmd: error while loading shared libraries: libZThread.so.0: cannot open shared object file: No such file or directory" What does this mean? And how do I solve it. Thanks

---

### Post by r4ik on 2007-03-31
Maybe this,

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

helps.


Good luck !

---

### Post by Peter1234123 on 2007-03-31
The file, as Ive seen from windows, launches in a command line, and it is not installed, it just launches, is it the same on Ubuntu?

---

### Post by r4ik on 2007-03-31
> **Peter1234123 said:**
> The file, as Ive seen from windows, launches in a command line, and it is not installed, it just launches, is it the same on Ubuntu?

Please read the link and stop thinking "windows" it will block you're mind :)

---

### Post by Skrynesaver on 2007-03-31
The problem is that you are missing a library file that the program requires to run.  This library, libZThread provides instructions for database routines.  Neither mangos nor LibZThread show up in the Ubuntu repositories.

This means you'll have to install it manually, did the mangos file come with any other files?

---

### Post by Peter1234123 on 2007-03-31
Yes, and it came with the LibZThread file also, yet it still won't run.

---

### Post by Maestro23 on 2007-03-31
> **Peter1234123 said:**
> Yes, and it came with the LibZThread file also, yet it still won't run.

Where is the the link that you downloaded the program from?

---

### Post by Skrynesaver on 2007-03-31
The LibZThread file needs to be in the library path, that means that you have to copy it to a library directory.  This is normally done by the install script however if you ```
sudo cp LibZThread.so.0 /usr/local/lib/
``` 
then run the program it should work, you should also consider putting the binary in /usr/local/bin, this would make it available as a command.

---

