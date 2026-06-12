---
title: "Running my Code"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by tshendruk on 2006-09-15
I'm new to both programming and Linux, so there is probably an obvious fix here:

I'm trying to learn C for the first time and I want to do all my practice on Linux so I've installed gcc along with the build essential.

I have code that I made on another machine that ran on that machine (it's just hello_world) and so I used gcc to compile it, just like I did on the other machine.
All went well. A prgram was created (hello_world) from the code (hello_world.c) and its highlighted appropriately and it looks like it should run...
But when I type hello_world into the terminal nothing happens. 

What have I missed? I didn't use make or make install before...

Thank you for any help.

---

### Post by Anonii on 2006-09-15
> **tshendruk said:**
> I'm new to both programming and Linux, so there is probably an obvious fix here:

I'm trying to learn C for the first time and I want to do all my practice on Linux so I've installed gcc along with the build essential.

I have code that I made on another machine that ran on that machine (it's just hello_world) and so I used gcc to compile it, just like I did on the other machine.
All went well. A prgram was created (hello_world) from the code (hello_world.c) and its highlighted appropriately and it looks like it should run...
But when I type hello_world into the terminal nothing happens. 

What have I missed? I didn't use make or make install before...

Thank you for any help.
./hello_world

<:

(Not a single idea of C, but I think I am right.)

---

### Post by tshendruk on 2006-09-15
Thank you very much! I really appreciate the help!

---

### Post by Timothy Butwinick on 2006-09-15
If you just type "hello_world", the terminal assumes that your program is installed on your system, which it isn't. The "./" tells it to look in the current directory (that is ".").

To make a program start *without* the /. you have to move it to the /usr/local/bin directory. I don't think that you will use your Hello World program enough to make that necessary though :)

---

### Post by Brunellus on 2006-09-15
you have to make it executable first.

chmod +x hello_world.c

then you can execute it

./hello_world.c

---

### Post by tshendruk on 2006-09-15
Thanks for all the help everybody. I especially appreciate the bits of reasoning behind why I did it and how to make it work other ways.
Thanks

---

### Post by cstudent on 2006-09-15
> **Brunellus said:**
> you have to make it executable first.

chmod +x hello_world.c

then you can execute it

./hello_world.c

Actually this would not be correct. This is a C program. It would be compiled via the command line like so:
```

gcc hello_world.c -o hello_world

```

This would create an executable binary file called hello_world which could then be ran with the command:
```

./hello_world

```


BTW, there is a whole sub-section of the forums for programming questions like this.
[http://www.ubuntuforums.org/forumdisplay.php?f=39](http://www.ubuntuforums.org/forumdisplay.php?f=39)

---

