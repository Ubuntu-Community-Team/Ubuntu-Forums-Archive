---
title: "gcc compiling.... bugs"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2007-08-08
Error lines, Makefile nad source code (hw.cpp)

Hi guys
I am ubuntu user but for some reason out of my control I am using fedora core 6 I believe. I have been trying to compile a simple c++ program but I got the following error: 
------------------------------------------------------------------------------------
[See attached file errorlog.txt]


--------------------------------------------
This is my makefile I am using:

       CFLAGS = -fPIC -DLINUX -Wall -I/usr/local/include
#      LDFLAGS = -L/usr/local/lib -lCAENVME
#    CPPFLAGS = -d -I/usr/include/c++/4.1.1/

hw: hw.o
    gcc -o hw hw.o

hw.o: hw.cpp
    gcc -c hw.cpp

clean:
    $(RM) hw *.o
----------------------------------------------
This is my source file (hw.cpp)

#include <iostream>
#include <fstream>

using namespace std;
    int main()
    {
        string s;
        string filename = "data.txt";
        ifstream fin( filename.c_str() );
        if( !fin ) {
            cout << "Error opening " << filename << " for input" << endl;
            exit(-1);
            }
          while( fin >> s ) {
              cout << "Read from file: " << s << endl;
          }
        
        fin.close();
        return 0;
    }



But for some reason I am having this problem compiling. I noticed my version of gcc is:
$gcc -V
Using built-in specs.
Target: i386-redhat-linux
Configured with: ../configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --enable-shared --enable-threads=posix --enable-checking=release --with-system-zlib --enable-__cxa_atexit --disable-libunwind-exceptions --enable-libgcj-multifile --enable-languages=c,c++,objc,obj-c++,java,fortran,ada --enable-java-awt=gtk --disable-dssi --enable-plugin --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-1.4.2.0/jre --with-cpu=generic --host=i386-redhat-linux
Thread model: posix
gcc version 4.1.2 20070626 (Red Hat 4.1.2-13)

Could anybody offer me some help about this problem I am having? Maybe should I am not initializing something that I should? This is just a testing file I am trying to run in my system. I really appreciate any feedbacks.
Krisfrajer

---

### Post by asmoore82 on 2007-08-08
it's been a _long_ time since I've seen C++ ...
I don't even know what that namespace business is about ...

but you declare CFLAGS that you never use.

GUESS: gcc $(CFLAGS) hw.cpp ... somthing like that :confused:

---

### Post by Zannax on 2007-08-08
Mmmm...
Shouldn't you:
#include<string>
?

If I remember well... :-)

---

### Post by Rocket2DMn on 2007-08-08
If it's C++, shouldn't you be using the g++ compiler instead of gcc?

---

### Post by LaRoza on 2007-08-08
Use g++, the command syntax is the same.

---

### Post by asmoore82 on 2007-08-08
> **Rocket2DMn said:**
> If it's C++, shouldn't you be using the g++ compiler instead of gcc?

that did make it work but why ?? ...

```
**asmoore@asmoore-laptop:~/src/hw$** gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v **--enable-languages=c,c++,fortran,objc,obj-c++,treelang** --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
**asmoore@asmoore-laptop:~/src/hw$** g++ -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
**gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)**
**asmoore@asmoore-laptop:~/src/hw$**
```

---

### Post by bashologist on 2007-08-08
Putting code in a code tag makes thing much easier to read. Did you try to compile it first without the make file?

```
#include <iostream>
#include <fstream>

using namespace std;

int main()
{
	string s;
	string filename = "data.txt";
	ifstream fin( filename.c_str() );
	if( !fin )
	{
		cout << "Error opening " << filename << " for input" << endl;
		exit(-1);
	}
	while( fin >> s )
	{
		cout << "Read from file: " << s << endl;
	}
	
	fin.close();
	return 0;
}

```

---

### Post by LaRoza on 2007-08-08
g++ is for C++
gcc is for C
G77 is for Fortran 77
gfortran is for Fortran (77 - 85)

They are different languages requiring different compilers.

G++ will be able to compile most C code as well, because of the backwards compatibility of C++.

---

### Post by asmoore82 on 2007-08-08
back when I took csci, gcc could do them all ... you didn't read my code ...

```
**asmoore@asmoore-laptop:~/src/hw$** g++ -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
***_gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)_***
```

---

### Post by Rocket2DMn on 2007-08-08
Don't worry about that, gcc means "GNU Compiler Collection", it is capable of working with all those languages you see listed.  gcc is the package of compilers as well as the C compiler itself.

---

### Post by ryangoff on 2007-08-08
shouldn't you #include <string> ?

also, I thought for the failed open statement, i think it's something like:

```
if ( !fin.open() )
```

---

### Post by bashologist on 2007-08-08
> **ryangoff said:**
> shouldn't you #include <string> ?

also, I thought for the failed open statement, i think it's something like:

```
if ( !fin.open() )
```

That's what I thought too but if you try it you'll see that string is defined already from the other headers.

Either should work to test if it's open. Anyone know if there's a difference?

---

### Post by Zannax on 2007-08-08
I've tried it in Anjuta IDE and it works perfectly.

I think the problem is that gcc doesn't know where to find the libraries to link (while everything is already configured in the IDE): you should check its man page and find it out how to tell it...

Sorry, right now I haven't time... :-)

---

### Post by krisfrajer on 2007-08-08
Ok guys.. thxs for the response. I have the feeling it has to do with some libraries, but I have no idea in what process it is missing it. In the linking part? or in the compiling part? Should I be using the -Idirname option while compiling?

I trried compiling it in the command prompt as gcc hw.cpp -o hw 
I also compiled it using the Makefile I created from a linux reference book. That is the makefile I attached but I kept having that same problem. I will keep scratching my head until I get a solution, but if anybody has any ideas about it... I will appreciate them. specially if you could show me how to declared the libraries for the linking part of the process as it was point out in the last posting.

I will try to compile this at home in my ubuntu machine... but tha has to wait until tonight. The thing about the system I am using now is that I have the impresion eclipse (c/c++, java IDE) updated my gcc but maybe it did not updated my libraries... Does that make sense?

---

### Post by krisfrajer on 2007-08-08
> **Zannax said:**
> I've tried it in Anjuta IDE and it works perfectly.

I think the problem is that gcc doesn't know where to find the libraries to link (while everything is already configured in the IDE): you should check its man page and find it out how to tell it...

Sorry, right now I haven't time... :-)

Zannax, what gcc version are you using and could you tell me if your IDE created a Makefile for you? Maybe it would be helpful if I could have a look at that.

---

### Post by krisfrajer on 2007-08-08
Ok guys... a simple command like g++ hw.cpp made my day. I still dont understand why gcc did not work. What is the difference between gcc and g++?
Cristian

---

### Post by Rocket2DMn on 2007-08-08
gcc is for C code, g++ is for C++ code.

---

### Post by Zannax on 2007-08-08
Ok.... actually the Anjuta IDE was launching **g++ ...** not gcc, right.
In fact g++ on the command line just works...

That's not a problem with paths, libraries or the like, as stated before.

Sorry for the bad "info" :-)

---

