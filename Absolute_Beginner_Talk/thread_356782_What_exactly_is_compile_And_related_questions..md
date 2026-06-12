---
title: "What exactly is compile? And related questions."
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by hito1 on 2007-02-08
Lot of newbie questions:

1. What exactly is compiling an app to install it?

2. How is it different from installing through synaptic?

3. How is an app installed through compilation handled by Ubuntu? Does it get updated by the update-manager? Does it stays in the same folder as synaptic installed applications?

4. If I install something through synaptic, can I install a later version of it through compiling? Will they both exist in the system? Will they conflict? For instance, I installed fluxbox 0.9.something through aptitude, there is a new version on the fluxbox page, can I compile and install it, or will I mess up things?

5. Is a .deb package made for Ubuntu the same one as made for Debian?

6. What is the linux equivalent for "C:\Program Files"?

7. If I get a source code for an application, how do I read it? I mean, do we get to see its code? (I have no experience in this, I just wanted to see how a program looks like in its inside - sort of an anatomy experiment :) )

8. What does the 'make' command do?

Thanks. :)

---

### Post by meng on 2007-02-08
1. Compile means you install the program from its source code (programming code).
2. When you install through Synaptic, you (generally) download and install software that's already been compiled for you.
3. You have to update compiled software yourself.
4. If you're a newbie, start off with accepting what is in the repositories, even slightly older versions of software work well for most users.
5. No. They may be compatible, but don't count on it.
6. No strict equivalent. A lot of programs are installed within /usr.
7. Source code is just a plain text file. I don't mean that it has a .txt extension.
8. It's part of the process of compiling from source.

---

### Post by pay on 2007-02-08
Compiling is the process of turning code into program. Here, let's have some fun```
sudo aptitude install build-essential checkinstall
sudo apt-get build-dep gaim
wget http://puzzle.dl.sourceforge.net/sourceforge/gaim/gaim-2.0.0beta6.tar.bz2
tar jxvf gaim-2.0.0beta6.tar.bz2
cd gaim*
./configure --help
./configure #and if you want to add some options
make
sudo make install # or sudo checkinstall if you want a debian file
```

---

### Post by hito1 on 2007-02-08
> **meng said:**
> 1. Compile means you install the program from its source code (programming code).
2. When you install through Synaptic, you (generally) download and install software that's already been compiled for you.
3. You have to update compiled software yourself.
4. If you're a newbie, start off with accepting what is in the repositories, even slightly older versions of software work well for most users.
5. No. They may be compatible, but don't count on it.
6. No strict equivalent. A lot of programs are installed within /usr.
7. Source code is just a plain text file. I don't mean that it has a .txt extension.
8. It's part of the process of compiling from source.

Thanks for the quick answers. I'd like to ask further questions, if I may:

1, 2, 7, 8. If the source code is a text file, what does compilation do with this text (in layman terms)?

3. How is that done?


And a new one, what is a binary file? (in layman terms, please :) )

Thanks. :)

---

### Post by smartalecks on 2007-02-08
Compiling is the process that turns source code into an application/program.

some langs, such as python, are interpreted languages and do not need to be compiled.
others, like c, c++, need to be compiled.

---

### Post by hito1 on 2007-02-08
Ah, and a new one, how to uninstall an application compiled from source?

(please, have patience :) )

Thanks! :)

---

### Post by pay on 2007-02-08
cd to where the program is and type```
sudo make uninstall
```

---

### Post by IYY on 2007-02-08
> 1, 2, 7, 8. If the source code is a text file, what does compilation do with this text (in layman terms)?

3. How is that done?


And a new one, what is a binary file? (in layman terms, please )

My favorite analogy is to baking a cake. The program text (code) is like a recipe for baking the cake: it tells you the exact instructions on how to bake the cake, and gives you the ingredients, but by itself it can't be eaten. Compiling the code is the act of baking the cake. The finished cake is the binary file: it is ready for use (in this case, eating) but no longer contains the exact information of how to bake it. 

A more technical explanation is not so much in layman terms, but it is detailed enough to give you the big picture:

Program code is readable by humans, and looks like this (just an example):

```
int x = 5;
int y = 3;
int z = x + y;
for (int i = 0; i < x; i++)
{
   printf("hello!");
}

```

This code doesn't do anything interesting at all. It adds up 5 and 3, and then for no particular reason writes "hello" on the screen 5 times.

While this code may appear to be computer code, it is not. It is intended only for humans, and computers cannot understand it. The compiler translates the code into something like this:

```
101000101001001001010101000111001001010101011100
010100011100101000010101000010101010010010010100
101010010100100010100101110010101010010100010100
010110101010010111001010100010101001010110100101
101010001010010010100010010101010101110101010010
101001010111001001010001010000101001010100101011
```

Some of these binary values can represent pictures, others can represent numbers, and others can represent instructions of what to do with the data. The computer executes these basic instructions line by line, using very basic hardware operations (it's basically a calculator with memory at this stage). Note that a line of binary code does have to represent a single line of program text. Depending on the context, a line like 

```
int z = x + y;
```

could be translated by the compiler to

```
add the contents of registers x and y, and place the result in register z
```

or (more commonly, because compilers tend to be stupid)

```

