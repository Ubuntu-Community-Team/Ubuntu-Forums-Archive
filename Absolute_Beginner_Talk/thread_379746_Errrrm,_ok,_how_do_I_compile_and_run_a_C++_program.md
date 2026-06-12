---
title: "Errrrm, ok, how do I compile and run a C++ program"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Mardok45 on 2007-03-08
I think this counts more as a noob question rather than a programming one...

Alrighty, I have the source code:

#include <iostream>
using namespace std;
int main()
{
cout << "Hello world" << endl;
return 0;
}

Now, I went into the shell and typed:
gcc /path/to/file.cpp

It then the shell went back to the $ awaiting further input, so I guess everything went fine.  Now... how do I run it???

---

### Post by Tomosaur on 2007-03-08
If compilation was successful, you will have a new file in the same directory as the source file. It will be called 'a.out'. You can run it by typing:
```

/path/to/a.out

```

:)

---

