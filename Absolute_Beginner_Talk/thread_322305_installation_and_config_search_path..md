---
title: "installation and config search path."
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-12-20
Hi eveyrybody

WHile installing the program wv via ./configure, I got the following message
> 
checking for libgsf-1 >= 1.13.0... configure: error: Package libgsf-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgsf-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgsf-1' found 

:confused: 

I've tried to install the pachage via synaptic but it is already installed.
What am I supposed to do?
Thanks for any help

---

### Post by jrib on 2006-12-20
wv is in the [universe]("https://help.ubuntu.com/community/Repositories") repository.  Just enable universe and install it from there using synaptic or apt-get.

The reason your configure fails though is you need the -dev packages for that library, take a look at [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware) if you are really interested.

---

### Post by helphope on 2006-12-20
Thanks Jason.
I didn't understand the mistake I was making; anyway I managed to enable the universal repos and install wv, but I can't run it.
I tried wv from terminal, I've looked everywhere in the menus, but it doesn't turn out anywhere. What can I do?

It seems you know the program; I've tried catdoc before it, but it gives me odd characters for characters with accent.

thanks again

---

### Post by jrib on 2006-12-20
I've actually never used the program.  Whenever I am in that situation though, there are a few things that usually help:

1) This will list all the files that the package installed to a place with "bin" in the name.
```

dpkg -L wv | grep bin

```

2) Take a look in /usr/share/doc/wv .  You'll see a README file in there that should explain how to use the different programs you found above.

3) You'll notice that most (all?) of the programs listed in (1) have manual pages, so just take a look at those too.

---

### Post by helphope on 2006-12-20
Thanks. Everything is Ok.

The point is that from terminal I need to type wvText; for instance

> wvText file.doc  file.txt

changes the doc file into a txt one.

Options to change into PDF, HTML, ...

So, thanks again :)  and merry Xsmas

---

### Post by jrib on 2006-12-20
> **helphope said:**
> Thanks. Everything is Ok.

The point is that from terminal I need to type wvText; for instance



changes the doc file into a txt one.

Options to change into PDF, HTML, ...

So, thanks again :)  and merry Xsmas

np, Happy Holidays to you as well :)

---

