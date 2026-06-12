---
title: "Sun Solaris and Linux"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-09-15
I've heard rumors that Sun might be releasing their Solaris code into the GPL or something, so, in effect it could be blended with Linux!  I'm happy because I'm pretty sure that Solaris deals well with multiple processors :) and, although Linux is still way better than windows, it's still no where near where it could be.  For example, anyone with a dual-core probably knows what I'm talking about, but have you noticed that when you do something that requires a lot, or "all" of your processing power, it will only use both cores to ~50 - 60%, or  less often, 1 core to 100 and leave the other only at about 10%?  Well, I'm hoping that if the code is properly blended, programs will be able to take advantage of *all* the processing power available (of course, at such a time, it would be a good idea to provide a feature like windows has to let you choose which cores a process is allowed to use (1, or 2 ,or both, or more...)).

Correct me if I'm wrong on any of this, but if I'm not, than I think this will be good for everyone! :guitar:

---

### Post by jackocleebrown on 2007-09-15
You've seen Nexenta OS right ([http://www.nexenta.org/os](http://www.nexenta.org/os)) ~ Ubuntu with Open Solaris Kernel. Give it a try if you are interested. 
I don't think that this answers your multi thread prayers - the programs running on-top of the kernel need to be written to take advantage of more than one thread at a time, not just the kernel.
You might also be interested in "taskset" (in the software repositories) which allows you to assign processes to specific CPU's ala windows - albeit only from the command line.

Jack.

---

### Post by ryanVickers on 2007-09-15
Actually, I didn't see that! :)  I just heard it somewhere, and I was under the impression that it wasn't out already, but it was going to happen eventually :)

On the topic of multi threading however, I was under the impression that no program can talk directly to hardware in Linux, so, in *theory*, that would mean that it's not up to the program to know how to request full power on both CPU's.  I thought that this would be fairly simple - each program would request "x" amount of CPU power, and it would be up to Linux to use both cores effectively.  If this was the case, then all that would need to be done would be to mix the code to better support
 multiple CPU's, but I guess it's not the case. :(

---

### Post by jackocleebrown on 2007-09-15
You are right about the kernel interfacing to the hardware and the software just talks to the kernel. Programs are controlled as processes that consist of one or more threads (which very simply are like lists of instructions sent to the CPU for execution in turn). The kernel controls which threads go to which cpu but there is no way currently to arbitrarily split a thread over more than one CPU at once.
I'm no expert but the problem is to do with both CPUs accessing the data they need to process the thread - what happens if one processor runs a bit of a program faster that the other (perhaps something else is using processing power) you easily get into the nasty situation where you cannot guarantee that a particular piece of info required for the thread to continue to execute is available. 
You can write a program so that it runs on lots of threads at once each of which can go to a different CPU at the same time but it is up to the program to make sure it can put them and all the data back together in the right way!

Loads of people are working on ways to multithread effectively and there are a number of programs that can already multithread very sucessfully. Lots of work to be done yet though, Watch this space!

Jack.

---

### Post by ryanVickers on 2007-09-27
Interesting.  That's too bad I guess, but it makes sense now :)

---

