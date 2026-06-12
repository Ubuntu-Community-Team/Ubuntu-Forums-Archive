---
title: "[SOLVED] Help with g++/gcc"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by ertrules22 on 2007-08-08
Okay, when I try and run g++ or compile code in it from the terminal, etc. it says:
```
Unable to exec g++.real: No such file or directory

```
And if I try to compile this c++ code in gcc using this line:
```
gcc test -o tester -x <c++>

```
I get this error:
```
bash: syntax error near unexpected token `newline'

```
Here is the code I am trying to compile, I am used to using Dev-C++, so if it is a different format or something, please help!  Anyways, here is the code that I am trying to get to compile:
```
int main()
{
cout << "Hello World!" << endl;
system ("PAUSE");
return (0);
}
```
and this is just a sample program to test out the compiler out of a book I am learning C++ from.  I really need help, so I can finish my C++ class that I am taking!  Otherwise I will have to program on a desktop running Windows, and I would really like to have mobile programming capabilities.
(oh, by the way, I edited the above source using gedit, and saved it as test.cpp, so if this is a problem, tell me in a NICE manner!  Thanks!)
ertrules22

---

### Post by ertrules22 on 2007-08-08
Oh, and I also know that g++ and gcc are installed, because I used these commands from another thread here:
> Yes, it looks like you already have it installed. So confirm it with
Code:

dpkg -l | grep g++

This will list the packages, probably "g++-4.1", so you can then do
Code:

dpkg -L g++-4.1

to list the contents.

Or
Code:

which g++

to find the executable, usually it will be located in /usr/bin..

---

### Post by Hospadar on 2007-08-08
Is this the entire code you are trying to compile?
```

int main()
{
  cout << "Hello World!" << endl;
  system ("PAUSE");
  return (0);
}

```
if that's the case, you will want to change it like so

```

#include <iostream>

using namespace std;

int main()
{
cout << "Hello World!" << endl;
system ("PAUSE");
return (0);
} 

```cout and system belong to the std namespace so unless you resolve their scope per-use (std::cout, std::system(blah)) you need to use the namespace.

And iostream is needed to dump the stuff into the stream.

Try that with g++
```

g++ test
./a.out

```(a.out is the default executable name)

Oh! I forgot
To get g++ working properly also you will need to rename your file so it ends with .cpp (if it's a c++ source file)
when using g++ be sure to use proper file extensions (.c, .cpp, .h, .hpp)

---

### Post by ertrules22 on 2007-08-08
I did only have that code
```
int main()
{
  cout << "Hello World!" << endl;
  system ("PAUSE");
  return (0);
}
```
but I changed it to this:
```
#include <iostream>

using namespace std;

int main()
{
cout << "Hello World!" << endl;
system ("PAUSE");
return (0);
}
```
and I saved it as test.cpp and it still didn't compile as g++ or gcc, it gave me the same exact error messages as before!:confused::confused:

---

### Post by ertrules22 on 2007-08-08
I really need help, I have tried doing a lot of things, changing the entire source code, reading countless tutorials, and I nor one of my Ubuntu using neighbors can figure out what is wrong!

---

### Post by Rocket2DMn on 2007-08-08
I would think it's time to reinstall the compiler stuff
```
sudo apt-get autoremove --purge build-essential
```  Reinstall:
```
sudo apt-get install build-essential
```

---

### Post by Cypher on 2007-08-08
In the terminal, do the following
```

cd /usr/bin
ls -l g++*
file g++*

```
and show us the output..

---

### Post by sputn1k on 2007-08-08
As previous recommended reinstall build-essential as the posted code compiles fine.

---

### Post by ertrules22 on 2007-08-08
Okay, when I did the reinstall of build-essentials, it asks for the disk labeled Ubuntu 7.04 etc. etc.  my disk is burned from the internet, as an iso, and it does not recognize it, although, it comes up in my cdrom and says Ubuntu 7.04 desktop i386 or whatever.  So, now I can't reinstall the build-essentials!
Help!

---

### Post by Rocket2DMn on 2007-08-08
You need to remove the line in your sources.list for the CD as a repository
edit the file:
```
gksudo gedit /etc/apt/sources.list
```
Place a # in front of the line for the cd as a repo.

---

### Post by ertrules22 on 2007-08-08
Okay, I got the build-essentials back thanks to Rocket2DMn
> You need to remove the line in your sources.list for the CD as a repository
edit the file:
Code:

gksudo gedit /etc/apt/sources.list

Place a # in front of the line for the cd as a repo.
Then I ran this like Cypher said:
```
cd /usr/bin
ls -l g++*
file g++*
```
and here is what I got for 
ls -l g++* :
```
lrwxrwxrwx 1 root root     11 2007-08-08 11:47 g++ -> builder-c++
-rwxr-xr-x 1 root root 185856 2007-03-02 19:50 g++-4.1
lrwxrwxrwx 1 root root      7 2007-08-08 13:35 g++.real -> g++-4.1

