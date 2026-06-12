---
title: "Lagging... Or lack of it."
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by cunawarit on 2006-09-22
OK, I am using Debian not Ubuntu but they are similar enough that the question is still relevant I think.

I want to know why/how Linux seems to be so, reactive when compared to Windows? I use Windows XP on, a Celeron D 2.53 GHz with one GB of RAM and Windows 2000 on a Pentium 4 2.8 GHz with 1.5 GB of RAM. And sometimes they lag and become unresponsive whilst some program does something.

I’ve noticed that Debian doesn’t do this, even on the Celeron 700 with 120 MB of RAM that I’m using! When some program is doing something the machine remains responsive, ALWAYS (so far anyway)!

Why? What is Windows doing wrong and what is Linux doing right? Is this something that Vista improves on? 

PS: I also use Windows 2003 Server and I haven’t noticed that, admittedly the machines I use are two CPU Xeon machines worth as much as a car, so I wouldn’t expect them to lag.

---

### Post by MrHorus on 2006-09-22
Because Windows is a resource hog whereas Linux is designed to make the most of whatever hardware there is.

---

### Post by Lord Illidan on 2006-09-22
I think the faster the hardware, the more advantage Linux takes from it. My dual core cpu is now feeling really really fast with Linux while others report slowness in Windows..

---

### Post by Leeghoofd on 2006-09-22
I've had lagging on my ubuntu laptop. Ofcourse I might need to add to this statement that this lagging occurs on a 5 year old laptop running all kinds of mediacrap which would have locked and probably crashed a Windows configuration....:D

---

### Post by Indras on 2006-09-22
This is also true of Macintosh systems.  I believe it has to do with how Windows assigns processor priority.  It allows programs to take greater priority than the operating system, or simply doesn't preserve enough resources to manage itself when confronted with a heavy task.  This has pretty much been true of all Microsoft OSes, even going back to MS-DOS.

It was definitely a trait I don't miss.  I can't tell you how many times I had a program stuck in a loop and cause the machine to lock up, forcing me to hard reset the computer.  A badly written or malicious program simply shouldn't have that kind of power.  Period.

---

### Post by cunawarit on 2006-09-22
> **MrHorus said:**
> Because Windows is a resource hog whereas Linux is designed to make the most of whatever hardware there is.

That’s doesn’t tell me much, most of the time with Windows the system idle process is around 90 odd % mark. Yet something happens sometimes when another process all of a sudden grabs 98% of the CPU thusly the OS not responding to mouse clicks or keyboard presses timely. Is there some reason in Windows why processes are allowed to do this? What does Linux do differently that this doesn’t happen? 

I use fluxbox and some programs like Firefox take a long time to load, however, as the program is loading I can use an xterminal and access the fluxbox menus without any delay. On Windows on a similar situation other things would slow down. 

It appears to me that Linux is better at multitasking, nothing to do with Windows being bloatware or a hog etc.... What does Linux do differently to Windows that no process seems to take all the CPU time at the expense of everything else? 

This is not a question about overall speed, I have no issues with not being able to run two bazillion programs with Windows, or it being slow overall. It is an issue of responsiveness to user input when the CPU is under high load.

---

### Post by cunawarit on 2006-09-22
> **Indras said:**
> This is also true of Macintosh systems.  I believe it has to do with how Windows assigns processor priority.  It allows programs to take greater priority than the operating system, or simply doesn't preserve enough resources to manage itself when confronted with a heavy task.  This has pretty much been true of all Microsoft OSes, even going back to MS-DOS.

Thank you :)

I wrote the above comment as you posted this!

Yeah, I figured something like that was going on. So I take it then that Linux limits how many resources a certain process can take then. Any idea how this is decided?

---

### Post by Indras on 2006-09-22
> **cunawarit said:**
> Thank you :)

I wrote the above comment as you posted this!

Yeah, I figured something like that was going on. So I take it then that Linux limits how many resources a certain process can take then. Any idea how this is decided?

Whenever you press a key on the keyboard or move the mouse, it sends an interrupt to the processor (via an IRQ number) and it puts whatever current task it is running on hold and handles the interrupt.  If it receives multiple interrupts, it handles them in numerical order.  The keyboard is given an interrupt of one, so it should be nearly the highest priority (the system timer is zero).

However, just because the operating system received the keyboard or mouse movement doesn't necessarily mean that the interface updates to show it.

Or, more likely, it only checks the IRQs whenever the processor gets free time, which is why when the processor really bogs down, you can type a whole line of characters before the first one appears, and then suddenly they all pop into existence at once.  The keyboard buffer can store up to 100 characters by default in Windows NT-based systems (XP & 2000 too), so whenever it gets around to checking it, it will dump to the screen all at once.

Linux, on the other hand, seems to check the keyboard buffer nearly constantly, or allows the processor interrupt to directly interrupt the kernel so it processes with each keystroke.  You'd have to ask a developer for deeper info, I'm just making guesses from the standpoint of a long-term computer user.

---

### Post by maaronB on 2006-09-22
> **cunawarit said:**
> Thank you :)

I wrote the above comment as you posted this!

Yeah, I figured something like that was going on. So I take it then that Linux limits how many resources a certain process can take then. Any idea how this is decided?

I really don't know much about Windows but, I know that on Linux every active process is given a "nice" attribute.  This determines how often it gets sent to the processor.  If a process tries to take to much of the system resources it gets its nice value raised causing it to get called less often.  
Read More: [http://www.samspublishing.com/articles/article.asp?p=101760&rl=1](http://www.samspublishing.com/articles/article.asp?p=101760&rl=1) 

With things like this it is important to remember that Linux decends from UNIX it was origanilly designed for multiuser/multiprocess secure network systems and has been being streamlined to do that for the last three decades.  Only in the last few years has it been trying to become a user friendly desktop.

With Windows the opposite applies.  It is built to be user friendly and easy.  And only in the last few years has it multiprocess functunality been built into it.

---

### Post by empcrono on 2006-09-22
yeah agree that windows does those things but the more i learn the more usr friendly froma computer usr stand point... linux is more usr friendly

---

### Post by maaronB on 2006-09-22
> **empcrono said:**
> yeah agree that windows does those things but the more i learn the more usr friendly froma computer usr stand point... linux is more usr friendly

Agreed Linux has in fact become very user friendly, and truthfully Windows has made great progress in the fields of security and efficency.  They are both moving towards the same point, they are just coming about it from opposite sides.

---

### Post by Brunellus on 2006-09-23
> **maaronB said:**
> Agreed Linux has in fact become very user friendly, and truthfully Windows has made great progress in the fields of security and efficency.  They are both moving towards the same point, they are just coming about it from opposite sides.
Except that Windows is still nonfree software.  When they reach a point of indifference, Linux becomes technically superior, because users are free to use it.

---

