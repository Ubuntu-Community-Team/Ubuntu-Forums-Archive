---
title: "Source vs. Binary"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by Maria_Firewire on 2006-06-12
Hello,

I am still quite new to ubuntu and linux but I love it! As I was trying to enable universe and multiverse repositories i kept running into the words "binary" and "source". I have actually run into these terms alot lately. I googled them and have looked them up in dictionaries but i'm still pretty confused as to what they mean.

I mean, i assume "source" is like the source code of programs and binary is....already compiled source?? Honestly i don't even understand WHAT compiling does...and as someone who enjoys programming, that's pretty embarrassing.

Well anyway, if anyone feels like explaining (or pointing me to a good website) these BASIC terms for me, that would be great! I'm tired of pretending I know what people are talking about...haha.

Thanks!

Maria

---

### Post by Sammi on 2006-06-12
Source code written in the programming language C++ can look something like this:[FONT=monospace]
[/FONT]#include <iostream>[FONT=monospace]
[/FONT]
using namespace std;[FONT=monospace]
[/FONT]
int main()[FONT=monospace]
[/FONT]{[FONT=monospace]
[/FONT]   cout<<"Hello World!\n";[FONT=monospace]
[/FONT]   cin.get();[FONT=monospace]
[/FONT]}


While after being compiled into binary code, the same thing may look something like this:
1111001010101010000001011111110001
1000100011101011001001111000011010
1010010010101011100010101010010100
1000101000111010010110000111010101
1000010100101100011010101001010100

---

### Post by Jagot on 2006-06-12
Source is referring to the source code and binary, in this instance, refers to the executable form of a program which has already been compiled.

This gives you a very brief explanation of compiling:

[http://webopedia.com/TERM/c/compile.html](http://webopedia.com/TERM/c/compile.html)

---

### Post by elemental666 on 2006-06-12
For clarity:

You compile source into a binary...

Try installing binaries first, if you experience problems it may be necessary to compile the program from source (which will also require a bit of knowledge reguarding make and possibly gcc).

---

### Post by mostwanted on 2006-06-12
> **Sammi]Source code written in the programming language C++ can look something like this:[FONT=monospace]
[/FONT]#include <iostream>[FONT=monospace]
[/FONT]
using namespace std said:**
> 
[/FONT]
int main()[FONT=monospace]
[/FONT]{[FONT=monospace]
[/FONT]   cout<<"Hello World!\n";[FONT=monospace]
[/FONT]   cin.get();[FONT=monospace]
[/FONT]}


While after being compiled into binary code, the same thing may look something like this:
1111001010101010000001011111110001
1000100011101011001001111000011010
1010010010101011100010101010010100
1000101000111010010110000111010101
1000010100101100011010101001010100

Technically binary isn't ones and zeros. When it's on a harddisk or in the RAM it's bits in state 1 or in state 0, and when it's executed it's electric signals, where 1 and 0 are reprented as the presence and absence of electricity in a certain small period. You can't send words through a copperline and even if you could, it you don't have hardware that is able to interpret them (otherwise computers would be a hell lot faster than they are today).

---

