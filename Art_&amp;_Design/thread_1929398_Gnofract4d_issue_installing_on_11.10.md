---
title: "Gnofract4d issue installing on 11.10"
date: 2012-02-22
forum: Art &amp; Design
---

### Post by kbk on 2012-02-22
Hello, I am trying to install Gnofract4d on Ubuntu 11.10.  There is a known issue with the .deb package, caused by gnofract4d depending on a python version of <2.7, and ubuntu having 2.7.2.  I have tried to remedy this by installing python 2.6.7 to /opt/python2.6.7 and creating a link to /usr/bin/python2.6.7, however, when I run the installer it fails because it is still looking at python 2.7 .  Can anyone help me with this issue?  This is where the script errors out:  ```
creating /usr/local/lib/python2.7/dist-packages/fract4d
error: could not create '/usr/local/lib/python2.7/dist-packages/fract4d': Permission denied

```

---

### Post by 23dornot23d on 2012-02-22
I too am having problems with this ......

> 
root@keith-Aspire-7730ZG:/home/keith/Downloads# gdebi gnofract4d_3.14-1ubuntu1_i386.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Building data structures... Done 
This package is uninstallable
Dependency is not satisfiable: python (< 2.7)


Also Cinepaint - is asking the same - why is there no backward compatibility ..... ?

root@keith-Aspire-7730ZG:/home/keith/Downloads# aptitude install cinepaint
The following NEW packages will be installed:
  cinepaint cinepaint-python{ab} oyranos-icc{a} 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,137 kB/8,995 kB of archives. After unpacking 16.5 MB will be used.
The following packages have unmet dependencies:
  cinepaint-python: Depends: python (< 2.7) but 2.7.2-9ubuntu2 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     cinepaint [Not Installed]                          
2)     cinepaint-python [Not Installed]                   



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
root@keith-Aspire-7730ZG:/home/keith/Downloads# 

What is the easy and safe method of [_[COLOR=Blue]**going back to Python 2.6**[/COLOR]_]("https://www.google.com/search?q=going+back+to+Python+2.6")

Not sure how to get this ... yet ....

[http://www.python.org/getit/releases/2.6.7/](http://www.python.org/getit/releases/2.6.7/)

Even though we can install the old version ... the package manager does not use it so
still reports the error 
( so it cannot be done easily and may lead to other problems - can use xaos or something else )


What we need to know is - is it possible to switch between the Two versions easily ... seen that Windows Users
can do this .....

[http://stackoverflow.com/questions/4583367/how-to-run-multiple-python-version-on-windows](http://stackoverflow.com/questions/4583367/how-to-run-multiple-python-version-on-windows)

---

### Post by kbk on 2012-02-23
Bump

---

### Post by 23dornot23d on 2012-02-23
I got it running but .... 

[IMG]http://img651.imageshack.us/img651/4228/snapshot2j.jpg[/IMG]

Everytime you do a update ..... it wants to remove it ..... my advice is to use a distro like maverick
 for it


Possible idea >>> [[COLOR=Red]_**on the help site too **_[/COLOR]]("http://sourceforge.net/projects/gnofract4d/forums/forum/2319/topic/5056937"), using a opt directory .... and linking to python 2.6

---

### Post by kbk on 2012-02-23
I got mine working as well, by installing python2.6.7 to the /opt directory XD .  The problem I was running into was that I hadn't made my symlink correctly and also bungled the permissions.  It's working like a dream now.  I used this guide to install version 2.6.7:  [http://achinghead.com/installing-multiple-versions-python.html](http://achinghead.com/installing-multiple-versions-python.html)
and I also found some useful info on the gnofract4d help page as posted above.

---

### Post by 23dornot23d on 2012-02-23
Just trying that now ..... but mine is missing somethings when I config then make the
python 2.6.7

Can you walk me through it - step by step please .... * ( It seems the way I linked it messed it up )

./configure --prefix=/opt/python2.6.7


> 
build/temp.linux-i686-2.6/opt/Python-2.6.7/Modules/_ctypes/libffi/src/x86/ffi.o build/temp.linux-i686-2.6/opt/Python-2.6.7/Modules/_ctypes/libffi/src/x86/sysv.o -L/usr/local/lib -o build/lib.linux-i686-2.6/_ctypes.so

Failed to find the necessary bits to build these modules:
_bsddb             _curses            _curses_panel   
_hashlib           _sqlite3           _ssl            
_tkinter           bsddb185           bz2             
dbm                gdbm               linuxaudiodev   
ossaudiodev        readline           sunaudiodev     
zlib                                                  
To find the necessary bits, look in setup.py in detect_modules() for the module's name.


Failed to build these modules:
crypt              nis                                

running build_scripts
root@keith-Aspire-7730ZG:/opt/Python-2.6.7# 

Tried it any way - but obviously need to know how to get the two modules .... crypt & nis

> 
root@keith-Aspire-7730ZG:/home/keith/Downloads/gnofract4d-3.14# ./setup.py build && ./setup.py install bash: ./setup.py: /opt/python2.6.7
running build
running build_py
running my_build_ext
compiling with None
building 'fract4d.fract4dc' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -D_REENTRANT=1 -DTHREADS=1 -DPNG_ENABLED=1 -DJPG_ENABLED=1 -Ifract4d/c -I/usr/include/python2.7 -c fract4d/c/fract4dmodule.cpp -o build/temp.linux-i686-2.7/fract4d/c/fract4dmodule.o -Wall -I/usr/include/libpng12
cc1plus: warning: command line option &#8216;-Wstrict-prototypes&#8217; is valid for Ada/C/ObjC but not for C++ [enabled by default]
fract4d/c/fract4dmodule.cpp:14:20: fatal error: Python.h: No such file or directory
compilation terminated.
error: command 'gcc' failed with exit status 1
root@keith-Aspire-7730ZG:/home/keith/Downloads/gnofract4d-3.14# 



---

