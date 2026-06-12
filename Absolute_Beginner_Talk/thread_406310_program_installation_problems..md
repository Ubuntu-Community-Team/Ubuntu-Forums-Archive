---
title: "program installation problems."
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by sewercake on 2007-04-10
HI!

For about a month now, I have been trying to install Ubuntu, and had many set backs. First, I didn't have enough room on my HDD, so I had to buy a new one, then when I finally did, it was screwed up, then, I lost my live CD, then I got a new hard drive, installed it, still couldn't find my live CD and had to make a new one. But finally, I got past it all and installed it (only about 20 mins ago) and I am liking it so far, but still a little confused. Now, the first program I downloaded was Wine. I went to synaptic, found the package, installed it ok. But then, i couldn't find it, it says it's installed (checked under ad remove programs) but I just don't know where it is. Does anyone have any ideas?
thanks



-Sewercake

---

### Post by raja on 2007-04-10
Type "wine" in the terminal and see. Also, if you right click on a ".exe" file in nautilus, you should see "open with wine" in the context menu if wine is installed.

---

### Post by sewercake on 2007-04-10
ok, i tried typing in "wine" and this is what it came up with > Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit


so then I put in "wine program" and it came up with >  Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/sam', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\program.exe": Module not found


so does anyone know what is wron? all help is greatly appreciated

---

### Post by david_kt on 2007-04-10
> **sewercake said:**
> ok, i tried typing in "wine" and this is what it came up with 

so then I put in "wine program" and it came up with 

so does anyone know what is wron? all help is greatly appreciated


Because you do not have any program name "program" in your home folder. You should try to to run real program, not imaginary. First of all, get your exe program. Put it in your linux box. Open terminal, navigate to the folder where you put your program, and then type:

```
wine your_program.exe
```

But you must make sure your_program.exe is really exist in your folder, not just imaginary.

DK

---

