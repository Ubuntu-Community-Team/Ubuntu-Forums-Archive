---
title: "I'm having trouble installing Tar.gz. Please Help. This is important."
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by YellowHat on 2006-06-24
dev-src_Jun_24_20h55.tar.gz

this is the file I'm trying to install

I already have build essential. 

So, I created a folder named Dev and then I put the tar.gz inside the folder. I then unpacked it and brought up the terminal. I Cd'd to Dev and then typed make inside the terminal and then typed  ./configure. I get bash: ./configure: No such file or directory
.

So as you can see. I can't even get to the make install step. Because ./configure just won't work for me.

---

### Post by Kilz on 2006-06-24
[QUOTE=YellowHat]dev-src_Jun_24_20h55.tar.gz

this is the file I'm trying to install

I already have build essential. 

So, I created a folder named Dev and then I put the tar.gz inside the folder. I then unpacked it and brought up the terminal. I Cd'd to Dev and then typed make inside the terminal and then typed  ./configure. I get bash: ./configure: No such file or directory
.

So as you can see. I can't even get to the make install step. Because ./configure just won't work for me.[/QUOTE]
Some source packages dont have a configure, and it would be the first step. Look in the folder, do you see a configure file? If so just type in ```
./configure
``` in the terminal. Wait to see if there are any errors. If it says it cant find a lib, I usualy search in synaptic for libname-dev. 
Once it stops, or if there isnt a configure file type in ```
make
```, and hopefully it will make a binary. If it dose type in ```
make install
```.

---

### Post by Apple 101 on 2006-06-24
What about the autogen.sh file that is sometimes in sources?  Is that an alternative to ./configure?

---

