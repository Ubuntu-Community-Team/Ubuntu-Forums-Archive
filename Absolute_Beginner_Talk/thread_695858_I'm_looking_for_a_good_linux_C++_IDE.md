---
title: "I'm looking for a good linux C++ IDE"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Chronotrigger_BG on 2008-02-13
Hello

I wish to apologize in advance in case this thread has been published(over and over) before. What I found on the forum didn't answer my question.

I want to get a good ubuntu IDE that looks and feels like either RHIDE or Dev-C++.
Now, I know that both RHIDE and Dev-Cpp are supposed to have Linux versions.
At least so I read.
I've used Rhide for a long time in the past, so imagine my discontent when, after trying several different ways to install it, every time it either didn't run at all (makefile problems, mostly) or it ran, but didn't have some really basic features working like 'user screen' (alt+f5) working properly. Also, the libraries it depends are no longer supported...it's a pain.

I tried some things like Anjuta and CodeWarrior but didn't really like them.
They seemed all too complicated and still lacked some basic stuff like "compile" and "run" buttons. Or they had, but they didn't do what they were supposed to do. Asking me for configuration files for the HWolrd program isn't exactly what I call a good IDE.
Perhaps I just didn't understand properly what to do, but they seemed too complicated for my purposes.


So, please send me suggestions about an IDE, which satisfies the following conditions:
It should be lightweight (like Rhide), and simplistic, it's ok if it's console only.
It should be possible to have a compiled Hello World program in C++ within one minute from the moment the IDE is launched.
Debugging capabilities are a must. That means tracing lines of code(step), breakpoints,  watches.
It should be able to create  *empty*  projects (or compile .cpp's without projects at all). I am tired of programs making 40+ files for (again) the HWorld program.

I need it for small personal(mostly console) projects that don't really need complicated GUIs. I also like to know what each and every line of code does :)

Thanks

---

### Post by TheOrangePeanut on 2008-02-13
If you're okay with using a command like IDE, why not just use the command line itself?  When I code simple, 1 file projects (which I've been having to do for my OpenGL class) I use g++ for compilation and gdb for debugging.  That's about as lightweight and quick as you can get :)

---

### Post by earobinson on 2008-02-13
geany is nice but you will still need to use the command line to compile.

eclipse is good but its not lightweight

---

### Post by amingv on 2008-02-13
Check the FAQ in the programming talk forum. There's an extensive discussion on IDEs there.

I saw Geany yesterday. It looks light and simple, but I haven't tried many IDEs, so I can't really tell.

Remember you must have the package build-essential.

---

### Post by Chronotrigger_BG on 2008-02-13
I am using the command line.
I'm experimenting with Geany right now and so far it's the one IDE that suits my needs best.
But it still doesn't have debugging! I want something with which I can trace.
And Gcd isn't exactly fast or easy to use. 

Eclipse...I tried that. Seems ok, but I heard that the C++ version is still not all that stable.
And Is there actually a way to set up watches in there? I mean except the ones that are automatically generated (and hidden once they're out of scope)? Because the auto-watches are too cluttered and not very helpful.
Seriously, is there a way?

---

