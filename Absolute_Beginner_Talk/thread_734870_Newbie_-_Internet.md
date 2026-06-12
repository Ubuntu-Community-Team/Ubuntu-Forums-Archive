---
title: "Newbie - Internet"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Jonesbk on 2008-03-25
Hi All

I am trying to get my old pc, up and running for my little girl.

1. Does Ubuntu need internet connection? I assume the answer is no, but would make life easier.

I have Iburst and 3g, but if I can not even figure out the simple things in Ubuntu how am I supposed to connect with Ibdrive to the internet.

2. User Manual, is there something like this for Ubuntu for idiots?

3. Dvd reader, to read AVI, VOB 

4. Change directory, (cd ) is there and Ubuntu "dir" to see what files are availiable to open.

Any help will be appreciated

---

### Post by hyper_ch on 2008-03-25
without inet you should download the dvd as it contains a lot more softare. However does that computer feature a dvd drive?

What's iburst and 3g?

User manual: There are some sources out there that covers most of the basics:
[http://www.psychocats.net](http://www.psychocats.net)
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)
[https://wiki.ubuntu.com](https://wiki.ubuntu.com)

You can use a tool to locally mirror that stuff, then you have a "manual" even without inet access...

For DVDs you need to install additional codecs and libdvdcss2

not sure what you mean with the "cd" and "dir" stuff...

---

### Post by Squish on 2008-03-25
1> Although ubuntu with no internet is possible, internet is allot of what makes linux useful. For example, installing programs from the Add/Remove Programs found in your Applications bar, downloads everything from the internet.

2> My favourite learning tools are the Ubuntu Screencasts, check them out:
[http://screencasts.ubuntu.com/]("http://screencasts.ubuntu.com/")

3> DVD Reader? Do you mean to rip dvd's, or view them on your computer? Both are possible btw

4> I am sorry, I am not sure exactly what you mean...
cd - works for changing directories. 
ls - To list the files of the current directory

---

### Post by Triggerhapp on 2008-03-25
> **Jonesbk said:**
> 4. Change directory, (cd ) is there and Ubuntu "dir" to see what files are availiable to open. DIR is the old DOS command equivalent to ls.

```
ls -l
``` to give date and permission details

---

### Post by Jonesbk on 2008-03-25
The response is awesome, thanks guys

"dir" is dos

Also where can I get a list of all the commands such as; cd, ls

I been trying to download ibdrive from a cd (which I copied, onto the cd via the internet on my laptop). How would I load/install/run  on Ubuntu

---

### Post by hyper_ch on 2008-03-25
Here's a small cheat sheet:  [http://www.digilife.be/quickreferences/QRC/UNIX%20commands%20reference%20card.pdf](http://www.digilife.be/quickreferences/QRC/UNIX%20commands%20reference%20card.pdf)

To know more about a given command, use the man pages

```

man COMMAND

```

e.g. for the "cd" command
```

man cd

```

---

