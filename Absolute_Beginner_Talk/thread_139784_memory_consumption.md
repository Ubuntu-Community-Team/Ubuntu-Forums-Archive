---
title: "memory consumption"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by bjrnfrdnnd on 2006-03-04
Hello, 
I am running kubuntu breezy badger on a samsung x20 xvm 1600II with 2 Gigs of Ram. 
Right now, I am running readcd in order to read a damaged dvd. 
The memory consumption, as displayed by the "top" program, is the following:

top - 02:00:59 up 3 days, 22:49,  2 users,  load average: 5.58, 4.66, 4.62
Tasks: 136 total,   1 running, 135 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.6% us,  3.7% sy,  0.0% ni,  0.0% id, 84.7% wa,  0.0% hi,  0.0% si
Mem:   2075700k total,  2021884k used,    53816k free,    74324k buffers
Swap:  2144668k total,      892k used,  2143776k free,  1451600k cached

Which seams an awful lot. 
The readcd program itself does not consume any noticeable amount of memory, 
and in short, I am not able to detect which kind of process is causing this memory consumption. 
Likewise for cpu usage. According to top, a lot of cpu power goes into a thing called wa (84.7% above), I was not able to find out what that is. 
No process seems to consume a lot of cpu. 
So I am a bit lost here. What is causing my machine to work so heavily, and can I change the behavior? I already reniced the readcd process to 19. 
Help appreciated!

---

### Post by pestilence4hr on 2006-03-04
[http://ubuntuforums.org/showpost.php?p=792881&postcount=2](http://ubuntuforums.org/showpost.php?p=792881&postcount=2)

You need to look at the output of "free", and pay particular attention to the second line, that is your actual memory usage (from an application POV).

Also I don't know what "wa" is.  Is your terminal truncating the output of "top"?  Maximize the terminal, and type "ps aux |grep wa", and see what that says.

---

### Post by bjrnfrdnnd on 2006-03-04
Thanks for the reply. 

free -m
             total       used       free     shared    buffers     cached
Mem:          2027       1973         53          0         82       1336
-/+ buffers/cache:        554       1472
Swap:         2094          0       2093

It seems that the memory is in use, then? It seems to go into the disk cache, 
no wonder, as I am using readcd. So much for the memory. 

As for the "wa" thing: it appears in the
"Cpu" Line, third line of the "top" output. It is not a truncated process name or something, but a general category of cpu power consumption, like "user", "system", 
and so on. Only I do not know what it is for :( .

Here once mor the top - output, look at the third line:

top - 03:03:14 up 3 days, 23:51,  2 users,  load average: 4.12, 4.55, 5.70
Tasks: 133 total,   1 running, 132 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.6% us,  2.7% sy,  0.0% ni,  0.0% id, 80.7% wa,  0.0% hi,  0.0% si
Mem:   2075700k total,  2021016k used,    54684k free,    84896k buffers
Swap:  2144668k total,      892k used,  2143776k free,  1362656k cached

        
The question is: renicing the readcd process didn't prevent the system to really 
slow down. Lots of memory goes into the disk caching. Lots of cpu power goes into the "wa" thing, whatever that is. What can I do to regain a better responsiveness? Can I limit the part of the memory used for the disk cache, which, 
I suppose, is the main factor in slowing down the machine? And where does the
cpu power go?

---

### Post by TrendyDark on 2006-03-04
Wait, you're saying that you're reading a damaged DVD, maybe it's just moving a large amount of information from the DVD to memory for the time being. I don't really use memory-intensive programs, so I'm just guessing, but that would make sense.

---

### Post by bjrnfrdnnd on 2006-03-04
Well no, sadly enough it is not. Right now, I am in the damaged part. 
The amount of data which is read can be completely neglected compared to 
the first part of the dvd, where the system did not slow down significantly. 
I have the followin vmstat output:
procs -----------memory---------- ---swap-- -----io---- --system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in    cs us sy id wa
 0  1    892  66884  85772 1340844    0    0   106   122   94    82  6  1 79 14

Last part of the cpu part is called iowait, the system waiting for  i/o events or something like that. I assume that this corresponds to the "wa" thing in the top
output, so here is an obvious contradiction between both outputs. 
I gather the situation is the following: The computer is continuously hitting bad sectors, and for one reason or the other, even though it finds at the best a few kilobytes per second to be transferren, it puts 1.3 GB of RAM in the disk cache. I still can't understand that! At the same time, it is always listening, with huge effort, to  the dvd giving it some data. 
What I do not understand, is, why this literally cripples the system. As I said, I reniced the readcd program, and where is the necessity to take more than 1 Gig of Ram to transfer so little memory? 
The bigger question is then, as this reading of the damaged dvd is really slow, 
how can I put it in the background in a way that does not cripple the system?

---

### Post by az on 2006-03-04
The linux kernel uses memory agressively - any memory that is not in use is wasted.  Don't worry!  If something needs memory with a higher priority, the unused consumed memory will be flushed.


So, linux uses memory to increase performance.  It will use up all the memory it can, as soon as it can.  This is normal and desired.

---

### Post by bjrnfrdnnd on 2006-03-04
Thanks for the reply. 
It is not the memory consumption I am worried about. 
I would be perfectly ok if it consumes all the memory it wants. 
I am worried that my computer is literally crippled while trying to read this damaged 
dvd, and I am not able to put it nicely in the background without slowing down the
rest of my applications. And especially its responsiveness. Sometimes it literally stalls. 
I do only suspect that the memory consumption of this disk cache is one big slower-down of my system, so I would like to know how to stop that. As for this "wa" thing which is going on, I would also like to know how I could tell my system to be a little bit more moderate, such that it keeps responding to my interactive demands in the way I am used to it.

---

