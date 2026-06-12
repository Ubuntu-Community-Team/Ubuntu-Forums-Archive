---
title: "Linux troubleshooting questions"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by kunalbelnekar on 2007-01-29
Hi,

I am looking to pursue a career in Linux System Administration and need some guidance. Could some System Administrators help me out here please !!

I have a few questions about Linux systems running slow. What could be the possible reasons of the system running slow ? I searched the web and found out that system being slow can be because of the Memory being low, or the HDD getting full or unwanted programs running.Are there any other (general or common) reasons apart from these ?

Can someone please tell me how to go about troubleshooting these problems. How would you go about interpreting the common commands like iostat, vmstat, top.What I mean is how would you figure out a problem when you look at the fields of these commands. Also are there any other commands that are used for troubleshooting a Linux system apart from these and how 

Sorry for asking so many questions...but the internet didnt really help me here.

Thanks

---

### Post by istrebitjel on 2007-01-29
I'm no sysadmin, but I can give you a vague idea about top.

First: If you have any question about a specific command on the linux command line, ask the manual, by typing
*man top*
In this case you can find the description of any of the fields listed (search by hitting / and entering the keyword, e.g. PID followed by Enter, press n for the next find).

Now look at this example from my system:
```
top - 17:19:44 up 47 min,  3 users,  load average: 3.62, 3.42, 2.96
Tasks: 137 total,   2 running, 134 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.7%us, 11.3%sy,  0.0%ni,  0.0%id, 83.7%wa,  0.7%hi,  3.7%si,  0.0%st
Mem:   1555008k total,  1253796k used,   301212k free,   777876k buffers
Swap:   835340k total,        0k used,   835340k free,   164316k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
11437 root      18   0  9932 9556 6228 R  7.0  0.6   2:23.12 ntfsresize         
12892 root      15   0     0    0    0 D  0.7  0.0   0:00.02 pdflush            
 4066 root      15   0 40808  28m 9116 S  0.3  1.9   0:31.23 Xorg               
 5196 marco     15   0 54152  15m 9648 S  0.3  1.0   0:09.96 gnome-terminal
```
The first line tells you the uptime (since your last boot), how many users are logged in and the load averages for the past 1, 5, and 15 minutes. (if you only want that info you can run uptime)
The next line is Tasks: If you have a lot of running processes that is the prime reason for slow system speed.
The next line Cpu breaks the current system load down by who is causing the load, user, system, etc (see [link]("http://small.dropbear.id.au/docs/linuxload.html") for more).
Now for memory: As you already said, low memory is often the cause of a slow system. When linux runs out of main memory it has to swap, i.e., put something currently in memory onto the swap partition and that takes time. You can tell that's the case by looking the free memory (I still have 300MB, so I'm good) and at the next line, the swap space - I have 0k used, so nothing has been swapped out.

Now follows the list of currently running tasks. You want to mainly look at %CPU %MEM  TIME+ - they tell you how much cpu and memory (%) your task uses and how much cpu time it used over time. So a high number (many minutes) indicates a process eating all you cpu. 

Maybe you can do without that program or you even need to kill it.

Hope that gives you at least one tool to look into your problem.

---

### Post by sardion on 2007-01-29
In my experience, the biggest reason for linux becoming slow is from the use of swap space.  Basically, when you run out of real memory, linux uses swap (known as virtual memory in other OSes), which is a prt of the disk that acts like memory.  Of course, a disk is much much slower than memory.

The way to check is to use the free command (or vmstat if you prefer).
If the swap row has some used then that's likely the problem.

The biggest issues with linux servers, at least the ones I've admined, are 1) X11 (though IMHO that should *never* be on a production server), 2) mailscanner (or similar),  3) sheer volume of IMAP/IMAPS/POP/POPS/HTTP/HTTPS and 4) PHP.

X11 eats memory and processor time like nothing else.  Mailscanner (or naything that scans email on its way in for viruses etc. needs a lot of resources if there's a lot of email, especially for the virus scanning into archives etc).  PHP is also nasty as far as resource usage.

Between top and free (use top to check for CPU time as mentioned above), you should be able to tel lwhat's slowing you down.

---

### Post by seuaniu on 2007-01-29
just a really quick suggestion:

Check out htop.  Its a neat little top clone with colors :)

---

### Post by louieb on 2007-01-29
> **seuaniu said:**
> 
Check out htop.  Its a neat little top clone with colors :)
I just installed it. very nice. Thanks

---

