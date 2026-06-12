---
title: "can't actually run programs made with scons"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by Xavier Oddmon on 2007-10-31
Okay, I've got a question about how to get programs that were manually extracted/compiled/whatever scons does. I downloaded xfer9860 (a program to connect to the Casio fx9860-g graphing calculator) from sourceforge. I had to use scons to extract it (i think that's what it did, not really sure.). I can either extract a normal or binary file. I tried the two. I am presented with a file called either xfer9860 or xfer9860-bin. Ubuntu recognizes this as an executable file. How do I run it? Double click does nothing, run in terminal tells me that it wasn't found (yes, i did CD to that folder, if that matters). I tried using chmod, which made the non-bin file give me an error, saying that no program was specified to open this kind of file. How do I run this sort of thing? (This isn't the first time this has happened, yet I'm failing to recall what the other programs were.) Please help, it would be greatly appreciated.

---

### Post by Jaco Du Toit on 2007-11-01
When changing into the directory to run the file, have you tried running it like this:

./xfer9860-bin

If the dot slash is not present, then quite often you get the command not found message. If this is what you tried, then it *might* be that xfer09860-bin is calling some other file that doesn't exist.

---

### Post by Xavier Oddmon on 2007-11-01
Yes, I tried this, with no success. Thanks though.

---

