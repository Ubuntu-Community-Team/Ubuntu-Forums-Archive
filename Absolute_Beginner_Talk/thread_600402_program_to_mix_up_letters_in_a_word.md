---
title: "program to mix up letters in a word???"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-11-02
any one know of a program that i can type in a word say "visual" and it will mix up all the letters and give me every possible combination of the letters mixed up, say in a text file so i can read it?

 hope this makes sense.

---

### Post by justleen on 2007-11-02
that would be perl ...

---

### Post by mali2297 on 2007-11-02
If you want to learn programming, it would be a nice beginner's exercise. But if you want an already written program for the task, you can try this:
[http://hood.sjfn.nb.ca/~eddie/wscr.html](http://hood.sjfn.nb.ca/~eddie/wscr.html)

Compile the program with *make* (see [howto]("https://help.ubuntu.com/community/CompilingEasyHowTo")), then run
```

./wscr visual > output.txt

```
The program will write all permutations of the string "visual" into the file output.txt.

If you want to install the program, use *checkinstall*.

---

### Post by stinger30au on 2007-11-02
awesome, thats what im looking for, thanks!

---

