---
title: "Problem With 'make' Command In Terminal"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by TheWiseNoob on 2007-05-31
Well, I finally decided I wanted to begin learning C++ yesterday and I've had a few difficulties, though all have been solved, until now. 

I'm using GTK for creating my GUI and it seems that it won't be to hard to learn how to use.  While a lot of the code seems confusing, I know it will come easy as time goes by. 

I'm having difficulties when using the 'make' command in terminal. The name of my makefile is 'Makefile.am'. The problem I'm having is when I type 'make' in terminal( after changing the directory to the folder with the C++ source and makefile) the response I get is:

```
make: Nothing to be done for `Makefile.am'.
```


I tried a few more times but with no success. So I google how to chose a makefile with a name other than 'Makefile.ma'. I found the code

```
make -f <NAME OF MAKEFILE>
```

should make that possible. So I type 

```
make -f Makefile.am
```

and the output is:

```
makefile.am:1: /examples/Makefile.am_fragment: No such file or directory
make: *** No rule to make target `/examples/Makefile.am_fragment'.  Stop.
```

I have no idea what this means except that obviously I don't have a folder called examples with another makefile in it.....

Here is a link the tutorial I'm using to learn how to use gtkmm for creating a GUI:
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch04.html#sec-Pushbuttons]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch04.html#sec-Pushbuttons")

And here is a link to the source files, including the makefile I'm using.
[http://www.gtkmm.org/docs/gtkmm-2.4/examples/book/buttons/button/]("http://www.gtkmm.org/docs/gtkmm-2.4/examples/book/buttons/button/")


I hope the mistake I'm making is an obvious and one of you can give me a simple solution....or a not so simple solution that still works.

---

### Post by Cypher on 2007-06-01
The "Makefile.am" is an input to the "automake" program which will generate a "Makefine.in" file that is an input to "configure" that will create the final "Makefile" that you can "make" on..

---

