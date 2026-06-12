---
title: "help with 'make' and 'make install'"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by strebor71 on 2006-02-13
i have been happily exploring the new world of linux with ubuntu and loving it. and am slowly beggining to understand how to deal with "tar balls" and installing pakages with dpkg. but recently i tried to install the clearlooks gtk+ engine. i have downloaded and unzipped and untarred the file (had a .b2z extention) i opened the readme file that was included which instructs how to install. all it says is to run:
 ./configure
make
make install

sounds simple enough, so i ran the ./configure and it seemed to run succesfully i then tried to enter the 'make' command. and recieve a :command not found error. now im stummped. have attempted all usuall recources to find help but cannot seem to find a 'noob' version of what these commands do or how to use them:confused. i know there must be a simple explanation, but ill be dammed if i can find it. please help.

---

### Post by paulmilliken on 2006-02-13
Installing from source is more difficult that using the repositories because you have to sort out dependencies yourself.  The "command not found" error indicates that one of the dependent packages is missing from your computer.  If you can find the package that you want in the repositories then it's best to use synaptic (a front end for apt-get) to install it as it will automatically find all the dependent packages.

Please post the output of "make" so that someone can help you to track down what other package(s) you need to install.

Paul

---

### Post by strebor71 on 2006-02-13
thats just it, i get nothing after entering make command that would hint as a solution. just command not found error. i do know of the synaptic and apt-get but i would like to learn how to install from source. you know reach my next milestone as it were :) .

---

### Post by BenTyreman on 2006-02-13
Have you done
```
sudo apt-get install build-essential
```

I get the feeling make is in there somewhere.

---

### Post by linear on 2006-02-13
You need to install the 'build-essential' package in order to compile. I'd also recommend 'checkinstall' so that you can use package management tools (apt-get or synaptic).

So:

./configure
make
sudo checkinstall

would build a .deb package at the same time it installs.

---

### Post by cwaldbieser on 2006-02-13
[QUOTE=BenTyreman]Have you done
```
sudo apt-get install build-essential
```

I get the feeling make is in there somewhere.[/QUOTE]
Yeah, that package will install make, the compiler (gcc) and other software building tools.  You would also do yourself a favor to get the "checkinstall" package.

Any time you would type "sudo make install", type "sudo checkinstall" instead.  This will turn the source you build into a .deb package that you can uninstall at a later time.

---

