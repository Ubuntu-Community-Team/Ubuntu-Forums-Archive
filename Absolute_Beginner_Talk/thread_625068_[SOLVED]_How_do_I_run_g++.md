---
title: "[SOLVED] How do I run g++?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by S3loth on 2007-11-27
SPM says it is install and I can find a g++ file in usr/bin, but it won't open. Any tips on how to get it to run?

---

### Post by ZipoTe on 2007-11-27
Not sure about what you want.

If you want to use g++ to compile you have to do it via terminal. Read the g++ manual

---

### Post by S3loth on 2007-11-27
I can't get g++ to run at all. I went to install it, but SPM said it was already installed, now I can't find it anywhere.

---

### Post by timbounceback on 2007-11-27
sudo apt-get install build-essential

should work - then run g++

---

### Post by S3loth on 2007-11-27
Nothing happens when  I type g++ in alt+F2

---

### Post by stchman on 2007-11-27
> **S3loth said:**
> SPM says it is install and I can find a g++ file in usr/bin, but it won't open. Any tips on how to get it to run?

gcc/g++ is installed by default in Ubuntu.  Unfortunately the build-essential package is not.

```
sudo apt-get install build-essential
```

Once that is done simply type g++ in a terminal and you are good to go.

You will have to do some reading on the CLI syntax.

---

### Post by timbounceback on 2007-11-27
You don't want to use g++ through Alt-F2, as it doesn't have a GUI - use it from the command line.

---

### Post by S3loth on 2007-11-27
Okay, when I type g++ in terminal it says:

g++: no input files

is that what it should say? Now do I have to put in a c++ file. btw when you're done typing a c++ file, what do you save it as?

---

### Post by Paul820 on 2007-11-27
Open a text editor, gedit will do, copy and paste this
```
#include <iostream>

int main()
{
    std::cout << "Hello World!" << std::endl;
    
    return 0;
}

```
Save it to your desktop as **helloworld.cpp**, open a terminal and type
> cd ~/Desktop
Now in the terminal again type
> g++ -o helloworld helloworld.cpp
To run it type in the terminal again
> ./helloworld

---

### Post by S3loth on 2007-11-27
Thanks, that works :)

---

### Post by Paul820 on 2007-11-27
No problem, if you need any more programming help, post it in the programming section of the forums 
[http://ubuntuforums.org/forumdisplay.php?f=39]("http://ubuntuforums.org/forumdisplay.php?f=39")
Good luck :)

---

