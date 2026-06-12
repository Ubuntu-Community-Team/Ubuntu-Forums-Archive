---
title: "2 quick questions"
date: 2005-08-24
forum: Absolute Beginner Talk
---

### Post by scottjack on 2005-08-24
I searched, and could not find anything appropriate to what I am looking for so here goes.

1: I am running a toshiba laptop that does have an internal thermometer somewhere (it works, i used to have motherboard monitor)

Is there any way I can setup a program to perform a similar function? GDesklets does not work for me when I try and setup a system temperature reading.

2: I am looking for a C++ compiler to use for school, and am wondering what you guys would reccomend for myself. I do know how to use g++ on red hat, and Dev c++ on windows. What one would you reccomend.

For both how would I go about installing your suggestions as well... I know virutally NOTHING about how to use the terminal besides how to copy and paste.

Thank you for your time. I love this operating system, and am glad I made the switch from xp.

---

### Post by Stormy Eyes on 2005-08-24
You should be able to use g++ in Ubuntu. Type **sudo apt-get install build-essential** into a terminal. You'll be prompted for your password. Enter it, and be patient. :)

---

### Post by scottjack on 2005-08-24
Ok, I did that, and I take it that I have a copy of g++, but how would I go about opening it? I cannot find it in the applications toolbar.

also: any ideas for the system temperature readout?

thank you very much for your time

---

### Post by Nequeo on 2005-08-24
[QUOTE=scottjack]Ok, I did that, and I take it that I have a copy of g++, but how would I go about opening it? I cannot find it in the applications toolbar.

also: any ideas for the system temperature readout?

thank you very much for your time[/QUOTE]
 G++ works from the command-line. For detailed (possibly too detailed!) information about how to use it, type
```

man g++

```
on the command-line.

For compiling simple programs, (e.g. only one .cpp and .h file) you can use it as follows...

```

g++ simple_program.cpp -o simple_program.exe

```
This tells it to compile and link simple_program.cpp and output the result as 'simple_program.exe'. If you forget to provide '-o', the program will be compiled as 'a.out', which you can then rename to whatever you want.

As for the temperature thing... You could look into the package 'lmsensors'. (As in 'L' for Lewis, not a capital 'i'). I've never really got it working, though. You might want to look into Gdesklets, too. There's a thread in this forum about it... which I can't find. 

[EDIT] Sorry, just re-read your post and noticed you've already tried Gdesklets. In that case, did you install 'Gdesklets-data' as well? I've heard that it's broken. Instead, you should use Google to find the Gdesklets home-page, and download the individual desklets you want, then use the 'install' function of the gdesklets program to add them. You might have better luck that way. [/EDIT]

Cheers,

---

### Post by cwaldbieser on 2005-08-24
[QUOTE=scottjack]Ok, I did that, and I take it that I have a copy of g++, but how would I go about opening it? I cannot find it in the applications toolbar.

also: any ideas for the system temperature readout?

thank you very much for your time[/QUOTE]
g++ is a command line utility.  You just edit your files in any editor you like (I like kate in KDE or nano in the terminal).  Then to compile, you just do something like:
```
$ g++ myprog.cpp
```
If it works, there will be no output, but a program called "a.out" will appear in the directory.  You can run it with
```
$ ./a.out
```
If there are errors, they will start to spew accross the screen.  It is sometimes best to redirect them to a file or pipe them to a pager.  E.g.
```
$ g++ myprog.cpp 2> errors.txt
```

---

