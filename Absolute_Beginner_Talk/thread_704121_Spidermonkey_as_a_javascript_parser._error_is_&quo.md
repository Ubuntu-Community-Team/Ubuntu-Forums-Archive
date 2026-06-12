---
title: "Spidermonkey as a javascript parser. error is &quot;parse error in file&quot;"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Mithu Mary Kuruvilla on 2008-02-22
Hello
 I want to use spidermonkey as a JavaScript parser.I could successfully compile the parser program.
  gcc -DXP_UNIX -I/usr/local/include/spidermonkey -o parser parser.c -L/usr/local/lib -ljs -lm

 While running i got the error:error while loading shared libraries: libjs.so: cannot open
 > shared object file: No such file or directory
 and corrected by setting the  LD_LIBRARY_PATH environment variable.

 Then I have given the JavaScript for parsing it gives "parse error in file".

 ./parser
 var x, y;
 x = 1;
 y = x * 2;

 "parse error in file".

 can anyone help me...
Regards
Mithu Kuruvilla

---

