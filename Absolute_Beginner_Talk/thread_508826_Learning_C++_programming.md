---
title: "Learning C++ programming"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by feistyfirsttimer on 2007-07-24
I dual-boot Ubuntu Feisty and WinXP.

I wanna learn C++ programming, and found a book called "C++ for dummies".  It comes with a CD that has Dev-C++, a "full-featured, integrated C++ compiler and editor" - for Windows.

I could install it on my XP partition, but I'd rather do this in Ubuntu.  What would you all suggest I get from the repos that will give me a similar package to the Dev-C++?

---

### Post by Mornedhel on 2007-07-24
I'm itching to test Anjuta myself (it's in the repositories and all), but at work I'm stuck on ole Visual C++ 6, and when I get home I try to relax (and code in Perl, heh)

---

### Post by Rocket2DMn on 2007-07-24
The windows program will probably give you a good editor that can help you with syntax and other such convenient things, but there is no way to learn like typing it up in a good old fashioned text editor and compiling with g++, then having to debug yourself.  Some *nix text editors will allow syntax highlighting that will recognize that you are programming and can color-code variables and other specific statement types.
I use an editor called emacs - it can be rather cryptic, but it's what they showed us to use on the unix systems at school.

---

### Post by Mornedhel on 2007-07-24
Ah, emacs, the editor of the Gods, and of their high priest Richard M. Stallman.

I find SciTE to be a good editor, with syntaxic coloration and all, and much less cryptic than emacs (but also a hundred times less powerful - after all, you can * play games * in emacs, and talk to your shrink about your problems in life...)

---

### Post by LaRoza on 2007-07-24
In Ubuntu, GEdit is a very good editor. g++ is the compiler and linker.

```

sudo aptitude install build-essential

```
This will give you everything you will need for C/C++ programming.

If you want other resources, free tutorials and free books, see my wiki in my sig, "Learn to Program".

---

