---
title: "[SOLVED] How to run a server"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Bliepo32 on 2007-06-26
I am a starting web developper, and I have the following problem. I want to install a server on an old computer, to test things before I put them online (the 'server' will not be connected to the internet). However, I have only recently begun with Linux, and the only commands I know are ls, cd and sudo.

Now my question is where I can find a good tutorial about the Ubuntu command line interface, and where I can find a good tutorial for running your own server.

---

### Post by ikonia on 2007-06-26
if you look on help.ubuntu.com at all the how tos there are guides for setting up apache/mysql/postgres/php/mono/etc etc etc.

thats an excellent place to start.

---

### Post by Bliepo32 on 2007-06-26
Allright. I will have a look over there, and if I have questions, I will post them here.

---

### Post by az on 2007-06-26
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by Bliepo32 on 2007-06-26
Thanks for all the reply's. I only have one question left. Is there are special tutorial for the Command Line Interface? Because I would like to know more about it.

---

### Post by Smandola on 2007-06-26
One option you may want to consider is searching/reading the posts in Ubuntuforums.org.  I've found almost everyhing I've ever had a question on.  The people out here are fantastic and I've always seem to get answers almost immediately... as long as I've worded the question correctly.  

Hope that helps.

---

### Post by patrickk on 2007-06-26
if you would like to get better at command line stuff, a good way to do so is only use the command line...submerse yourself in it and use only a terminal for a week or two.  you'll pick it up in no time.

---

### Post by mlentink on 2007-06-26
> **Bliepo32 said:**
> Is there are special tutorial for the Command Line Interface? Because I would like to know more about it.

try [this...]("http://www.linuxcommand.org/")

---

### Post by coolen on 2007-06-26
> **mlentink said:**
> try [this...]("http://www.linuxcommand.org/")

Ahh, you beat me to it.
That's the site I used when I first installed Debian. Incredibly useful.
Learn how to traverse the directory tree, read files (less is more), and the man command. From there, it's smooth sailing. I wouldn't recommend simply immersing yourself in the terminal before you have these basics. You don't throw your child in a pool before he knows how to doggy paddle.

---

### Post by Bliepo32 on 2007-06-27
Ok. I have one last question. Sometimes (when I use **ls** for example), the result does not fit on the screen. As I am using the server version, I can't scroll. How to solve this?

I already tried /p (in windows e.g. dir /p does what I want).

---

### Post by Bliepo32 on 2007-06-27
Whoops. Didn't mean to post this reply.

---

### Post by bren on 2007-06-27
see linux command advice already given or do this

> ls | less


bren

---

### Post by Bliepo32 on 2007-06-28
That code works perfect, but I have another problem. When working with mysql, some things don't fit on the screen as well, and " | less" doesn't work (which is locigal, as it isn't a command in mysql).

Anyone an idea?

---

### Post by hyper_ch on 2007-06-28
I ilke the howtos here: [http://www.howtoforge.com](http://www.howtoforge.com)

---

### Post by Bliepo32 on 2007-06-28
I googled around a bit and found this:
[http://ubuntuforums.org/archive/index.php/t-13245.html](http://ubuntuforums.org/archive/index.php/t-13245.html)

Maybe it woulde be handy to make a sticky from this in the server section. Just a suggestion...

---

