---
title: "Help installing G++"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by ryangoff on 2007-08-08
I feel almost silly asking this, but I'm still very new to Linux...

I want to install and run G++ on Ubuntu. I opened up Snaptic Package Manager and found g++-4.1. I selected it for install and applied it. It downloaded g++ and all the associated dependencies. Now I'm searching around the computer and can't find where it is, or how to run it.

Looking in the /usr/bin folder, I have both the g++-4.1 and gcc++-4.1 files, but despite all my efforts, I can't figure out how to run it.

---

### Post by Cypher on 2007-08-08
Open a terminal and type
```

sudo apt-get install build-essential

```

---

### Post by ertrules22 on 2007-08-08
I am just wondering, G++ is for C++ development right?
Or what is it for exactly?

:guitar:

---

### Post by Rocket2DMn on 2007-08-08
You compile from terminal simply by running
```
g++ [-o outfile] infiles
ex:
   g++ -o myprogram.out myprogram_code.cpp myprogram_code2.cpp
```

g++ is a compiler for C++ code.  gcc is for C code.

---

### Post by ryangoff on 2007-08-08
I've tried ...

```
sudo apt-get install build-essential
```

... as well. What came up in the terminal was:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libgc-dev libocc0c2a
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

That means that it searched and found that everything under build-essential has already been installed on my computer, correct? I just haven't figured out how to run it yet.

---

### Post by Rocket2DMn on 2007-08-08
You have everything you need, except maybe some code to actually compile.
These compilers are needed for times when you compile programs from source (that maybe you downloaded b/c they weren't in the repositories).  You also need them to compile any code you write, like if you're trying to teach yourself to program in C or C++.

---

### Post by Cypher on 2007-08-08
Yes, it looks like you already have it installed. So confirm it with
```

dpkg -l | grep g++

```
This will list the packages, probably "g++-4.1", so you can then do
```

dpkg -L g++-4.1

```
to list the contents.

Or
```

which g++

```
to find the executable, usually it will be located in /usr/bin..

---

### Post by ryangoff on 2007-08-08
> **Rocket2DMn said:**
> You have everything you need, except maybe some code to actually compile.
These compilers are needed for times when you compile programs from source (that maybe you downloaded b/c they weren't in the repositories).  You also need them to compile any code you write, like if you're trying to teach yourself to program in C or C++.

Thanks guys. I just took a conceptual wrong turn at Albuquerque.

I'm used to Visual Studio C++. You know... the Microsoft version with all the pretty colors, bells, and whistles. I was looking for a windowed program like that, and not something you use purely from the terminal.

No wonder I was all confused.

---

### Post by Hospadar on 2007-08-08
If you are looking for an ide, I would suggest the eclipse with cdt (download them from the eclipse website, they are much newer than the versions in the repository) or anjuta or kdevelop from the repository.  Kdevelop is for kde, but it works fine in gnome and is a little more more full featured than anjuta at present.  

both of those can be had from the repository with a "sudo apt-get install anjuta" or "sudo apt-get install kdevelop"

I use eclipse personally, It feels to me the most complete and is also probably the most ms VS like of the three

---

### Post by Cypher on 2007-08-08
> **ryangoff said:**
> Thanks guys. I just took a conceptual wrong turn at Albuquerque.

I'm used to Visual Studio C++. You know... the Microsoft version with all the pretty colors, bells, and whistles. I was looking for a windowed program like that, and not something you use purely from the terminal.

No wonder I was all confused.

Once you get the packages installed, there are indeed numerous IDE's that you could use that will not require you to compile from the command line. Furthermore, these tools will also create the necessary Makefiles to make the build possible.

[This]("http://linuxmafia.com/faq/Devtools/ides.html") is a good list of IDEs available based on languages..

---

