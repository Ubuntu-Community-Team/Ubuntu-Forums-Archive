---
title: "CPU and RAM Question"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by boywondr16 on 2006-09-21
I know this question is going to come off as strange to those who spend more time working in Linux, but my curiousity has gotten the best of me.

I'm running Dapper on a Pentium III, 857 MHz with 512 MB of RAM.  When I am doing any heavy process, such as using Avidemux to re-encode a movie, the CPU runs at 100%, but the memory doesn't budge very much.

Is this normal?  Is the computer not accessing the memory correctly?

---

### Post by kidders on 2006-09-21
Hi there,

What do you mean by "budge" exactly? If you mean that the amount of free RAM doesn't tend to leap around like crazy, then that's quite normal ... at least on properly-written operating systems :-)

On most OSs, you can't generally use the amount of allocated/unallocated RAM as a useful indicator for anything.

---

### Post by boywondr16 on 2006-09-22
Given that my point of reference is the specific OS you're mentioning, then my question doesn't seem so dumb now.

However, it then brings me to the next conundrum: why does avidemux keep crashing, giving me memory errors, when the system is running at about 1/3 of the RAM, but full CPU?

---

### Post by Brunellus on 2006-09-22
> **boywondr16 said:**
> Given that my point of reference is the specific OS you're mentioning, then my question doesn't seem so dumb now.

However, it then brings me to the next conundrum: why does avidemux keep crashing, giving me memory errors, when the system is running at about 1/3 of the RAM, but full CPU?
either a) bad RAM or b) a program bug?

---

### Post by kidcharles on 2006-09-22
Transcoding video is one of those extremely CPU intensive things, but it isn't necessarily a RAM hog. The program might work with little chunks of the data at a time, and therefore doesn't need a whole bunch of RAM, depending on how the program is written. I'd bet if you are getting memory errors when using this particular program and not when using others, that the code is buggy. *dodges heads of lettuce and tomatoes thrown by coders of avidemux*

---

### Post by reclusivemonkey on 2006-09-23
> **boywondr16 said:**
> Given that my point of reference is the specific OS you're mentioning, then my question doesn't seem so dumb now.

However, it then brings me to the next conundrum: why does avidemux keep crashing, giving me memory errors, when the system is running at about 1/3 of the RAM, but full CPU?

Try mencoder to re-encode videos. If you still get errors/crashes then use memtest in the grub menu to test your memory.

---

### Post by boywondr16 on 2006-09-24
Well one chunk of my newly purchased memory is bad.  So bad that I nearly burned my fingers on it after running memtest...

Sheesh.  

Thanks for the help.

---

