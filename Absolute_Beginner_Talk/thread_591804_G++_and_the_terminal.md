---
title: "G++ and the terminal"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by GearedForWar on 2007-10-25
OK, so far Linux is all I could of dreamed for.  better than Windows and its free what greater?  OK back to the point I just installed Linux with a dual boot of windows and got G++ installed.  Can anyone help me with compiling programs?  Its really confusing me.

---

### Post by llamakc on 2007-10-25
> **GearedForWar said:**
> OK, so far Linux is all I could of dreamed for.  better than Windows and its free what greater?  OK back to the point I just installed Linux with a dual boot of windows and got G++ installed.  Can anyone help me with compiling programs?  Its really confusing me.

What is confusing you? You should be specific, and don't forget to read this:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by Hospadar on 2007-10-25
also, did you just install g++ or did you install the "build-essential" package?  If not, you should grab build-essential it has other important tools like gcc and make.

As a quick reference, if you are just trying to compile a single .cpp file you are going to use "g++ -o"NameOfExecutable" your_file.cpp"

But if you download source packages for other software, it will probably use the standard configure/make/make install ```
./configure
make
sudo make install
```

---

### Post by GearedForWar on 2007-10-26
Sorry for not posting earlier I got it to work.  I'm good now sorry.

---

