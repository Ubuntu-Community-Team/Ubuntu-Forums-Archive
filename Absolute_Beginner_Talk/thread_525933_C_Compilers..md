---
title: "C Compilers."
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by zeehat on 2007-08-14
What are some well known, easy to use C Compilers for Linux?  In Windows I use Visual C++.  I would like a compiler for Linux.  Also how to install/run it step by step because of my newbie Linux skills.  Thanks.

---

### Post by some_random_noob on 2007-08-14
sudo apt-get install build-essential
sudo apt-get install gcc
sudo apt-get install g++

... try that, that should install compilers. As for an editing environment I'm not so sure. If you're skillful enough, just use a basic text editor and GCC - You can compile stuff via the command line. Or you could use an IDE such as anjuta

... Then again, I'm probably not the best person to ask.

---

### Post by zeehat on 2007-08-14
Ok, can I have a step by step guide of how to install gcc, and run it?  If I can get this to work, I will be in Ubuntu way more than Windows.  Programming is a reason why I still boot to Windows often.  I would like to less often:D

---

### Post by some_random_noob on 2007-08-14
> **zeehat said:**
> Ok, can I have a step by step guide of how to install gcc, and run it?  If I can get this to work, I will be in Ubuntu way more than Windows.  Programming is a reason why I still boot to Windows often.  I would like to less often:D
Like I said, I'm not the best person to ask. But since no-one else is replying I guess I'll try.

1. Run the commands I mentioned in my first post in order to install the compilers.
2. Get an IDE - if you get an IDE then you won't have to compile via the command line, and you'll be able to troubleshoot your programs more efficiently. I haven't really tried anything, but apparently Anjuta is good for C/C++. I would recommend looking at other IDE's though.

That's all you need to know for starters. You may run into problems deciding what software you want to use etc, but believe me on this: its not that hard. I'm 16 and I managed to get my C++ programs compiling via the command line :) ... if you need help with other programming related stuff, check the following links.

[https://help.ubuntu.com/community/Programming](https://help.ubuntu.com/community/Programming)
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)
"what's you're favourite IDE?" --> [http://ubuntuforums.org/showthread.php?t=6762](http://ubuntuforums.org/showthread.php?t=6762) (see other peoples opinions here)

---

### Post by zeehat on 2007-08-15
Ok, I am semi-getting this.  When I write a simple program in C in the text editor, I save it 'text.C'
Then I go to the terminal and type: gcc text.C
Then if it compiles with no problems, in the Terminal I just type the filename and it should load.  Is this right?

---

### Post by Rocket2DMn on 2007-08-15
you would type:
```
./a.out
```
When you compile, you can give the output file a different name, but a.out is the default
```
gcc filename -o my_program.out
./my_program.out
```
For more info: ```
man gcc
```
Happy coding!

---

### Post by russell.h on 2007-08-15
Yes. Try 'gcc --help' or 'man gcc' (in the command line) to see all of the many options you can use. -o is probably the first one you will want, as it will allow you to tell gcc what to name the output file (by default it is like a.out or somesuch - keep in mind in Linux the extension doesn't matter, its the MIME type, so you can call it whatever you want, just don't put .exe on the end or you will confuse people and possibly Wine).

---

### Post by Chaotic Thought on 2007-08-16
Here's a small tutorial to try (type the commands at a shell)

```

$ echo 'main(){}' > dummy.c
$ gcc -o dummy{,.c}
$ ./dummy

```

Note: **dummy{,.c}** expands to **dummy dummy.c** and means to output the executable as **dummy** and take in file **dummy.c** as the input.

---

