---
title: "some questions about scripts"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by sandro87 on 2008-04-01
i wanted to write a script that will change some nautilus properties every now and then (wanted to write it alone so i can learn a bit more about ubuntu), so i have a few questions about scripts ..

1. i've seen in scripts that i've found over net that they are written in perl, but i'm familiar with c and c++. can i write scripts in c/c++ ? do i need to say somewhere in the file that it is in c, or when it gets executed ubuntu sees that it is in c ??

2. to make a script that starts on every login, do i need to put it in the nautilus folder for scripts, or anywhere i want to, and then add it to sessions -> startup programs?

if there is anything else i need to know about scripts, pls let me know or put a link to a useful guide.

tnx

---

### Post by alexforcefive on 2008-04-01
*edit* replied to the wrong thread! nooooo >.<

---

### Post by jrib on 2008-04-01
1. Scripts usually refer to text files that an interpreter (like ruby, perl, python, or bash) runs.  C and C++ are compiled languages.  Which means you write a text file with C or C++ code in it and then compile it.  You can write a program in C or C++ and compile it if you want (search for a guide on compiling with gcc if you want to do this).

Scripts are usually easier to write.  I don't know of guides to recommend for ruby or perl, but for bash and python I like:
* bash:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)
[http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)

* python:
[http://docs.python.org/](http://docs.python.org/) (start with the tutorial)
[http://diveintopython.org/](http://diveintopython.org/)
[http://rgruet.free.fr/PQR25/PQR2.5.html](http://rgruet.free.fr/PQR25/PQR2.5.html)

I like python, but it's good to know some shell scripting as well.

2.  To make a program run when you startup use sessions -> startup programs.  I'm not sure what you man by "nautilus folder for scripts".


Here's a hello world program in bash:
#!/bin/bash
echo "hello world"

Here's one in python:
#!/usr/bin/python
print "hello world"

save as a file, give execute permissions: chmod +x file, and execute it: ./file

---

### Post by forrestcupp on 2008-04-01
If you already know C or C++ really well, you could always compile the binary file and make it automatically start up in your sessions.  But if you're not really advanced in C/C++, you definitely should look into scripting with bash and python.

---

