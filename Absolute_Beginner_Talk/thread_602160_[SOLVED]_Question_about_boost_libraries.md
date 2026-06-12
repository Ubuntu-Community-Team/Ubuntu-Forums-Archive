---
title: "[SOLVED] Question about boost libraries"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by leileicats on 2007-11-01
Several questions about boost library installation:
I have downloaded the **boost_1_34_1.tar.bz2** and extract to **/usr/local/boost_1_34_1**.
1) I use the simple program on the official website to test the header-only library first.
```
#include <boost/lambda/lambda.hpp>
#include <iostream>
#include <iterator>
#include <algorithm>

int main()
{
    using namespace boost::lambda;
    typedef std::istream_iterator<int> in;

    std::for_each(
        in(std::cin), in(), std::cout << (_1 * 3) << " " );
}
```

And the compilation is successful, ```
lei@maverick:~$ g++ -I /usr/local/boost_1_34_1 -o example example.cpp
```

But I want to know what is the meaning of option "**[COLOR="Red"]-I[/COLOR]**"? Besides I need provide information of the position of boost **/usr/local/boost_1_34_1** to complier, but if I just want to simple key in command:
```
lei@maverick:~$ g++ -o example example.cpp
```
Then the compiler could find the boost library automatically, what should I do next, or do I need move the file to other place?

2) If I also want to use libraries which must be built separately, such as Boost.IOStreams, **which path** do I install the boost libraries, then I could simple key in command such as 
CODE]lei@maverick:~$ g++ -o example example.cpp[/CODE], the GCC will automatically find the boost libraries.

If I easily build:
```

$ cd /usr/local/boost_1_34_1
$ make install
```
Is the default place correct for me? Or I need modify
```
$ ./configure --prefix=[COLOR="Red"]**?????**[/COLOR]

```

It will cost me a lot of time to build boost, so I have to make it clear. Thanks

---

### Post by Paul820 on 2007-11-01
Boost in available from the repositories, **version 1.34.1**. If you installed it from there you don't need to specify the path when building it as it is automatically found by the compiler.

---

### Post by leileicats on 2007-11-01
> **Paul820 said:**
> Boost in available from the repositories, **version 1.34.1**. If you installed it from there you don't need to specify the path when building it as it is automatically found by the compiler.
I am using Ubuntu 7.04, so I check the version of boost in my Synaptic Package Manage, and it is still Version 1.33.1.:(

---

### Post by leileicats on 2007-11-01
> **Paul820 said:**
> Boost in available from the repositories, **version 1.34.1**. If you installed it from there you don't need to specify the path when building it as it is automatically found by the compiler.
The boost version in my Synaptic Package Manage is still Version 1.33.1. How could I update it to the latest version? Thanks.

---

### Post by leileicats on 2007-11-01
I want to install boost library through Synaptic Package Manage. I am using Ubuntu 7.04 and the boost library in Synaptic is still version 1.33.1. How could I update to the latest version in Synaptic? 

If I download the source code **boost_1_34_1.tar.bz2**, I use the command **checkinstall** , is it the same with installing through Synaptic?

Thanks

---

### Post by Paul820 on 2007-11-01
Sorry, i didn't know you were using feisty, i'm using gutsy. Maybe you will have to specify the path each time, or specify the path usr/include/boost/

---

### Post by leileicats on 2007-11-01
> **Paul820 said:**
> Sorry, i didn't know you were using feisty, i'm using gutsy. Maybe you will have to specify the path each time, or specify the path usr/include/boost/
I have the CD-ROM of Ubuntu 7.10, how could I install boost library from CD-ROM through Synaptic?:)

---

### Post by leileicats on 2007-11-01
I have the CD-ROM of Ubuntu 7.10. How could I install boost libraries from that CD-ROM through Syntactic?

---

### Post by Paul820 on 2007-11-01
Boost might not be on the install CD, that's the problem. I think it only comes with build-essential on there.

---

### Post by leileicats on 2007-11-02
I install 1.33.1** filesystem** from respo, and find the install file: [COLOR="Red"]**/usr/include/boost/filesystem**[/COLOR].

But when I use the downloaded source code to compile by myself, it will generate file **"/usr/local/include/boost_1_34_1/boost/filesystem/*.*"** and **"/usr/local/lib/*.*"**.

Follow the guide from official Boost website, I could use the command
```
$ g++ -I path/to/boost_1_34_1 example.cpp -o example \
  [COLOR="Red"] /usr/local/lib/libboost_filesystem-gcc41-mt-d-1_34_1.a[/COLOR]
```
to compile the sample program. But it is inconvenient to add such long [COLOR="Red"]/usr/local/lib/libboost_filesystem-gcc41-mt-d-1_34_1.a[/COLOR],
and the simple command: [COLOR="Red"]g++ -I path/to/boost_1_34_1 example.cpp -o example [/COLOR] will failed. But when I installed from respo, the command works!

---

### Post by leileicats on 2007-11-03
Hey folks, I need some help about boost libraries installation.

1) I am using Ubuntu 7.04, so the boost libraries version is 1.33.1, but I really wish to use the latest version 1.34.1

2) I follow the guide on Boost website of "Getting Started on Unix Variants". After installation, I will have Boost binaries in the **/usr/local/lib/*.*** and Boost headers in the **/usr/local/include/boost_1_34_1/boost/*.***. By using simple program example, I could link my program to a boost library using command:
```
$ g++ -I /usr/local/include/boost_1_34_1/boost example.cpp -o example /usr/local/lib/libboost_regex-gcc34-mt-d-1_34.a
```

The program works well but the command seems too long and tedious. I tried to install the Boost 1.33.1 from respo. The generated libraries after installation is all under path **/usr/include/boost/*.***.
Then I could simply use command for compilation: 
```
$ g++ example.cpp -o example
```

How could I install 1.34.1 Version Boost library that I could easily use the command to compile?

---

