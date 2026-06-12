---
title: "Ubuntu newbie requesting programming help"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by snappyjack on 2007-08-15
Hey, I know just barely enough Linux to function; Ubuntu is my first crack at the operating system and I'm just feeling my way along with all the tutorials and FAQS I can find.

Anyway, I've been learning C++ and Perl. Now that I have Linux, I don't know how to find a C++ compiler or run Perl. 

I KNOW I have perl somewhere in here already, but how to I get it to run? I've been trying to install Cpan bundles, but i don't really know what I'm doing. I just go and DL the files that the terminal says to, but i can't even get past Bundle::CPAN. What bundles do i need, and how do I get them?

And for C++, how do i get a compiler? Ive tried downloading compilers that say theyre for linux, but then what is the next step? What do i type in the terminal to get it to "go"?

On a side note, that seems to be an ocurring problem. I download a program i know i want, but what's the next step? How do I get it out of the folder it comes in and running? The only things ive sucessfully downloaded are the ones already under add/remove programs.

Thanks alot.

---

### Post by ErusGuleilmus on 2007-08-15
Couldnt you use Anjuta form add/remove programs?

---

### Post by Max Luebbe on 2007-08-15
Easy!

to get all you need for C/C++ development do the following:

Open up a terminal

type:
```
sudo apt-get install build-essential
```

then enter your admin password

The GNU C/C++ compiler will then be installed (gcc)

To test out if you have perl, try something in your terminal called tab-expansion

type the letters : per 
and then hit tab twice, which will produce a list of all the commands in your current path that start with those letters

perl should be in there. if not:
```
sudo apt-get install perl
```

If I were you, I'd take a look at Python which is the Ubuntu Lingua Franca and a great language for somebody just getting their feet wet. Comes with Ubuntu by default, and there is tons of free documentation over at python.org

Hope this helps

---

### Post by Paul820 on 2007-08-15
In the terminal type
> sudo apt-get install build-essential
This will install all the tools needed to compile c and c++ programs. Perl, i don't know, never used it.

---

### Post by snappyjack on 2007-08-15
thanks alot guys. 

I was really impressed with how fast i got a response here. Most times i post on a "newbs only" forum for anything and i need to wait days. Glad to see these forums are populated by friendly/helpful people.

---

### Post by snappyjack on 2007-08-15
sorry, one more question (remember im a super noob)

Ok, i downloaded the build-essential. I also have gcc in my bin.

But what do i DO to actually run the compiler?

The same with perl, what do i DO to actually make it pop up?

---

### Post by meatpan on 2007-08-15
> **snappyjack said:**
> 
But what do i DO to actually run the compiler?


Give this a try:
o Open a terminal (gnome-terminal, from your program list), and type 'gcc --version'.  Verify the command works by looking at the output
o Run 'gcc --help' to see a brief synopsis of how to run the compiler.  You should see something            like:  
```

Usage: gcc [options] file...
Options:

```
o Open up your favorite editor and write a short program.  Pass the program file as an arg to gcc.

---

### Post by snappyjack on 2007-08-15
how exactly to i pass the file as an arg? Do i just do one of the commands listed in --help? Because when i try, it reads gcc: no input files.

---

### Post by p_quarles on 2007-08-15
What are you attempting to compile? 

Most legitimate source-based applications come with a "readme" file with installation instructions.

---

### Post by snappyjack on 2007-08-15
well i just was trying something stupid to start off to see if i could compile anything in the first place; just something that returns text "This works".

It keps saying the file format is not recognized. I'm just using the default text editor, is there a specific format it wants? If there is, how do i make the text i wish to compile into that?

---

### Post by p_quarles on 2007-08-15
> **snappyjack said:**
> well i just was trying something stupid to start off to see if i could compile anything in the first place; just something that returns text "This works".

It keps saying the file format is not recognized. I'm just using the default text editor, is there a specific format it wants? If there is, how do i make the text i wish to compile into that?
Okay, I don't program in C or C++ (just a little bit of PHP and Python) at all, and I'm kind of guessing that you don't either. The binary compilers for Linux definitely work, so the best way to figure out how to do it is to get the source code for an application you want to install, and then follow the instructions that come with the package. 

You said you're new to Linux. My advice is to take it more slowly. Figure out the basics of the system before you start trying to make binaries from source.

---

### Post by snappyjack on 2007-08-15
you're right, i don't know how. But thats why i wanted this compiler, so i can play around and figure it out. I'm not claiming to be a wiz at it and that's why i visited this board. 

Is it actually really difficult to compile simple codes? If so, i'll stay away from it. But i wouldn't think it so difficult that even a new user shouldn't be able to create and compile simple files.

---

### Post by p_quarles on 2007-08-15
No, it's no difficult to compile codes, and like I said there are usually instructions that come with the programs. The difficult part is writing the code, which (from what I can tell) is what you're trying to do. 

I mean, I absolutely encourage you to do that, too. But I think the first step is to get a book (there are many online) about writing in C++, and start there. 

Compiling is a lot simpler, but you have to have something to compile first. :)

---

### Post by Bushfire on 2007-08-15
GCC is the Gnu Compiler Collection, and it comes with various front ends for various languages.

g++ is the C++ front end, so write:

```

$ g++ hello.cpp -o  hello
# then run
$ ./hello
This works
$

```

```

# Various helpful flags
g++ -o # the name of the output file
g++ -c # stop before linking.
g++ -S # stop before assembling
g++ -g # compile with debugging info

```

---

### Post by snappyjack on 2007-08-15
i have 
//simple program
#include <isotream>
#include <cstdio>
#include <cstdlib>

using namespace std;

int main()
{

int good=5;
cout << "The value of int good is" << good;

system("PAUSE");
return 0;
}

saved in text editor as whatever the default filetype is.

Can anyone see what's wrong?

---

### Post by Bushfire on 2007-08-15
> **snappyjack said:**
> i have 
//simple program
**#include <isotream>**
#include <cstdio> // Not needed
#include <cstdlib>

using namespace std;

int main()
{

int good=5;
cout << "The value of int good is" << good;
[B]
system("PAUSE");  [/B] // This isn't windows. Take this line out.
return 0;
}

saved in text editor as whatever the default filetype is.

Can anyone see what's wrong?

Helpful?

---

### Post by snappyjack on 2007-08-15
Thanks brushfire!

I guess i had no idea about the g++ front emd...

whne i entered gcc --help i got the message
"gcc [option] file..."

so i assumed to compile something, I would just need to find an option that translated as a "compile" of sorts. so i kept entering gcc [some option] myfile.cpp, to no avail. 

...not to menton my stupid typo (i attribute it to haste and frustration), and my windows mindset with pause.
Thanks!

---

