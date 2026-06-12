---
title: "trying to learn the terminal... help me copy files"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by olivesmarch4th on 2006-07-13
Hello!  I'm new to Linux, I've been reading "Beginning Ubuntu Linux" by Keir Thomas and it's been quite helpful so far, but it doesn't provide particularly detailed information about the command line.

I'm trying to learn how to use the Terminal.  I'd like to reach the point where I can do virtually anything with it, but I have to start with the basics.

I've learned ls, that works.

I'm just trying to use the basic command to copy a single file, purely for practicing purposes.

The file in question is on my Desktop, it's called Screenshot.png

I can find the file easily through 'ls' or 'locate' commands, but I can't succeed in copying it.

I've tried 'cp Screenshot.png /home/olivesmarch4th/writing'
 
and 'cp Screenshot.png /home/olivesmarch4th/writing/

and I've tried the Screenshot without the .png, and every time I get the response, "cannot stat 'Screenshot'; no such file or directory"

What am I missing here?

Hopefully this will be easy to answer!

Olives,
Christy

---

### Post by Brunellus on 2006-07-13
The Desktop you see in GNOME/KDE reads the contents of 

/home/olivesmarch/Desktop

But when you open up a terminal, the first working directory is always your home directory--

/home/olivesmarch


so the command is

cp /home/olivesmarch/Desktop/Screenshot.png /path/to/destination

and that will copy.  If you want to *move* it, replace cp with mv.

If you ever get 'lost' and can't remember what directory you're in (happens sometimes) type

pwd

which prints the directory you're working in.

Keep at it, and you'll love the shell!

---

### Post by CrustyDOD on 2006-07-13
Or simply go to Desktop folder (cd Desktop) and use
cp your_file.png /dest/path/filename.png

Using TAB key (auto-complete) is also very usefull, try it, it helps a lot.. In case you haven't seen that :)

---

### Post by Brunellus on 2006-07-13
> **CrustyDOD said:**
> Or simply go to Desktop folder (cd Desktop) and use
cp your_file.png /dest/path/filename.png

Using TAB key (auto-complete) is also very usefull, try it, it helps a lot.. In case you haven't seen that :)
well, yes.  

I learned the expanded form of the commands first, though, so I could get a sense of what they were actually doing.....

---

### Post by olivesmarch4th on 2006-07-13
Woohoo!!!  Thanks, guys!  That worked perfectly.  Now I can copy, move, delete and rename files through the BASH.


:)


Olives,
Christy

---

