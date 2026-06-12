---
title: "where is gcc"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by chadmichael on 2006-08-11
I know that gcc is installed on my system, but I can't find it.  Does anyone know where it is?  

Furthermore, does anyone know why its not on my default path?  Philosophically speaking I mean.

---

### Post by dusu on 2006-08-11
I think gcc is not installed by default in Ubuntu...
are you sure you installed it by hand ?

---

### Post by mostwanted on 2006-08-11
It's a command-line program, not a graphical IDE.

---

### Post by chadmichael on 2006-08-11
There are several versions of gcc installed on my system.  In particular, I found gcc-4.0 in /usr/bin.  I understand that this is not a graphical user interface application.  

So, ubuntu doesn't use gcc to compile itself?

---

### Post by mostwanted on 2006-08-11
> **chadmichael said:**
> There are several versions of gcc installed on my system.  In particular, I found gcc-4.0 in /usr/bin.  I understand that this is not a graphical user interface application.  

So, ubuntu doesn't use gcc to compile itself?

I'm sorry, I don't understand what you're getting at. Ubuntu is compiled already and so are all of the applications you get from the repositories. It's not like Gentoo, you don't have to compile anything yourself.

---

### Post by chadmichael on 2006-08-11
I'm not really interested in ubunut and whether it uses gcc, I just wondered about that.  

However, I'm interested in the manner in which the ubunut system, through the package manager, installs gcc to the system.  Some similar types of tools get deployed with a soft link out of the usr/bin directory.  For gcc, it didn't do this.  I found a gcc-4.0 there, but it seems like it should have made a gcc soft link to this version of gcc, to make it compatible with scripts that just invoke 'gcc'.

---

### Post by dusu on 2006-08-11
Well that's what it does, or at least usually !
In my /usr/bin, here's what I have :
lrwxrwxrwx  1 root root     7 2006-03-24 16:18 gcc -> gcc-4.0
-rwxr-xr-x  1 root root 89208 2005-10-01 16:16 gcc-4.0

I don't know why it's not the same on your install...

---

### Post by taurus on 2006-08-11
Open a terminal, Applications -> Accessories -> Terminal, and see what does it say when you type in this command?

```

gcc -v

```

---

### Post by MrHorus on 2006-08-11
> **mostwanted said:**
> It's not like Gentoo, you don't have to compile anything yourself.

Yes but maybe he wants to?

At any rate, try installing the build-essentials package and if that doesn't work, try if there is a gcc package but build-essentials should contain it.

For what it's worth there is no such thing as a "graphical version" of gcc - gcc is a command line tool only.

What you probably have is an Integrated Development Environment or "IDE". This provides a nice, enhanced editing environment and will usually contain an inbuilt compiler or hook into an installed on such as gcc.

---

### Post by Brunellus on 2006-08-11
gcc and the other developer tools are NOT installed by default in Ubuntu--it's a security and design issue from what I understand.  

It is, however, trivial to get them:

sudo aptitude install build-essential

they are included on the CD, but not installed.

will get you everything you need.

I don't much mind it.  users who never use the compiler are freed from the potential security hazard:  why have a package you won't use?  Users who need the compiler can easily get to it.

---

### Post by chadmichael on 2006-08-11
As I said, 'gcc' is not on the path and doesn't exist on the system, as far as I could determine through locate, and manually checking /usr/bin, et. al.

---

### Post by chadmichael on 2006-08-11
Thanks for the info, everyone.  I think I'll check out the build-essentials package.  I suppose this contains general development tools.  What documentation is available that would contain such an important detail as this?  Also, is this a debian convention that has trickled down, or ubuntu's own convention?

---

### Post by Brunellus on 2006-08-11
it's an ubuntu convention.  I believe the wiki mentions it somewhere, and most howtos that involve a compilation step involve the installation of the build-essentials package.

the rationale:  those who don't need build-essentials don't know it exists.  Those who do generally will be able to get it easily.

---

