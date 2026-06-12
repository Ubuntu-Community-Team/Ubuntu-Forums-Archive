---
title: "Question about Ubuntu."
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2006-02-03
Hello People,
I am new to linux. I have seen that are many distros available. Ofcourse I have ubuntu. I want to know, in addtion to the kernal, what are the other things common to all distros (if you could, please give commands also).
Thanks,
Linuxnovice.

---

### Post by bscbrit on 2006-02-03
Essentially, although the GUIs change from distro to distro, the commands for use in a terminal are fairly constant.  Try the last link in my sig - don't try to read it all but pick whatever you want from it. :-D

---

### Post by az on 2006-02-03
Some people write software for other people.  They work and are paid by the hour.  What they write belongs to their employer.  It is their property.  This is an example of proprietary software.

Some people feel that because software code is so close to being an idea (an algorithm that someone else would have written anyway) you cannot make it property.  This is the principle of free-libre software:  software is not property.

The practical aspect of this is that you can "stand on the shoulders of giants" and write really intersting applications, just by reusing and improving existing code.  The GPL is the licence that says that anything you release under the GPL has to remain free.  Anybody who uses your GPL'ed code has to release that new code under the GPL as well.

All linux distributions use common source code.  Most of the individual projects whise applications are shipped with a linux distribution are open source collaborative projectes.

The interface for these projects is the source code.  When you compile the code, you turn it into a binary executable that runs.  You cannot take a binary and turn it back into code.  The C programming language does not work that way.

You usually cannot take a binary built for another distribution and run it in another distribution.  These binaries are built using the GNU toolchain (free-libre compiler suite)  Not everybody uses the same version of the toolchain.  Usually, one application needs a certain library to work.  Those libraries are not always the same version from distro to distro.  There are two reasons why binaries are not interchangeable from distro to distro.

While you are free to get the source code for an application and compile it on your distribution, it is less convenient than just installing the prebuilt binary version that shipped with your disto.

Ubuntu releases every six months, which is pretty often.  It can usually ship with more applications being at a more recent version than other distributions, on the whole.  There are always exceptions.

Some distributions are less militant about free-libre software.  An example of that is hardware vendors who do not distribute drivers for ther stuff in source-code form.  They only supply prebuilt binary drivers.  This upsets the free-libre software proponents who want to know what the thing does before installing it.  It is kind of like buying a car with the hood welded shut - you don'T know and are not allowed to change the way the motor works.

There is no guarantee that binary-only applications are not spying on you or are unstable.

Debian linux is pretty militant.  Since there are many open source licenceses available, they use the DFSG (Debian free software guidelines) which are strict.  For example, firmware - which is code that is executed by a peripheral device, and not the kernel in your computer, is considered software and is not dfsg-compliant unless you get the source code.  Other distributions are more leniant about distribting such firmware and binary-only drivers.

Ubuntu distributes them, but they are packaged seperately.  If you install ubuntu, you have them, but if you remove the linux-restricted-modules package, and do not enable the multiverse repository, you are completely free-software.

There are more diffrerences, but I think I have bored you enough...

---

### Post by weasel fierce on 2006-02-03
If its any help, a lot of linux-generic books, with commands and ways to use it, will work across most linux distributions.

---

