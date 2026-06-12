---
title: "c compiler"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by marty13 on 2007-03-26
wanted to install vmware, posted a new thread and got a great response, with a step by step how to. got to the part where it says it needed a C compiler and could not find a "make" file.
i thought that Linux came with its own compiler? the software is not installed because of this.
 I did a HDD search for "Make" and "compiler" came up with way to many variations of both. i am way to new at Linux to know which one to use. what do i do now?
any thoughts?
thanks.

---

### Post by taurus on 2007-03-26
You need to install the build-essential package.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by marty13 on 2007-03-26
well the comands installed a lot of stuff that i don't understand. thanks.
the latest is : "usr/src/linux/include" is not an existing directory so it sits there.
do i have to create one?

---

### Post by compmodder26 on 2007-03-26
You have to install the headers for your existing kernel.  This can be done with this command:

```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by marty13 on 2007-03-26
it now says: itcan not find the package 'uname -r' i tried some variables of it .....ng.

---

### Post by taurus on 2007-03-26
What's the output of this command then?

```
uname -r
```

---

### Post by compmodder26 on 2007-03-26
> **marty13 said:**
> it now says: itcan not find the package 'uname -r' i tried some variables of it .....ng.

If you are using a default Ubuntu kernel, the command I gave you should work.  Note, in the command I'm using backticks and not single quotes.  The backtick key is above the tab key.

---

### Post by marty13 on 2007-03-26
just put the command "uname -r" in and this is the responce; 2.6.15-28-386
did not get your post till i did this post i will try again with the backtick, thanks

---

### Post by compmodder26 on 2007-03-26
You can then change the command I gave you above to this one:

```
sudo apt-get install linux-headers-2.6.15-28-386
```

The `uname -r` part of the previous command was to tell apt-get which headers it should fetch, by having it look at your currently running kernel's version number.

---

### Post by marty13 on 2007-03-26
OK.........looks like it worked. iam at the key install now.
before i go any further, i wanted to say thanks to you guys for helping out a newbe.

---

### Post by compmodder26 on 2007-03-26
No problem at all.  Let us know how it goes.

---

