---
title: "[SOLVED] trouble compiling C++ code"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Kymus on 2007-11-04
I just started reading *Sams Teach Yourself C++ For Linux in 21 Days* and so after installing recommended compiler software (*Geany*), I got to work.

To no surprise, I am having some n00b issues with compiling. I've read Geany's manual and that really hasn't helped me :(.

After writing the code for the simple *Hello World*, I figured out that I needed to set the file type to *C++ source* and then I push the *compile* button and it says it's compiled but... I'm still just seeing source code in the output folder; not an executable. This is - almost - my first time programing (aside from the very small amount of time I spent with VB), so I am assuming that this is most likely an issue of me overlooking something.

thanks for any feedback :-D

---

### Post by ddrichardson on 2007-11-04
I've got that book somewhere, it came as a set on developing kernel modules for some reason (if you develop modules you probably don't need a C++ in 24 hours book).

Have you tried compiling from the command line - it'll give you more feedback as to the problem.

---

### Post by amingv on 2007-11-04
Hello,

I have a bit of time learning C++, but I have never used "Geany" for my practices, so I cannot help you with that.
What I can help you with would be suggesting another compiler: use the GNU Compiler Collection (GCC), it comes preinstalled in many Linux distributions and works perfectly fine in my opinion. 

Pros: it won't give you any headaches while compiling and, if ever you decided to learn more than one computer language, you would have all (or most) of the tools at hand.
It has an easy interface that will take care of compiling & linking, you just need to type:
```
g++ /home/user/myprogram.cpp -o /home/user/myprogram
```

Cons: GCC is not an IDE (Integrated Development Environment), so you have to write your code somewhere else (Kate, Emacs, etc), save it as *.cpp and then compile.

Overall: a GREAT compiler, so good that I use MinGW whenever I'm forced to run Windows.

---

### Post by ddrichardson on 2007-11-04
Sorry I meant to mention this earlier - Geany isn't a compiler its an Integrated Development Environment.

---

### Post by Kymus on 2007-11-04
> **ddrichardson said:**
> I've got that book somewhere, it came as a set on developing kernel modules for some reason (if you develop modules you probably don't need a C++ in 24 hours book).

Have you tried compiling from the command line - it'll give you more feedback as to the problem.

I would, were I not almost command line stupid, currently :-\

---

### Post by ddrichardson on 2007-11-04
amingv has shown the command line.

---

### Post by Kymus on 2007-11-04
> **ddrichardson said:**
> Sorry I meant to mention this earlier - Geany isn't a compiler its an Integrated Development Environment.

Oh boy, that explains a lot right there :lolflag:

I ponder then, what is with all the "build" "make" "compile" options :confused:

---

### Post by Kymus on 2007-11-04
> **amingv said:**
> Hello,

I have a bit of time learning C++, but I have never used "Geany" for my practices, so I cannot help you with that.
What I can help you with would be suggesting another compiler: use the GNU Compiler Collection (GCC), it comes preinstalled in many Linux distributions and works perfectly fine in my opinion. 

Pros: it won't give you any headaches while compiling and, if ever you decided to learn more than one computer language, you would have all (or most) of the tools at hand.
It has an easy interface that will take care of compiling & linking, you just need to type:
```
g++ /home/user/myprogram.cpp -o /home/user/myprogram
```

Cons: GCC is not an IDE (Integrated Development Environment), so you have to write your code somewhere else (Kate, Emacs, etc), save it as *.cpp and then compile.

Overall: a GREAT compiler, so good that I use MinGW whenever I'm forced to run Windows.

I was gonna go with GCC since that is what the book uses, and obviously I'm not ready for something with lots of options :-D. I tried downloading and installing GCC last night and after it took more than an hour to **make**, it just spit some strange error at me afterwards. So, I thought I was doing myself a favor my trying to go back to *Geany* :-P.

---

### Post by Kymus on 2007-11-04
ugh, I'm cursed..

> kymus@Shouxing:~$ g++ /home/kymus/Programing/HelloWorld.cpp -o /home/user/myprogram
g++: /home/kymus/Programing/HelloWorld.cpp: No such file or directory
g++: no input files


