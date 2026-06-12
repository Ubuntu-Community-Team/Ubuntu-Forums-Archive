---
title: "C compilers in ,linux"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by natman on 2007-06-23
Hi,
I not sure if this is the right place or not, but i have a dual core intel core2 and i am running a C++ program thats taking 24+hrs, under MS visual studio 6, but thats only using one core.
Is there any open source/linux c++ compiler version that will fully use both cores?

Thanks:

---

### Post by mendingo84 on 2007-06-23
gee, this is tricky :). does g++ do the job? have you tried to see if that is so?

---

### Post by natman on 2007-06-23
This is where i must pleed ignorance, i cant compile from the terminal, if you want to help feel free. But to date ive been using Anjuta, and Kdevelope ( which no longer works for me for some reason - thanks feisty upgrade )

---

### Post by Cypher on 2007-06-23
You have "Makefiles" for your project? If so, you should be able to just call "make". G++/GCC allows you to run parallel compilation by spawning multiple compilation threads. With a dual-core CPU this should definitely speed up he compilation.

How many millions of lines of code are you compiling that it's take 24+ hours in VC++..

---

### Post by natman on 2007-06-23
Im not working with million only maybe a hundred or so, its a math program that uses brut force to find a couple of thousand answers, but the method is very slow, imagine breath first search with a ver very very very wide tree.
Could you elaborate on what you ment by
[HTML]You have "Makefiles" for your project? If so, you should be able to just call "make". G++/GCC allows you to run parallel compilation by spawning multiple compilation threads. With a dual-core CPU this should definitely speed up he compilation.
[/HTML]

I have the .cpp files, do i just use a terminal command? how does gcc know to use parralle  processing? or does it by default since i have a 64 bit kubuntu ( support for dual as standard )?
If its not too much trouble do you know where i could get the terminal commands?

---