```
and here is what I got for 
file g++* :
```
g++:      symbolic link to `builder-c++'
g++-4.1:  ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), stripped
g++.real: symbolic link to `g++-4.1'

```
There you go, does that help?

---

### Post by ertrules22 on 2007-08-08
I really need this to work soon!
:mad:

---

### Post by Rocket2DMn on 2007-08-08
Can you please try to compile your code and post here everything that is says (including the command you ran).  That will help us help you more effectively.

---

### Post by ertrules22 on 2007-08-08
Sure, here it is:
```
g++ test
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status

```
that is what it says now, when I compile through g++, unless I am typing it wrong :confused::confused:
and here is how I did it through gcc:
```
gcc test.cpp -o tester11 -x <c++>
bash: syntax error near unexpected token `newline'
```
If you need anything else, I can get it for you (I'm really not THAT dumb, [I hope])
:lolflag:
Oh, and here is the source code:
```
#include <iostream>

using namesapce std;

int main()
{
cout << "Hello World!" << endl;
return (0);
}
```

---

### Post by ertrules22 on 2007-08-08
bump:lolflag:

---

### Post by Rocket2DMn on 2007-08-08
Add a second include:
```
#include <ostream>
```
also, you mispelled "namespace"
When you return, you dont use () since return is not a function, you just
```
return 0;
```

Now you have 
```
#include <iostream>
#include <ostream>

using namespace std;

int main()
{
cout << "Hello World!" << endl;
return 0;
}
```

Also, don't use gcc since this is not C code, it is C++.  gcc will not work.  Always use g++ for C++ code.

---

### Post by ertrules22 on 2007-08-08
Okay, same thing!  I realize that I mispelled it, and fixed it:
```
#include <iostream>
#include <ostream>

using namespace std;

int main()
{
cout << "Hello World!" << endl;
return 0;
}

```
and when I get into terminal I type this and get this error:
```
g++ test
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status

```

---

### Post by Rocket2DMn on 2007-08-08
Change the filename to "test.cc" or "test.cpp".
If you can, test the code on another machine.  I'm not in front of my laptop to test it for you.

---

### Post by ertrules22 on 2007-08-08
Okay, and I tried to change it to g++ test.cpp, and it sort of paused for a second, and then came back up with my regular terminal line you know the ~$ thing, but no error messages, so okay, I will try it on another computer and let you know!:)

---

### Post by Rocket2DMn on 2007-08-08
> **ertrules22 said:**
> Okay, and I tried to change it to g++ test.cpp, and it sort of paused for a second, and then came back up with my regular terminal line you know the ~$ thing, but no error messages, so okay, I will try it on another computer and let you know!:)

So did it compile OK on your computer after you changed it?

---

### Post by ertrules22 on 2007-08-08
Okay, whoops, I didn't look in my home directory, and I actually had a.out, and when I type:
```
/home/ertrules22/a.out
```
and it ran fine, so I did this:
```
g++ test.cpp -o test
```
and now it works!  I couldn't have done it without you and everyone elses help though, but mostly you!
Thanks a million!
ertrules22
:KS:KS:KS:):):guitar::guitar::guitar:

---

### Post by ertrules22 on 2007-08-08
Now it works just fine!
Thanks again!
\\:D/\\:D/\\:D/\\:D/\\:D/\\:D/\\:D/\\:D/

---

### Post by ertrules22 on 2007-08-08
Okay, enough with the smileys, sorry I am happy and bored and tired, bad combination!](*,)

---

### Post by nickburns on 2007-08-08
way to go ertrules22  :)

---

### Post by ertrules22 on 2007-08-08
Thanks for the moral support nickburns! :)

---