methinks there's again something obvious that I am missing.

---

### Post by ddrichardson on 2007-11-04
You shouldn't need to make it - sudo apt-get install g++ will do that.

An IDE is just a text editor that links into the compiler and debugger so that everything is in one place. I did wonder because I remember this book using the command line.

IDE are popular with some developers, others prefer the command line it's down to personal preference really.

---

### Post by Kymus on 2007-11-04
> **ddrichardson said:**
> You shouldn't need to make it - sudo apt-get install g++ will do that.

An IDE is just a text editor that links into the compiler and debugger so that everything is in one place. I did wonder because I remember this book using the command line.

IDE are popular with some developers, others prefer the command line it's down to personal preference really.

Thanks :-D

> kymus@Shouxing:~$ sudo apt-get install g++
[sudo] password for kymus:
Reading package lists... Done
Building dependency tree
Reading state information... Done
g++ is already the newest version.
g++ set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Apparenly last night's headache wasn't necessary :P

is there some secret to knowing what the name to use (for lack of an appropriate term) is for any program when trying to get it through the terminal? I've found that doing it through the terminal is usually the simplest option (and certainly with less errors), but sometimes I can't find things because I'm not naming them appropriately.

---

### Post by ddrichardson on 2007-11-04
If you mean installing software, then some commands point you in the right direction - g++ is one if its not installed it'll tell you what packages it's in.

As for commands, tab is your friend. This is true for all parts of the command - try typing sudo apt-get tab tab and you get a list of options. Don't forget man too - man apt-get will tell you a lot and this is true for system files as well as commands.

---

### Post by Kymus on 2007-11-04
I'm not sure what's goin on now..

I followed the previous instructions, which unfortunately ended up in error, so I turned back to the book and followed the instructions there, and I'm still getting the same error:

> kymus@Shouxing:~/Programing$ g++ HelloWorld.c++ -o file
g++: HelloWorld.c++: No such file or directory
g++: no input files


When I look at the properties of the HelloWorld file, it says it's *C Source Code*, so.. :confused:

---

### Post by amingv on 2007-11-04
> ugh, I'm cursed..
```
kymus@Shouxing:~$ g++ /home/kymus/Programing/HelloWorld.cpp -o /home/user/myprogram
g++: /home/kymus/Programing/HelloWorld.cpp: No such file or directory
g++: no input files
```
methinks there's again something obvious that I am missing.

Nah, you aren't. Here's some tips:

1. Drag and drop, that way you are less likely to make mistakes. in this case you would open your console, type g++, then drag HelloWorld.cpp drop it on the console and clic on paste. Then space type -o, space do the same again and delete the .cpp part.

2. For the sake of using the command line, name all your files and folders in lowercase, it is easy to get confused when besides remembering the path you need to remember case-patterns as well.

