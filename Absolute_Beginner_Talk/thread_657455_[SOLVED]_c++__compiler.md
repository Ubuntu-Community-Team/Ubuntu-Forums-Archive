---
title: "[SOLVED] c++  compiler"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by chips24 on 2008-01-03
the c compiler is intalled by default in ubuntu 7.10 right?


i installed ubuntu on my computer twice, and they both dont have it.i need the c compiler because i dont have a internet connection on my laptop, at least on my ubuntu side/ i dualboot vista. and ive had a bad experience with NDiswrapper. couldnt find it. 

i also (every once and a while) will right my own program so i neeeed that C compiler. if i install the iso again and the distro dosnt have it, what should i do?

---

### Post by LaRoza on 2008-01-03
No.

See my wiki, then the wiki that it links to for specifics on Ubuntu.

---

### Post by chips24 on 2008-01-03
ok, can i get a c compiler off of the vista side and install it onto my ubuntu side?

---

### Post by LaRoza on 2008-01-03
> **chips24 said:**
> ok, can i get a c compiler off of the vista side and install it onto my ubuntu side?

?

I don't know what you are asking.

Run this command:

```

sudo aptitude install build-essential

```

It will ask for the CD you installed with.

See my second wiki (linked to in my main wiki) for how to use it.

---

### Post by PinkFloyd102489 on 2008-01-03
sudo apt-get install gcc

---

### Post by LaRoza on 2008-01-03
> **PinkFloyd102489 said:**
> sudo apt-get install gcc

No, gcc is already installed. build-essential is needed to use it.

---

### Post by chips24 on 2008-01-03
apt-get build-essential

right?

i can find a ethernet connection.

---

### Post by LaRoza on 2008-01-03
> **chips24 said:**
> apt-get build essential

right?

i can find a ethernet connection.

build-essential

A dash is there.

The code is posted in my first post...

---

### Post by stburman on 2008-01-03
I think you can just install g++ if you only want the compiler.  This will make it easier if you're trying to find all the packages on your other os at packages.ubuntu.com.

---

### Post by LaRoza on 2008-01-03
> **stburman said:**
> I think you can just install g++ if you only want the compiler.  This will make it easier if you're trying to find all the packages on your other os at packages.ubuntu.com.

I don't think you understand...

g++ is gcc and gcc works by compiling code to assembly so as can assemble it.

You need the compiler, preprocessor, linker and assembler to do this, and you need the headers. 

```

sudo aptitude install build-essential

```

This will install all you need, and build-essential is on the cd so you don't need the internet.

[http://laroza.wikidot.com/C](http://laroza.wikidot.com/C) has all this information, which I stated in my first post, and I posted the package to install in my second.

---

### Post by chips24 on 2008-01-03
ok, im confused, is k, build essential the c compiler? because first im hearing that its not on the disk than im hearing its not, oh yeah, i dualboot vista and ubuntu 



LaRoza  	
Re: c++ compiler
Quote:
Originally Posted by chips24 View Post
ok, can i get a c compiler off of the vista side and install it onto my ubuntu side?
?

I don't know what you are asking.

Run this command:

Code:

sudo aptitude install build-essential

It will ask for the CD you installed with.

See my second wiki (linked to in my main wiki) for how to use it.

---

### Post by LaRoza on 2008-01-03
You are in Ubuntu, run this command in the terminal:

```

sudo aptitude install build-essential

```

Copy and Paste it.

It will ask for the Ubuntu CD, put it in and press enter.

Disregard anything anyone one else has said.

---

