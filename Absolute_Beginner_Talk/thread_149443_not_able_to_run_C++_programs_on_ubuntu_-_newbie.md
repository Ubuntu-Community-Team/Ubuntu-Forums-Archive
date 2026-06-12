---
title: "not able to run C++ programs on ubuntu - newbie"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by peekay on 2006-03-23
Hi
 I just installed ubuntu and i ran the following command to install gcc
sudo apt-get install gcc g++

i then typed in this simple c++ program and called it test.cpp

#include <iostream.h>
int main()
{
        cout<<"this is a test program";
        return 0;
}

when i compile it as 

gcc test.cpp

I get a lot of error messages ..any help will be appreciated

thanks
PK

---

### Post by KansasJoe on 2006-03-23
sudo apt-get install build-essential

---

### Post by engla on 2006-03-23
[QUOTE=peekay]Hi
 I just installed ubuntu and i ran the following command to install gcc
sudo apt-get install gcc g++

i then typed in this simple c++ program and called it test.cpp
...[/QUOTE]
1. You first have to install build-essential so that you can actually compile anything. Yeah, build-essential includes gcc and g++ but also a lot of other things.
2. Your program is actually not standard C++. You want this, else it won't compile:


```
#include <iostream>
int main()
{
        std::cout<<"this is a test program\n";
        return 0;
}
```

---

### Post by TylerH on 2006-03-23
try using g++ instead of gcc

as in:

```
g++ fileName.cpp -o appName
```

---

