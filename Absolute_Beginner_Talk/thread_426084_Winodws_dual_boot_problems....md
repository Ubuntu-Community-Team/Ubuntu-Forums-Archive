---
title: "Winodws dual boot problems..."
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by DrunkPeanut on 2007-04-28
I'd like to start by saying I'm aware of the many, many threads addressing this problem ("hal.dll missing" error message is displayed whenever I attempt to boot into Windows).
However, they all state that you need "ntfstools"- which I am unable to install. The "make" and "make install" commands do not respond, and the './configure" command informs me that "C compiler cannot create executables".

So what I need is either another way to fix the boot or a way to install ntfstools.
I have to tell you, Linux is getting more frustrating by the minute... The people here are great though :)
Thanks in advance.


Never mind, I just saw the answer in an unrelated thread ("sudo apt-get install build-essential" in the terminal).

---

### Post by freebird54 on 2007-04-28
Don't know about ntfstools, but the Super grub disk should handle it for you.  Or, there are various Windows tools that can work too.  If you have a 'startup disk' from any version of Windows up to XP (3.0 and newer) a boot to the DOS commandline will allow you to

```
fdisk /mbr
```

or from an XP install disk, go to Recovery console, and run 

```
fixmbr
```

THat's a couple of extra options anyway..

Hope it helps.

---

### Post by Sef on 2007-04-28
> ("sudo apt-get install build-essential" in the terminal).

In the terminal, type this first:

```
sudo aptitude update
```

then type

```
sudo aptitude install build-essential
```

Note: you can use apt-get instead of aptitude if you prefer.

---

