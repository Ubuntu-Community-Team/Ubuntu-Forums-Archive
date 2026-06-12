---
title: "[SOLVED] C++ compilation error"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-16
> #include<iostream>
int main()
{
cout<<"great";
return 0;
}
when i run this program under C(using printf and stdio.h),it works.but when the above program is compiled it gives the following error;
> arvind@arvind:~$ gcc -o a a.cpp
a.cpp: In function ‘int main()’:
a.cpp:6: error: ‘cout’ was not declared in this scope

pls help.

---

### Post by cmnorton on 2008-02-16
You need two changes:

1) Add 

using namespace std; 

after your include.

2) Use g++, instead of gcc.

---

### Post by asmoore82 on 2008-02-16
I assume that you've already installed ``build-essential'' package ...

you need to use `g++` to compile C++ programs instead of `gcc`
also, I had to change ``iostream'' to ``iostream.h'' ...

```
**asmoore@pickles:~/fun$** cat a.cpp 
#include <iostream.h>

int main()
{
        cout << "great\n";
        return 0;
}

**asmoore@pickles:~/fun$** g++ -o a a.cpp 
In file included from /usr/include/c++/4.1.3/backward/iostream.h:31,
                 from a.cpp:1:
/usr/include/c++/4.1.3/backward/backward_warning.h:32:2: warning: #warning This file
includes at least one deprecated or antiquated header. Please consider using one of the
32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting
the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the
deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
**asmoore@pickles:~/fun$** ./a 
great
```

---

### Post by stevescripts on 2008-02-16
2 ways to fix this:

Either make the call to cout "std::cout", or add using namespace std;

```

#include<iostream>
int main()
{
    std::cout<< "great" << std::endl;

    return 0;
}

```  
 
or:
```

#include<iostream>

using namespace std;

int main()
{
    cout<< "great" << endl;

    return 0;
}


```

Hope this helps.

Steve
(I appear to be typing too slow today - others already answered)

---

