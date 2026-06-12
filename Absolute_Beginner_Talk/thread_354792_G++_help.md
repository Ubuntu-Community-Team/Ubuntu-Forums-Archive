---
title: "G++ help"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by pietimer on 2007-02-06
Hello,
I install g++ on my system a little while ago (from synaptics). I wrote a quick c++ program, compiled it (g++ -o foo.o -c foo.cpp), and tried to run it.
I typed in ./foo.o into the terminal and got back:
bash: ./foo.o: Permission denied
so, I typed in sudo ./foo.o and got back:
sudo: ./foo.o: command not found

What am I doing wrong?

Thanks for your help!

---

### Post by ramzai on 2007-02-06
chmod u+x foo.o
./foo.o

You may also want to read
[http://en.wikipedia.org/wiki/Permissions#Basic_Permissions](http://en.wikipedia.org/wiki/Permissions#Basic_Permissions)

---

### Post by xfceslacker on 2007-02-06
Hi,
I'm not sure what you're doing, but for a simple program with one source file. You would use g++ foo.cpp -o foo. The -c option can be used if you're compiling more than one source file. If you don't give g++ the -o foo it will put the program in a file called a.out. Also you don't need to chmod the files that come out of g++ to run them.

Hope that helped.

---

### Post by pietimer on 2007-02-06
xfceslacker, thanks for correcting my syntax. I tried your suggestion and it works great.
Thanks again!

---

### Post by ramzai on 2007-02-06
**xfceslacker** is right, sorry. The -c option says not to run the linker, so the output consists of object files output by the assembler (man g++). You can't run those, however, your permission error was a chmod issue.

---