3. Pay attention to what you write, in the above quote you defined your output path (that's what the -o denotes) as '/home/user/myprogram' rather than '/home/kymus/Programing/HelloWorld'. This means that if your file does compile it will probably not get to the path you expected.

Also, and I forgot to mention this before, GCC recommends leaving a blank line at the end of the code, most likely it will compile if you don't, but will give you a warning. Thus, your helloworld.cpp sould look somewhat like this:

```
#include <iostream>
using namespace std;

int main() {
        cout<< "Hello, world!" <<"\n"; [COLOR="Blue"]//<-- "\n" it's a scape character for newline
                                                    //but you can use <<endl[/COLOR]
        cin.get(); [COLOR="Blue"]//<--this one it's not necesary, 
                     //it just serves as a "Press enter to continue" function.[/COLOR]

        return 0;
}
[COLOR="Blue"]//There should be an empty space here.
```[/COLOR]

---

### Post by Kymus on 2007-11-04
> **amingv said:**
> Nah, you aren't. Here's some tips:

1. Drag and drop, that way you are less likely to make mistakes. in this case you would open your console, type g++, then drag HelloWorld.cpp drop it on the console and clic on paste. Then space type -o, space do the same again and delete the .cpp part.

Here's what I did:

> kymus@Shouxing:~/Programing$ g++ '/home/kymus/Programing/HelloWorld' -o
g++: argument to '-o' missing

kymus@Shouxing:~/Programing$ g++ '/home/kymus/Programing/HelloWorld' - o
g++: o: No such file or directory
g++: -E or -x required when input is from standard input

> **amingv said:**
> 2. For the sake of using the command line, name all your files and folders in lowercase, it is easy to get confused when besides remembering the path you need to remember case-patterns as well.

Yeah, that's a good point :-D

> **amingv said:**
> 3. Pay attention to what you write, in the above quote you defined your output path (that's what the -o denotes) as '/home/user/myprogram' rather than '/home/kymus/Programing/HelloWorld'. This means that if your file does compile it will probably not get to the path you expected.

I don't mean to sound dense... but unless I missing something, I looked at my post and I read it as *'/home/kymus/Programing/HelloWorld* :-\

> **amingv said:**
> Also, and I forgot to mention this before, GCC recommends leaving a blank line at the end of the code, most likely it will compile if you don't, but will give you a warning. Thus, your helloworld.cpp sould look somewhat like this:

```
#include <iostream>
using namespace std;

int main() {
        cout<< "Hello, world!" <<"\n"; [COLOR="Blue"]//<-- "\n" it's a scape character for newline
                                                    //but you can use <<endl[/COLOR]
        cin.get(); [COLOR="Blue"]//<--this one it's not necesary, 
                     //it just serves as a "Press enter to continue" function.[/COLOR]

        return 0;
}
[COLOR="Blue"]//There should be an empty space here.
```[/COLOR][/quote]

Yeah, the book says something like that as well, afterwards. Thanks :-D

---

### Post by amingv on 2007-11-04
I'll address some more points:

First, I think you named your file "HelloWorld.c++", don't, it's not standard and it's not correct, you should name it "HelloWorld**.cpp**

Second, I think you misunderstood my first and third tips (or maybe I dind't explain myself) so I'll try and be more clear:

1. Drag and Drop: There is two "steps" on this, so that the line **should not** end in -o:
Supose your file is in /home/Kymus and it's called "hello.cpp", the compiled file you want to create will end in /home/Kymus and will be called "hello_executable". With the drag and drop technique you would do as follows:

Step 1: Write g++ in the command line and press the spacebar once, then drag the 'hello.cpp' file from your directory on top of the console and drop it, from the options you get, select "paste". By now you should have something like this:

```
g++ '/home/Kymus/hello.cpp'
```

Step 2: still in the same line press the spacebar once and type -o (note there is no space between "-" and "o"), press the spacebar again and get your "hello.cpp" file again, drag it and drop it just as you did before. Now delete the ".cpp" part and add the _executable, so that it reads "hello_executable", by now the line should read like this: 

```
g++ '/home/Kymus/hello.cpp' -o '/home/Kymus/hello_executable'
```

this should compile without problems.

3. What I meant as wrong was the part after the -o, which reads /home/user/myprogram.cpp, the part after the -o is very important because you can specify where you want the program to save the executable file.

---

### Post by Kymus on 2007-11-04
Thanks for the input **amingv**, it is much appreciated :-D

My head isn't straight tonight, so I'll try your suggestions late, tomorrow. Hopefully that will do the trick ;) (we'll see... stay tuned... ugh)

quick question though: how do I control the extension that my source code file gets? Assuming it's *.c++* now, how would I change it to *.cpp*?

---

### Post by amingv on 2007-11-04
You're welcome, as for renaming, it's quite easy:

Just click on your file, press F2 and change the .c++ for .cpp.
or from the console:

```
mv /home/hello.c++ /home/hello.cpp
```

Needless to say, read my sig.

---

### Post by Kymus on 2007-11-05
> **amingv]Needless to say, read my sig.[/QUOTE]

You don't want to tell me that said:**
> 
#include <iostream.h>
int main(); // most compilers don’t need this line
int main()
{
  cout <<“Hello World!\n”;
  return 0;
}


geary has a conniption fit when I tell it to compile.. but it sure as hell loves your code :confused:

the heck is the difference?

---

### Post by LaRoza on 2007-11-05
> **Kymus said:**
> [php]#include <iostream.h>
int main(); // most compilers don&#8217;t need this line
int main()
{
    cout <<&#8220;Hello World!\n&#8221;;
    return 0;
}[/php]

What about the namespace?

[php]
#include <iostream.h>
int main(void)
{
    std::cout << "Hello World!" << std::endl;
    return 0;
}
[/php]

---

### Post by Kymus on 2007-11-05
Hi LaRoza,

When I put in the code you supplied, it complains about the header, but otherwise, it compiles successfully in geary and I can turn it into an executable with gcc.

I'm just trying to figure out what the difference is between the codes I am being shown here, and in the book, cause it doesn't like that book too much it seems, and I ponder if I will have more headaches as I move on if I am already having a headache with the simplest code to begin with.

---

### Post by ddrichardson on 2007-11-05
There's nothing wrong with your original - I just tried it to be sure. I suspect you're not following the book (not meaning to be rude) but are jumping straight in at the hello world example. If I remember correctly this book starts off describing command line compilation and revision control system.

---

### Post by Kymus on 2007-11-05
> **ddrichardson said:**
> There's nothing wrong with your original - I just tried it to be sure. I suspect you're not following the book (not meaning to be rude) but are jumping straight in at the hello world example. If I remember correctly this book starts off describing command line compilation and revision control system.

oh boy... I'll go back and check. I made sure to not jump ahead this time :-D

---

### Post by amingv on 2007-11-05
> Though now I am confused. When I input the code from the book


```
#include <iostream.h>
int main(); // most compilers don’t need this line
int main()
{
cout <<“Hello World!\n”;
return 0;
}
```
geary has a conniption fit when I tell it to compile.. but it sure as hell loves your code

the heck is the difference?

Your book actually gave you this code? Are you sure? If it is so then I suggest you RUN to your bookstore and get your money back. Here's why:

```
#include <iostream.h> [COLOR="Blue"]/*`<--Yes, this was correct some time
ago, but now most headers must be included without the .h extension. This was done
to remove some compatibility issues with different OS. You should use
#include <iostream> unless you are using some OLD compiler (with GCC, this is
not the case)*/[/COLOR]
```

```
using namespace std; [COLOR="Blue"]/*If you wish to use the cout command,
you need to specify this. This defines the "place" where cout has ben declared.
You may skip this and use std::cout, but I do not recommend it because it's very likely
you'll make mistakes*/[/COLOR]
```

```
int main(); // most compilers don’t need this line
int main()[COLOR="Blue"] /*<--Here you have declared the main function twice. This is
completely wrong. You must only have ONE main function per program. This function is
**very** important since it's the function your OS calls for execution, so all compilers
DO need this line, but not twice. And you may not call the main function yourself, that is
illegal. The correct way to do it is:

int main () { //Note there is no semicolon after the parenthesis
        //insert your code here
}*/
[/COLOR] 
```

Overall, the above code when corrected should look like this:

```

#include <iostream>

using namespace std; [COLOR="Blue"]//<--Here you need the semicolon[/COLOR]

int main() {
        cout<< "Hello, World\n";
        return 0;
}
```

Another suggestion: use indentation to make your code more readable. In the
above example, you will notice that "cout" and "return" are one tab space apart from
the margin; that helps us identify it as a **block** of code that belongs to the main
function, and helps us establish the hierarchy of the program.

Hope all this is helpful. -Regards

---

### Post by Kymus on 2007-11-06
> **amingv said:**
> Your book actually gave you this code? Are you sure? If it is so then I suggest you RUN to your bookstore and get your money back.

see what I see:

[[IMG]http://img462.imageshack.us/img462/2564/screenshotof5.th.png[/IMG]](http://img462.imageshack.us/my.php?image=screenshotof5.png)

Thanks for the detailed explanation of the code; I'll look over that tomorrow :)

---

### Post by ddrichardson on 2007-11-06
> **amingv said:**
> Your book actually gave you this code? Are you sure? If it is so then I suggest you RUN to your bookstore and get your money back.Mate, it doesn't surprise me - the book is really old, I had it as part of a set the came with one of the Redhat versions before it became commercial.

---

### Post by Kymus on 2007-11-06
> **ddrichardson said:**
> Mate, it doesn't surprise me - the book is really old, I had it as part of a set the came with one of the Redhat versions before it became commercial.

Mayhaps I should find a new book... :-D

I got that one through bittorrent anyway :P. I'll have to see if I can dig up a better "C++ in Linux" book.

---

### Post by ddrichardson on 2007-11-06
> **Kymus said:**
> Mayhaps I should find a new book... :-D

I got that one through bittorrent anyway :P. I'll have to see if I can dig up a better "C++ in Linux" book.La la la I'm not listening copyright laws la la la ;-)

To be honest, if you're really interested in C++ then you need not worry too much about books being Linux specific - any book by Soustrup or Shildt is a good place to start. It's probably a little out of date but Shildt's C++ Nuts and Bolts got me through first year at university. Mind you that was 1995.

---

### Post by Kymus on 2007-11-06
> **ddrichardson said:**
> La la la I'm not listening copyright laws la la la ;-)

To be honest, if you're really interested in C++ then you need not worry too much about books being Linux specific - any book by Soustrup or Shildt is a good place to start. It's probably a little out of date but Shildt's C++ Nuts and Bolts got me through first year at university. Mind you that was 1995.

It's not stealing, it's only borrowing :-D. Besides, did you see that recent report about P2P downloaders buying more music? :P

I was looking at Linux specific books since the only other C++ books I've seen deal with MS Visual Studio and I look at that and I'm all :confused::confused:. Of course I could get Visual Studio to run, but obviously my main focus is to avoid MS software all together.

I'm interested in C++ for 3 reasons:
[LIST=1]
[*]so I can follow along [this]("http://www.amazon.com/Hacking-Art-Exploitation-Jon-Erickson/dp/1593271441/ref=pd_bbs_sr_1/104-4151456-2965519?ie=UTF8&s=books&qid=1194357946&sr=8-1") book and understand the code examples
[*]ability to understand and work with open source software in Linux
[*]maybe (maybe) make a god aweful game that gets nowhere (or more likely, the ability to tinker with already open source games ;P)
[/LIST]

I figured that trying to work along with a book that dealt specifically with C++ in Linux would help me both as a Linux noob and a programming noob. I'll look for those books you suggested though, thanks :D

---

### Post by amingv on 2007-11-06
If you are looking for a C++ tutorial to get you started then try [this]("http://www.cprogramming.com/tutorial.html#c++tutorial"). It has all the basic information and is up to date, but it is a webpage, which means it would be difficult to download it.

Also, never mind if you are learning C++ for windows or linux. There is no such thing as MS++ or TUX++. C++ it's a very **portable** language and most of the code you write for windows will work for linux with no or minimal changes, and vice-versa.
Of course, some applications can be made specifically designed for windows or specifically designed for linux, but if you want to work open source (The same reason that motivated me:)) This will most likely not be the case.

---

### Post by Kymus on 2007-11-06
> **amingv said:**
> If you are looking for a C++ tutorial to get you started then try [this]("http://www.cprogramming.com/tutorial.html#c++tutorial"). It has all the basic information and is up to date, but it is a webpage, which means it would be difficult to download it.

Also, never mind if you are learning C++ for windows or linux. There is no such thing as MS++ or TUX++. C++ it's a very **portable** language and most of the code you write for windows will work for linux with no or minimal changes, and vice-versa.
Of course, some applications can be made specifically designed for windows or specifically designed for linux, but if you want to work open source (The same reason that motivated me:)) This will most likely not be the case.

It looks like it will do the trick, thanks :-D

---

