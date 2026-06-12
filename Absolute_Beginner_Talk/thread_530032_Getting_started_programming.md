---
title: "Getting started programming"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by RTrev on 2007-08-20
Okay, I think it's time to begin programming in Linux, but the last time I wrote any C code was under DOS (before the term Distributed Denial of Service had been coined.)

I wasn't bad with C, so I thought I'd try a hello world.. and ran into an immediate problem.  Of the almost 20,000 .h header files on the system, stdio.h wasn't one of them.

Not off to a good start here.

Anyone have suggestions?  Perhaps a good link to getting started?  Or perhaps suggestions of other languages which might be a better place to be?

I generally like to write small utility programs, although having easy gui capabilities would probably be nice.  My main concern is that I'd like my code to be as portable as possible.

I'm thinking here that I want to write things which will run under KDE or Gnome or Flux or whatever, and that can be easily re-compiled for most other Linux systems.

I normally use Gedit for HTML and PHP code, but am open to suggestions for an editor which might make coding a bit quicker or more efficient for edit/compile/link/test cycles.

Thanks in advance
Bob

---

### Post by Jimmyfj on 2007-08-20
Since you are willing to "start over" you could try out Python or Perl. Both are easy to ajust to when familiar with C

---

### Post by RTrev on 2007-08-20
> **Jimmyfj said:**
> Since you are willing to "start over" you could try out Python or Perl. Both are easy to ajust to when familiar with C

Thanks!  I've heard good things about both.  I'll do a little searching, as there must be discussions of the relative merits of each somewhere.

Bob

---

### Post by daveshields on 2007-08-20
You say you have some experience in C and want to learn more about Linux. Here a couple of possibilities:

Find the code for "busybox," an implementation in C of many commonly-used Linux primitives.See if you can follow the code. The busybox web site has the CVS tree on display to you can take a peek If "cvs" is new to you then you can learn about that , "gcc," "gbd" and all the other key tools in the Linux "land of C." If you are still interested, try to add some minor changes. For example, add a "move" command that does the same thing as the "mv" command. 

Get a book about PHP. It's a key language behind the idea of "dynamic" web content. Its design is based on that of C, though it has a *large* library. See if can you write a web page that prints the squares of the first 10 integers, not by entering a table but by writing a PHP code snippet that computes them. Then see if you can ask the user to enter how many integers and so forth.

---

### Post by RTrev on 2007-08-20
> **daveshields said:**
> You say you have some experience in C and want to learn more about Linux. Here a couple of possibilities:

Find the code for "busybox," an implementation in C of many commonly-used Linux primitives.See if you can follow the code. The busybox web site has the CVS tree on display to you can take a peek If "cvs" is new to you then you can learn about that , "gcc," "gbd" and all the other key tools in the Linux "land of C." If you are still interested, try to add some minor changes. For example, add a "move" command that does the same thing as the "mv" command. 

Sounds good,, thanks.  I there any general consensus about C versus something like Python or Perl in terms of speed, size, and so on?  I don't want to get in the middle and decided I made the wrong choice.  :-s

> Get a book about PHP. It's a key language behind the idea of "dynamic" web content. Its design is based on that of C, though it has a *large* library. See if can you write a web page that prints the squares of the first 10 integers, not by entering a table but by writing a PHP code snippet that computes them. Then see if you can ask the user to enter how many integers and so forth.

I think I worded my post poorly.  What I was intending to convey was that I now write HTML and PHP code, using the Gedit editor.  I was wondering if there might be an editor which would is especially recommended for C or Python or whatever I end up with.  Maybe one which just has a button to compile/link, etc.  No biggy.. Gedit is fine. I have the PHP down reasonably well, and have functional pages which work fine.  I'm wanting to write something other than just web pages at this point.  Sorry for the confusion, and thanks again!

---

