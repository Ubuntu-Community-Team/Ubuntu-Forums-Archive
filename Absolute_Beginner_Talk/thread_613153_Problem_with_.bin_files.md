---
title: "Problem with .bin files"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Esben Kramer on 2007-11-14
I have a problem with a demo of a game I found. I can't install the .bin-file. I get this message:

 Syntax error: "(" unexpected

You might think that it's the .bin that's out of order, but my laptop has done this with a bunch of different files, including some that my desktop can run without problems. It's always that same message. Any ideas?

---

### Post by Hospadar on 2007-11-14
what command are you using to run them?

---

### Post by Esben Kramer on 2007-11-14
(sudo if necessary) sh nameoffile.bin

---

### Post by PeterJS on 2007-11-14
Sh is generally used for executing shell scripts, which generally have an extension of .sh. Usually files that have a .bin extension are actual program executables. Try just typing in ./name_of_file.bin, if that doesn't work run chmod +x ./name_of_file.bin to give the file execute permissions and try running it again.

---

### Post by Esben Kramer on 2007-11-14
Great stuff. Thanks. 'Problem' solved.

---

### Post by Inxsible on 2007-11-14
Please mark your thread solved by going to Thread Tools>>Mark thread as solved :)

---

