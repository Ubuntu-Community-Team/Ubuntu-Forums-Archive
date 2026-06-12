---
title: "How do I list files with same size?"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-10-08
Sometimes I find duplicate files but under different names.  Is there a way I can list files with matching size without entering a specific size?

---

### Post by gborzi on 2006-10-08
To find duplicate files you can use fdupes. From *man fdupes*:
> FDUPES(1)                                                            FDUPES(1)

NAME
       fdupes - finds duplicate files in a given set of directories

SYNOPSIS
       fdupes [ options ] DIRECTORY ...

DESCRIPTION
       Searches  the  given  path for duplicate files. Such files are found by
       comparing file sizes and MD5 signatures,  followed  by  a  byte-by-byte
       comparison.

---

### Post by tux101 on 2006-10-09
The first time I ran fdupes, it said something about "Building <something...>" before my screenname in the console.  And it just stayed that way until I canceled.  I also noticed that it accessed the Internet to download something.  What was it trying to download?!

The fdupes seems to be working now.  But what was it trying to download before when I first 2 or 3 times?

Also, when it scans for duplicates does it make a (temporary) file somewhere and keep the data there?  If so, where is this file?  Or does it pipe the data on screen?

---

### Post by gborzi on 2006-10-09
> **tux101 said:**
> The first time I ran fdupes, it said something about "Building <something...>" before my screenname in the console.  And it just stayed that way until I canceled.  I also noticed that it accessed the Internet to download something.  What was it trying to download?!

Who knows ? I have used it while disconnected. On my system it prints "Building file list" followed by a rotating line (i.e. the -\|/ sequence), and after a few seconds it prints "Progress [n/ntot] x%" where n is the number of files scanned, ntot the total number to be scanned and x the percentage.

> **tux101 said:**
> 
The fdupes seems to be working now.  But what was it trying to download before when I first 2 or 3 times?

Also, when it scans for duplicates does it make a (temporary) file somewhere and keep the data there?  If so, where is this file?  Or does it pipe the data on screen?

I'm not aware of any temporary file used by fdupes. You can try to look at the source code of this program. Do you think it is possible that your system was compromised by some attacker that changed the fdupes binary ?

---

### Post by tux101 on 2006-10-10
And what does it mean if it reads?:
```
Building file list / user@domain ~$
```

And it just stays that way with nothing else happening.  The / is not rotating into -, /, |, \, etc.

---

### Post by gborzi on 2006-10-10
To me, it seems that fdupes crashes, because when it prints the "/" this is not followed by a newline. So, after the crash, the usual prompt is printed on the same line.

---

### Post by tux101 on 2006-10-10
Any idea why it might crash?

I did not know things can crash in Linux.

---

### Post by gborzi on 2006-10-11
> **tux101 said:**
> Any idea why it might crash?
Frankly speaking, no.
> **tux101 said:**
> 
I did not know things can crash in Linux.
They can. However, you can download the source code, compile it with debugging information, debug it, and hopefully fix the problem.

---

