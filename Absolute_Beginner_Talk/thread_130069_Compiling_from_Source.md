---
title: "Compiling from Source"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by Vuen on 2006-02-15
Hi, I'm trying to compile Audacity from source on Hoary. It says get the source tarball, unzip it somewhere, and run configure and make and etc from wherever you unzipped it.

So where should I unzip it?

---

### Post by carlosqueso on 2006-02-15
You can unzip it anywhere that you can find it.  I'd use a subdirectory in your home directory.  When you run your final command (probably "make install") it'll put the files where they belong.

---

### Post by LordBug on 2006-02-15
I don't know Hoary, but is Audacity not in it's repositories?  I'd check Synaptic before you proceed with trying to compile from source.  To directly answer your question though:

Unzip wherever you want :)  I generally download things into my home directory, so I just unzip them right there.  Source tarballs will make a new sub-directory and dump all the files into there.  You'll cd into that new directory and proceed with your respective configure and make commands (follow the instructions provided with source code).

I would also suggest installing the basic dev tools, you're going to need them:

apt-get install build-essential
apt-get install gcc

You'll likely need more dev tools as well, I don't know what all Audacity requires for compiling.

---

### Post by Vuen on 2006-02-15
Ah, I didn't realise Make Install put it where its supposed to go; I thought it just stayed where you compile it.

Yes, Audacity is in its respositories, but it doesn't work. I want to compile it with a few different options to see if I can get it to work.

Thanks.

---

