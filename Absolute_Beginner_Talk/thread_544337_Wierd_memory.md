---
title: "Wierd memory"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by kinngg on 2007-09-06
Hi i was just wondering how come everytime when i run my usual programs my programs would use about 45% of my memory and 45% would be used by cache, but if i keep my laptop on longer my memory usage for programs would become 60% even though the same programs are running, is there something wrong?

---

### Post by abhilash82 on 2007-09-06
What are your system specs? How much space have you allocated for swap?

---

### Post by kinngg on 2007-09-06
memory: 748mb
intel pentium m processor 1.70GHz
and 800mb of swap

---

### Post by kinngg on 2007-09-06
Now its going over the roof, its 70% memory used by programs.. all i have on is my compiz-fusion, with very few effects, amule,skype,pidgin,firefox usually all this would use up maybe 50% most, but now its 70% is it normal? and does so much memory being used make my laptop slow?

---

### Post by kinngg on 2007-09-06
*bump*

---

### Post by Paulmd on 2007-09-06
> **kinngg said:**
> Now its going over the roof, its 70% memory used by programs.. all i have on is my compiz-fusion, with very few effects, amule,skype,pidgin,firefox usually all this would use up maybe 50% most, but now its 70% is it normal? and does so much memory being used make my laptop slow?

It sounds like  a memory leak in one (or more) of the running processes, it it possible to reboot, get a list of allocated memory by process. Then wait a bit until memory allocated gets higher, and so the same thing. Then compare the lists.

---

### Post by Austin_KW on 2007-09-06
Is there actually a problem? Or are you just curious?
When you exit a program, parts of it; libraries etc may stay resident in memory. If you start the same program again it should open up much faster. Try starting openoffice, closing it and restarting it. See how fast it starts the second time.

If you don't have problems starting new programs, then you don't have a problem. The OS will manage the memory as best it can. Free memory does not make a lot of sense when it can be used for something else like making the same program start faster the second time or programs that use the same libraries start faster.

---

### Post by abhilash82 on 2007-09-06
**kinngg: **Can you post the results of running "**top**" when you find your memory getting exhausted? Have you tried the memtest86 program to check for errors in your RAM? Memtest86 is also available when you boot through the Live CD.

---

### Post by dwhitney67 on 2007-09-06
When running applications on a computer, it is most desirable to have all of the applications running from RAM (memory) because it is a lot faster than trying to access data from the HDD.  So ideally, if you are only running a few applications, you want all data associated with those applications to be stored in RAM.

If enough applications are running with the RAM exhausted, any new application that is started, or when an existing application requires more memory (e.g. web browsers), the use of the swap space on the HDD will come into play.

The OS will write data from RAM into the swap space (HDD), thus freeing space in RAM for any other application that may need it.  When this occurs, it is possible to experience latency problems when running applications.

Thus more RAM makes a system merrier.  A lot of software developed today is not written with performance in mind.  Many developers have top-notch systems with the latest hardware and lots of RAM, and they tend to forget about the small guy with a cheapo Pentium II system with 128MB of RAM.  C'est la vie.

-----------------------------------

Everything I say is a lie.

---

