---
title: "Writting apps for Linux...What Language?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Greg Mueller on 2008-04-10
I know this is a real simplistic question, but I'd like to find out about how to write simple apps for linux (ubuntu).
Can someone suggest a book?
Is there an app which lets you "build an app" graphically? (Like a webpage)

Nothing fancy, just simple little apps like sending a file through a serial port etc.

I used to write in Basic in the DOS days, then later Quick Basic. Then came windoz and that was the end of it

---

### Post by R6V2 on 2008-04-10
Check Out

AutoItScript.com free software. This simple language is used to automate programs or make GUI's. *Note* Doesn't work on Linux. It is a windows app, you must use something like Wine.

---

### Post by Greg Mueller on 2008-04-10
That looks great....
If only it were for Linux

I really want to move my internet operations over to Linux full time. Right now I use two computers (one windoz, one Linux) so I can do all the things I need to do.

One of the things is to be able to upload files over a serial port. I have to do it on the windoz machine still. 

A more ambitious thing is a substitute for MailWasher. I just don't want to pay (full price) for a half finished Linux version, which is discontinued with no support.

I've tried Wine and although some things work (after a fashion) I guess I'd rather just leave windows behind

---

### Post by apostate on 2008-04-11
There are lots of good programming IDE (Integrated Development Envronment) apps out there. Anjuta for one.

I think it supports C, C++, Python and a few other languages.

You could also look at Gambas. If you use Kubuntu, try KDevelop.

---

### Post by scramasax on 2008-04-11
> **Greg Mueller said:**
> I know this is a real simplistic question, but I'd like to find out about how to write simple apps for linux (ubuntu).

You'd use a cross-platfrom toolkit rather than something specifically to do with the OS.  The GNOME desktop is what you see on Ubuntu.  (Linux is the OS kernel.)  GNOME is built around [GTK+](http://en.wikipedia.org/wiki/GTK), which is based on C.  The toolkit KDE uses is [Qt](http://en.wikipedia.org/wiki/Qt_toolkit),  which, by contrast uses C++.  But both have bindings for other languages.  There is an interesting article on GNOME's future directions here:

[http://arstechnica.com/articles/culture/reinventing-gtk.ars](http://arstechnica.com/articles/culture/reinventing-gtk.ars)


Anyway, you'd probably want to use a higher-level language at least at first -- Python, perhaps.

[https://help.ubuntu.com/community/PythonRecipes](https://help.ubuntu.com/community/PythonRecipes)

---

### Post by Greg Mueller on 2008-04-11
Great advice.
 Thanks!

---

### Post by pedro_orange on 2008-04-11
You should check out the stickies in the Programming Talk forum.

This question has been asked loads, and there are loads of great links to books/IDEs and everything you need to get started.

---

### Post by 3rdalbum on 2008-04-11
I use Pythoncard to write small graphical applications. Unfortunately it seems to be unmaintained and the IDE (resourceEditor) is buggy as hell... but it's easy to use.

---

### Post by scorp123 on 2008-04-11
> **Greg Mueller said:**
>  I used to write in Basic in the DOS days, then later Quick Basic. Then came windoz and that was the end of it For really simple things: Shell scripts. But other than that you might be interested in **Python** I guess ...

---

