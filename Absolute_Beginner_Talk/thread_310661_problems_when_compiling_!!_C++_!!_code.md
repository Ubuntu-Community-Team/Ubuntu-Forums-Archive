---
title: "problems when compiling !! C++ !! code"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2006-12-01
Hello! I'm trying to compile this:

```

#include <iostream.h>

int main()
{
cout << "test :)" << endl;
return 0;
}

```

with GCC and I get the next "errors":

```
cpp.c:1:22: error: iostream.h: No such file or directory
cpp.c: In function &#8216;main&#8217;:
cpp.c:5: error: &#8216;cout&#8217; undeclared (first use in this function)
cpp.c:5: error: (Each undeclared identifier is reported only once
cpp.c:5: error: for each function it appears in.)
cpp.c:5: error: &#8216;endl&#8217; undeclared (first use in this function)

```

I tried even without ".h" and the same... I took a look through /usr/include/c++ folder and I saw, in both, 4.0.2 and 4.0 folders the "iostream" file exists...
Does anybody know why, and how do I solve this?
Thanx in advance.

---

### Post by LLRNR on 2006-12-01
Never been a big fan of the "iostream" myself, mate, sorry to disappoint you...
```

#include <stdio.h>

int main() {
  int x, y;
  printf ("x = "); scanf ("%d", &x);
  printf ("y = "); scanf ("%d", &y);
  printf ("%d + %d = %d\n", x, y, x+y);
  return 0;
}
```

Then do:```
gcc -o test test.c
```assuming you named your file *test.c* and execute it with```
./test
```:D

LLRNR

---

### Post by hod139 on 2006-12-01
you should consider posting this in the programming talk section, you will most likely get more and faster feedback.

You need to use iostream without the h
```

#include <iostream>

```and use 
```

std::cout

``````

std::endl

```

---

### Post by faraazs on 2006-12-01
you can get around using std:: before everything if you just add this after your include line:

```
using namespace std;
```making your final code look like this:```
#include <iostream.h>
using namespace std;

int main()
{
cout << "test :)" << endl;
return 0;
}
```

And I'm not sure but if you are using C++, you shouldn't need to do #include <iostream.h>...#include <iostream> should be fine. The .h inclusion is more of a C thing...

This isn't really a forum to help with programming code though :-/

---

### Post by the_nomad on 2006-12-01
for
```
#include <iostream>
using namespace std;

int main()
{
cout << "test :)" << endl;
return 0;
}
```

I get
```
cpp.c:1:20: error: iostream: No such file or directory
cpp.c:2: error: syntax error before &#8216;namespace&#8217;
cpp.c:2: warning: data definition has no type or storage class
cpp.c: In function &#8216;main&#8217;:
cpp.c:6: error: &#8216;cout&#8217; undeclared (first use in this function)
cpp.c:6: error: (Each undeclared identifier is reported only once
cpp.c:6: error: for each function it appears in.)
cpp.c:6: error: &#8216;endl&#8217; undeclared (first use in this function)

```



and for
```
#include <iostream>
int main()
{
std::cout << "test :)" << std::endl;
return 0;
}

```
I get
```
cpp.c:1:20: error: iostream: No such file or directory
cpp.c: In function &#8216;main&#8217;:
cpp.c:4: error: syntax error before &#8216;:&#8217; token

```

lol I'm really CONFUSED :(

---

### Post by faraazs on 2006-12-01
What is the compile command that you are using? Your code works fine for me with this build command:```
g++ file.cpp
```remember to have proper extensions for your file names and to use the c++ compiler on C++ files and the C compiler on C files.

Personally, I think you just dont have the header files on your computer. When you installed the compiler, somehow they got deselected for install. You probably need a package called libstdc++6...but my suggestion is that you just run this command:```
sudo apt-get install build-essential
```

---

### Post by the_nomad on 2006-12-01
thanx alot dudes! i was using the "gcc ..." command :)

---

