---
title: "iostream not installed"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Kevin the Olden on 2007-12-26
Seems the c++ libraries and headers aren't on my system. using package manager or apt-get, what do I actually install so I can compile c++ programs? Thanks and have a good 2008...
Oh, and "HO HO HO have a Merry Christmas!!!!"

---

### Post by taurus on 2007-12-26
You need the build-essential package that would include everything that you need to run gcc/g++.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by meindian523 on 2007-12-26
Um,```

sudo apt-get install build-essential
```?

edit:
taurus beat me to it.....BTW,where on ebay do I get those? ;-)
And thanks for confirmation of my answer...

---

### Post by Kevin the Olden on 2007-12-26
Did the update and build essential (that thrashed for a while!). Still no joy. Tried a restart but still no joy. (sigh...)

---

### Post by taurus on 2007-12-26
What was the exact command that you ran and was there any error message?

Which release are you running?

Can you post your /etc/apt/sources.list?
```
cat /etc/apt/sources.list
```

---

### Post by Kevin the Olden on 2007-12-26
ran sudo update then sudo apt-get install build-essential. There were no errors. I found iostream under /usr/include/c++/4.1.2 This doesn't seem right to me. (not that I know what 'right' is). It's 88 degrees outside and 1:30 in the afternoon, I'm on vacation so maybe a cold beer under the apple tree is a better thing for me to be doing right now...

cheers...

---

### Post by taurus on 2007-12-26
Have you written a C program and tried to compile it?

I guess you guys in the Southern Hemisphere are in the middle of Summer right now.

---

### Post by Kevin the Olden on 2007-12-26
I can compile straight 'c' programs, but using c++ causes the troubles. yep, in the middle of summer and no water!!!  Can I come and live with you :-)

On my ubuntu computer at work, I don't have the problem. I set it up but don't know what I've done different here at home. Oh well, I'm not going to sweat over it, too many other things to be doing.

---

### Post by Hospadar on 2007-12-26
sure you didn't just forget 
#include <iostream>
 or
using namespace std; (or std::stdin)

Also note too, if you want to compile c++, the file needs to have the .cpp suffix (not just .c) and you need to use g++, not gcc.  There are no special directives to include iostream or any of the standard libraries.  What exactly are you trying to compile, what command are you using to compile it, and specific errors do you get?  If they arn't of the confidential nature, would you mind posting an example of the program you are having trouble with (the source files, or a link to them perhaps)

---

### Post by Kevin the Olden on 2007-12-26
#include <iostream>
#include <string>
using namespace std;

int main(void)
{
   string s;

   s = "hello";

   cout << s;

  return 0;
}

using cc -o foo foo.c then tried gcc -o foo foo.c then tried gcc -foo foo.cpp after renamimg the source file. I have been programming for 25 years in c and c++ but only using MS-DOS and Windoze.

---

### Post by meindian523 on 2007-12-28
I think you should do what Hospadar said and use g++ for C++ programs WITH the extension ".cpp"

---

