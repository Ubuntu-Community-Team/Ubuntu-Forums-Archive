---
title: "Installing C++ Libraries"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by brawr on 2007-11-17
Hi!
I need to install some C++ libraries for my CS class on my home machine, but I'm not sure how to do it. I've installed GCC C++ from the Package Manager, do I just copy these libraries into that directory? If so, what directory is that?

Sorry, I just recently switched after 14 years of Windows, I'm still very new :)

---

### Post by Majorix on 2007-11-17
```
sudo apt-get install build-essential
```

Then you can include headers in your sourcecodes.

---

### Post by brawr on 2007-11-17
Is there anything else I need add to the header? My compiler still can't find the library I'm trying to include - for example:
```
#include "ccc_win.h"
```

---

### Post by bongobonga on 2007-11-17
I'm not entirely sure what your problem is, but I'll try and answer anyway. 

There is no specific location where libraries/header files have to be installed in a linux box to get them to compile. The default directory would probably be '/usr/include' but it is always possible to pass a given path to the compiler. 
So, for example, if you want to include the file "ccc_win.h", then on the command line you just have to use the '-I' option with the compiler and specify the directory that contains the desired header files, such as 
```
g++ -I/path_to_directory_containing_cc_win.h main.cpp
```
 
You will also have to specify the location of the actual library using the '-L' option. The library will be a file named something like 'ccc_win.a', or 'ccc_win.so.1.0.1' depending on whether it is a static or shared library. 
So the full compile command line argument would be something like. 
```
 g++ -I/path_to_directory_containing_cc_win.h -L/path_to_ccc_win_library main.cpp 
```

Finally, when running programs, the compiled binary file will need to know where to find any shared libraries. The default directory for those is '/usr/lib*' You can simply copy the library you need into this directory and any executable files will run fine. If you want your library to be stored in a different location then simply add that path into the file '/etc/ls.so.conf' and run the command 'ldconfig'. That directory will then be added to the locations that are looked in for libraries at run time. In general though, this is a step that you will seldom have to do, since most libraries that you will be using already have installers built for them which takes care of all this.

---

