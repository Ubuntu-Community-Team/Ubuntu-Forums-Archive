---
title: "New to Linux,TerraIM"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by joexoreo on 2008-03-06
Im new to Linux and i just got it installed, got my wireless card working(Thanks to ubuntu forums) and i am learning commands pretty well for being a windows transfer. I didnt really like pidgin and im a old fan of terraim, its website saids its compile-able for Linux but doesnt have directions up and someone else said that its easy to do, I Was wondering if anyone know how and could tell me how to compile and run Terraim

---

### Post by drascus on 2008-03-06
you should first download the program and extract the archive. In the folder that results there should be a readme file that will tell you how to install that particular program. as not all programs are compiled the same way. hope that helps.

---

### Post by billgoldberg on 2008-03-06
The only download I found was a platform independent .zip file.

It had no install instruction and I didn't get it compiled (but I have very little experience with compiling).

I tried looking on the web and I didn't find any .deb packages. I found a .rpm package.

I'm going to try to convert the rpm (terraim version 2.1) to .deb but I don't know if it will work.

---

### Post by Nythain on 2008-03-06
Wow does that company/coders suck... there's like little to no documentation on compiling from source on any platform...

given the structure of source zip, i would say, download the zip, unzip it, cd into the src directory of the directory created by unzipping and then try the good ole
```

./configure
make
make install

```
im not at home or i would have tried further to install it... maybe need a sudo in there for the make install, who knows... but im assuming given the lack of documentation that a normal ./configure, make, make install method should work.

unfortunately, there's also no documentation in the zip on dependancies, if any, or anything... make sure you have build-essential installed first though...
```

sudo apt-get install build-essential

```
or just search for it in adept/synaptic

hope that helps a little bit, if at all... be sure to post back any problems you might encounter, errors, missing libs, etc

---

### Post by billgoldberg on 2008-03-06
No, the conversion and installation of the converted .rpm worked, using it didn't.

---

### Post by billgoldberg on 2008-03-06
> **Nythain said:**
> Wow does that company/coders suck... there's like little to no documentation on compiling from source on any platform...

given the structure of source zip, i would say, download the zip, unzip it, cd into the src directory of the directory created by unzipping and then try the good ole
```

./configure
make
make install

```
im not at home or i would have tried further to install it... maybe need a sudo in there for the make install, who knows... but im assuming given the lack of documentation that a normal ./configure, make, make install method should work.

unfortunately, there's also no documentation in the zip on dependancies, if any, or anything... make sure you have build-essential installed first though...
```

sudo apt-get install build-essential

```
or just search for it in adept/synaptic

hope that helps a little bit, if at all... be sure to post back any problems you might encounter, errors, missing libs, etc

I tried that. 

The first error it gave : "cant find ./configure directory" or something of that nature.

the make and make install gave alot of errors and failed.

---

### Post by Nythain on 2008-03-06
what errors does it spit out at you when you try to run it from the command line??

Edit: the program that is, not the compile instructions, since you've already mentioned those errors


on a side note, i never really trust converting rpm to deb... source compile is usually infinately easier for me, and at least tells me anything that goes wrong in the process

---

### Post by billgoldberg on 2008-03-06
Since you asked:

```

...
Driver.cpp:1851: error: expected constructor, destructor, or type conversion before &#8216;EVT_TIMER&#8217;
Driver.cpp:1864: error: variable or field &#8216;OnCloseTimer&#8217; declared void
Driver.cpp:1864: error: &#8216;int TimedMessageWindow::OnCloseTimer&#8217; is not a static member of &#8216;class TimedMessageWindow&#8217;
Driver.cpp:1864: error: &#8216;wxTimerEvent&#8217; was not declared in this scope
Driver.cpp:1864: error: &#8216;e&#8217; was not declared in this scope
Driver.cpp:1865: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
make: *** [Driver.o] Error 1
rw@legend:~/Desktop/TerraIM_1.2.5_source/src$ make install
make: *** No rule to make target `install'.  Stop.
rw@legend:~/Desktop/TerraIM_1.2.5_source/src$ 

```


I don't think it would be wise to past the whole 1869 lines of errors.

---

### Post by joexoreo on 2008-03-06
Well i tried the ./configure make make install, whole bunch of errors but atm i dont have my internet for that machine right now, so i will post the errors later but, there was no ./configure file so I couldnt do that command, the reason there is so little info on this program is cause it was made by 1 guy and was generally made for windows, on his side he said its multiplatform and said he would put up mac/linux instruction but that was like a year ago and never put the instructions up.

---

### Post by Vadi on 2008-03-06
Can you please pastebin the output?

It looks like you're missing a library it needs.

---

### Post by joexoreo on 2008-03-06
Just to let you know, the errors i got were the same as Bill's up top

---

### Post by billgoldberg on 2008-03-06
I don't think it will be able to install it on debian based systems.

There are other IM clients beside pidgin, browse through 'applictions -> add/remove' in the internet section.

---

### Post by joexoreo on 2008-03-06
Ok ill look for others, thanks for trying, i just figured i would see if it was possible but no big woop, thanks everyone

---

