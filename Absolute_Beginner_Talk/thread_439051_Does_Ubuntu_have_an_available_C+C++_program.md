---
title: "Does Ubuntu have an available C+/C++ program?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-10
I really want to get into programming and learn myself up a bit to help with Ubuntu issues.  Basically, I have free time and want to contribute :D

Any free programs for this?

---

### Post by LaRoza on 2007-05-10
Ubuntu has g++ as the compiler, 

sudo apt-get install build-essential

will give you everything you need.



-edit

If you have no programming experience you might want to learn using a different language first, like Python. For Python you do not need to install anything.

There is no "C+", only C and C++. "++" is how many languages increment variables.

---

### Post by derjames on 2007-05-10
hi there... please have a look at the 'programming talk' subforum in particular to this thread

[http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)

happy coding...

---

### Post by gohanssjn on 2007-05-10
Thank you both, I'll get on it as soon as I can.

I did some C way back, so I figure it's just better to start from scratch.

Thanks again!

---

### Post by Terl on 2007-05-10
Check out:  [NetBeans]("http://www.netbeans.org/").  It is an IDE and compiler too.  It works for a variety of languages (C and C++ with a plug-in) and is packed with documentation and tutorials.

---

### Post by u04f061 on 2007-05-10
The only thing i dislike in ubuntu is unavailability of build tools by default. why is it so?

---

### Post by martijn_bakker on 2007-05-10
At the very least, you will need a compiler. The most common C/C++ compiler available for linux is called gcc. You will install gcc and most other tools necessary for compiling C/C++ programs by installing the package "build-essential".

You can do this in one of two ways:

1. Open a terminal (Applications->Accessories->Terminal) and in the terminal window, type "sudo apt-get install build-essential"
2. Open the package manages (System->Administration->Synaptic Package Manager), find the build-essential package, right click to mark it for install and then click on the green Apply icon (and confirm by clicking Apply again in the popup).

Now this will give you only a basic set of command line tools. If you would prefer a more integrated development environment then you might want to try using some IDE. You could install the "kdevelop" package from the Ubuntu repositories (in the same manner as you just installed build-essential). Personally, I much prefer Code::Blocks ([http://www.codeblocks.org/]("http://www.codeblocks.org/"))

---

### Post by Cypher on 2007-05-10
> **u04f061 said:**
> The only thing i dislike in ubuntu is unavailability of build tools by default. why is it so?

The Desktop version of Ubuntu tries to be an easy migration of users of Windows and in that, keeps the availability of programming and other tools to a minimal. It doesn't even install the build-environment. The general mass of people who are migrating aren't programmers. 

However, if you are so inclined to learn/do programming, you need to look no further than Synaptic's Development/Programming tab to find a plethora of IDEs and tools..

---

### Post by Spook27 on 2007-05-10
One thing I've found rather nice is that even your basic text editors (GEdit, Kate and vim come to mind) often have support for little niceties like syntax highlighting, code folding and relatively sane treatment of tabs, so even after you get build-essentials, you won't really have to jump out and get an IDE.  And...  There's plenty of those out there if you want them.

---

### Post by u04f061 on 2007-05-10
You are right but there is also a problem in not providing build tools. for example build essential is not capable of building softwares. for example i tried two softwares to build using build essential which are stardict and ngspice. every time it gave an error that this library is missing. i kept on installing everything it asked. it took 2 hours to do this and i ended up with a package which i could not find in apt-cache search. so i ended with zero output.

---

### Post by rich.bradshaw on 2007-05-10
Yeah, compiling is only really for the hardcore people! (not me either!)

If you compile yourself, it won't appear in apt will it, because you made it, it's not in any repo.

---

