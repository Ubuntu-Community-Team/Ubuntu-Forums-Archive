---
title: "Compile source code GCC ANSI C"
date: 2007-08-27
forum: Apple Intel Users
---

### Post by verbatim210 on 2007-08-27
**I'm using Mac OS X, not ubuntu...**
Sorry to post this here, but I have no where else to go :(

I'm trying to compile WINE from source (so i can use that to port quincy.exe across)

I've downloaded and installed Xcode, only the GCC components.

Here is the result...

It says GCC is not found, any ideas?

Thanks really need to get this up soon get some homework done :)

---

### Post by cyberdork33 on 2007-08-27
it doesn't say no C compiler is found, it says no acceptable compiler is found. Apple's version of gcc is crippled.

---

### Post by Viro on 2007-08-28
I know it's popular to bash Apple but please read the error message before spouting misinformation. The version of GCC that Apple ships is not "crippled", unless you're going to be kind enough to explain exactly *how* it is "crippled".

The problem you're facing is that the config program can't find gcc in your PATH. This should not happen, since there are links to gcc in /usr/bin and that directory should already be on your path. I suggest downloading the latest version of Xcode and installing the whole thing. 

I followed the instructions [here](http://blog.alantan.com/2007/02/compile-wine-on-mac-os-x-tiger.html) and it worked fine for me.

---

### Post by verbatim210 on 2007-09-18
Thanks for the Viro, I installed the whole thing and it worked as well...

I just didn't want to install 1gig worth of junk just for a compiler that is about 10meg.

---