Grab an integer value from memory at address x, put it in register 1.
Grab an integer value from memory at address y, put it in register 2.
Add the contents of registers 1 and 2, and place the result in register 3.
Allocate space in memory for an integer number.
Move the contents of register 3 to this location.

```

You can see why programmers prefer to write their programs in a high-level language as opposed to machine language, and why it's as difficult to figure out what the compiled program does as it is to figure out the exact recipe of an already baked cake.

Note that while the program code shown at the top could be written in any programming language, the resulting machine code (1's and 0's) doesn't "know" what language it was originally written in, but can only run on a system similar to that for which it was compiled. Your cellphone doesn't understand the same 1's and 0's as your PC at home, and your Windows machine doesn't understand the same 1's and 0's as your Linux machine.

---

### Post by hito1 on 2007-02-08
> **IYY said:**
> My favorite analogy is to baking a cake. The program text (code) is like a recipe for baking the cake: it tells you the exact instructions on how to bake the cake, and gives you the ingredients, but by itself it can't be eaten. Compiling the code is the act of baking the cake. The finished cake is the binary file: it is ready for use (in this case, eating) but no longer contains the exact information of how to bake it. 

A more technical explanation is not so much in layman terms, but it is detailed enough to give you the big picture:

Program code is readable by humans, and looks like this (just an example):

```
int x = 5;
int y = 3;
int z = x + y;
for (int i = 0; i < x; i++)
{
   printf("hello!");
}

```

This code doesn't do anything interesting at all. It adds up 5 and 3, and then for no particular reason writes "hello" on the screen 5 times.

While this code may appear to be computer code, it is not. It is intended only for humans, and computers cannot understand it. The compiler translates the code into something like this:

```
101000101001001001010101000111001001010101011100
010100011100101000010101000010101010010010010100
101010010100100010100101110010101010010100010100
010110101010010111001010100010101001010110100101
101010001010010010100010010101010101110101010010
101001010111001001010001010000101001010100101011
```

Some of these binary values can represent pictures, others can represent numbers, and others can represent instructions of what to do with the data. The computer executes these basic instructions line by line, using very basic hardware operations (it's basically a calculator with memory at this stage). Note that a line of binary code does have to represent a single line of program text. Depending on the context, a line like 

```
int z = x + y;
```

could be translated by the compiler to

```
add the contents of registers x and y, and place the result in register z
```

or (more commonly, because compilers tend to be stupid)

```

Grab an integer value from memory at address x, put it in register 1.
Grab an integer value from memory at address y, put it in register 2.
Add the contents of registers 1 and 2, and place the result in register 3.
Allocate space in memory for an integer number.
Move the contents of register 3 to this location.

```

You can see why programmers prefer to write their programs in a high-level language as opposed to machine language, and why it's as difficult to figure out what the compiled program does as it is to figure out the exact recipe of an already baked cake.

Note that while the program code shown at the top could be written in any programming language, the resulting machine code (1's and 0's) doesn't "know" what language it was originally written in, but can only run on a system similar to that for which it was compiled. Your cellphone doesn't understand the same 1's and 0's as your PC at home, and your Windows machine doesn't understand the same 1's and 0's as your Linux machine.

Wow! Big thank you, that's what I was looking for :D. So, if I understood it correctly, a binary file is one already compiled?

Two more questions, the last ones, I think/hope: 

1. Why there are dependencies when compiling a program? 

2. Totally unrelated, but what is a daemon?

Thanks. :)

---

### Post by IYY on 2007-02-08
> Wow! Big thank you, that's what I was looking for . So, if I understood it correctly, a binary file is one already compiled?

That's right.

> 1. Why there are dependencies when compiling a program?


In order to save disk space, and allow greater consistency, most Linux applications don't come with all of the code required for their operation, but rather refer to external code that should already be on your system. This external code can be shared between several applications: for example, both Gaim and Gimp (and most other applications in Ubuntu) use the GTK2 toolkit for the graphical user interface (all the buttons, menus, textboxes and such). It's possible for both Gaim and Gimp to come with their own versions of GTK2, but it's easier to just share an existing library. 

It's just like if you are submitting a philosophy essay in College: you make references to other books and papers, but don't attach a copy of each one. You assume that the professor has access to all of these books. 

If it wasn't for these dependencies, downloading and installing a program from the repositories would take much much longer (as long as it takes to download and install a program in Windows, for example).

> 2. Totally unrelated, but what is a daemon?

A program that runs in the background, rather than under the direct control of a user. Many daemon programs run on your system, doing various tasks, without you having to worry about them. 

[http://en.wikipedia.org/wiki/Daemon_(computer_software](http://en.wikipedia.org/wiki/Daemon_(computer_software))

---

### Post by hito1 on 2007-02-08
Thanks a lot, IYY! :)

---

### Post by ZxEfR on 2007-03-03
IYY....

I just had to tell you thank you for your correct and full answer (even though it's not my question).

If all the questions (within reason) could be answered the way you have answered this mans question...with interest, enthusiasm, fully detailed and correctly.....I believe Linux would be twice as far along as it is and far more popular.....so thanks so much   :KS :KS :KS :KS :KS

---

