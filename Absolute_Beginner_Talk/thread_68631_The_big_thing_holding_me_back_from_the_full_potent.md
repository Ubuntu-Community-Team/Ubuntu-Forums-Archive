---
title: "The big thing holding me back from the full potential of linux..."
date: 2005-09-23
forum: Absolute Beginner Talk
---

### Post by xequence on 2005-09-23
Ok. Many linux programs are in .tar.gz format, or whatever the extension is. I have tried many times, posting many times, to learn how to compile. It NEVER works. Can anyone explain, step by step, what files I would have to get and what commands I have to do to compile?

I have just the normal hoary hedgehog kernal, nothing special. The one thing that annoys me is people who think everyone knows as much as them... You have no idea how many times ive seen "You just do a simple sudo make install to install it". That, to me, is VERY annoying.

I was told I needed kernal headers or something, then that didnt work, and they forgot to tell me I needed x window system headers or whatever.

I havnt downloaded ANY headers or anything. No development things, nothing.

---

### Post by 23meg on 2005-09-23
maybe the convenience of [ checkinstall](http://asic-linux.com.mx/~izto/checkinstall/) will get you a bit more enthusiastic about compiling from source.

- install the following: linux-headers-xxx , linux-source-xxx , linux-tree-xxx (xxx being your cpu architecture), make, gcc, checkinstall

- unzip/untar the archive. if there's no setup script (usually setup.sh), and if the README file does not instruct otherwise, go to the folder where you extracted the archive in the terminal and type "./configure"

- you'll see lots of scrolling text; if it complains about not finding a certain version of a certain library, find a package of it and install it. if it's not in the ubuntu repositories, see if the  website the source came from points you to a download location.

- assuming everything went fine, type "sudo make".

- the compilation process will begin. it usually goes fine. now type "sudo checkinstall".

- in the normal linux way of doing things, you'd be typing "install" instead of "checkinstall"; here the difference is that checkinstall will create a .deb package of the compiled software and automatically install it. this means that you can easily uninstall and reinstall the software in the future using apt-get or synaptic.

hope this helps..

---

### Post by Wolki on 2005-09-23
> **23meg]
- install the following: linux-headers-xxx , linux-source-xxx , linux-tree-xxx (xxx being your cpu architecture), make, gcc, checkinstall[/quote]

kernel headers and source are not needed for normal compiling.[Oops that's what i get for not reading the original question thoroughly.... even then, headers should be enough I think. Compiling stuff that nneds the kernel can be a bit ugly, maybe try something else first?]  Instead of installing gcc and make, get the "build_essential" package. You'll probably need automake too. Chackinstall is a very good idea.
[QUOTE]
- you'll see lots of scolling text said:**
> 

It's important to have normal and -dev packages of required libraries. Most you'll need are available from synaptic..

[QUOTE]- assuming everything went fine, type "sudo make".

No reason to compile as root, "make" is enough.

Xequence, maybe someone on IRC will walk you through installing if you have any problems. A real-time conversation can really help here.

[edit: me being stupid]

---

### Post by matthew on 2005-09-23
Everyone is giving good advice. I just thought I would add a link to this site that you might find helpful.
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by 23meg on 2005-09-23
does my memory fail me or did build_essential use be in the main repositories? i can't see it in breezy; that's why i didn't mention it. or was it in backports?

---

### Post by bored2k on 2005-09-23
[QUOTE=23meg]does my memory fail me or did build_essential use be in the main repositories? i can't see it in breezy; that's why i didn't mention it. or was it in backports?[/QUOTE]
```
grep@noir:~$ search build-essential
build-essential - informational list of build-essential packages

``` It's on breezy.

---

### Post by 23meg on 2005-09-23
sorry, i've spelled it with an underscore..

---

### Post by xequence on 2005-09-23
Thank you every body very much :) This looks like alot of help and when I get back to my ubuntu computer ill try it =)

---

### Post by weasel fierce on 2005-09-24
When I run "make" I get this:
make: *** No targets specified and no makefile found.  Stop.

---

### Post by Knome_fan on 2005-09-24
[QUOTE=weasel fierce]When I run "make" I get this:
make: *** No targets specified and no makefile found.  Stop.[/QUOTE]

You'll probably have to run ./configure first.

---

### Post by weasel fierce on 2005-09-24
Allright, got the configure done properly, after installing a load of dev packages.
Synaptic is a dear friend of mine now :)

When I run make, it exits with this:

make[2]: *** [filesystem.o] Error 1
make[2]: Leaving directory `/home/weasel/Desktop/wesnoth/wesnoth-1.0rc1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/weasel/Desktop/wesnoth/wesnoth-1.0rc1'
make: *** [all] Error 2


Is there something particular thats not right, or are there certain other packages Im lacking ? 
I know this is a little vague, but Im not really sure how to proceed from here. 
For what its worth, Im trying to compile battle for wesnoth 1.0

---

### Post by BoyOfDestiny on 2005-09-24
I get this occasionally too (folder related errors). 

It might be all done though. Check your /src directory and see if there is a binary there (I'm going to guess a file called wesnoth, that has like a purple icon)

My advice would be to download checkinstall from synaptic. Then run sudo checkinstall, this will install it and make .deb .

---

### Post by weasel fierce on 2005-09-24
Well, I tried running both configure and make again, and now its compiling happily

---

### Post by weasel fierce on 2005-09-24
aand we have a functioning program :)

---

