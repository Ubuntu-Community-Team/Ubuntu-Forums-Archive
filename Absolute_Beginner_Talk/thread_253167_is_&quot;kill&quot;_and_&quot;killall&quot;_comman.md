---
title: "is &quot;kill&quot; and &quot;killall&quot; command bad for system?"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by styracosaurus on 2006-09-07
Hi, I have been using Linux for a while, and Ubuntu for about a year, but I still consider myself a relatively green Linux user even though I use it for all my university work. In one of my CS classes today, a TA said that you should not use "kill" to end a process because it is "really bad for your system." I was too embarrassed to admit it, but I have used it several times when programs are not responding at all and I can't close it any other way. The person who introduced me to Linux told me this is like ctrl-alt-del in Windows when a program is not working.

So what's the story? If a GUI program is non responsive how should you end it nicely? I was told by my friend to use "ps -A" and look up the id and then use "kill <id #>" or use "killall <name>". Am I messing up my system?

I don't know if this is the right part of the forum either, or if it has been addressed before. As you can see it is my first post.

---

### Post by Seine on 2006-09-07
Good question. I use it often at work on Solaris without consequence. Now I too wonder if its OK!

---

### Post by aysiu on 2006-09-07
Why don't you ask your TA on what basis she's saying that and what the exact consequences are of using the *killall* command too much are?

---

### Post by bodhi.zazen on 2006-09-08
> **aysiu said:**
> Why don't you ask your TA on what basis she's saying that and what the exact consequences are of using the *killall* command too much are?

Better, have her post the answer here..... Just tell her you found a discussion on the web....

---

### Post by DSn0wMan on 2006-09-08
It really depends on how you use it. Typically you only kill processes that are not terminating normally. If for some reason you just like to use kill instead of bringing down a process gracefully then thats probably not good.

For example: If I just kill all my oracle processes it may be difficult to bring the database back up. On the other hand when firefox hangs I just kill it. No choice no problem.

---

### Post by Seine on 2006-09-08
> **DSn0wMan said:**
> It really depends on how you use it. Typically you only kill processes that are not terminating normally. If for some reason you just like to use kill instead of bringing down a process gracefully then thats probably not good.

That sounds reasonable if you're talking about the *KILL* signal, which will perform no cleanup and leave all sorts of resources hanging. But a standard *kill* uses the *TERM* signal. Isn't this just like nicely asking the process to shut down?

---

### Post by IYY on 2006-09-08
It depends on the individual applications. Some may not handle being "killed" gracefully.

---

### Post by Seine on 2006-09-08
If I bring a process to the foreground and CTRL-C. Is that any better than *kill*?

---

### Post by amo-ej1 on 2006-09-08
Yeah, ctrl+c sends a signal (15 SIGTRM) to the application that can be trapped by the application, in the signal handler there 'can' be code to cleanly close all open files and terminate properly. Will a 'kill -9' sends a signal (SIGKILL) that cannot by trapped. A regular kill also sends a SIGTERM so ctrl+c and kill are equivalent but ctrl+c and kill -9 are not.

As a rule i would say that if you have an enterprise ciritical application you'd better shut it down the 'right' way always, just in case in any other way you can kill all you want.

It is the responsibility of the application developer to handle SIGTERM signals in a decent way (except the signals that cannot be trapped)

---

### Post by Lakefall on 2006-09-08
> **styracosaurus said:**
> In one of my CS classes today, a TA said that you should not use "kill" to end a process because it is "really bad for your system."
It's not "bad for your system" unless you are doing it to some critical system process running as root. Killing system processes with direct access to hardware like the X server can cause trouble, but probably nothing a reboot doesn't fix. As long as you are not killing (important) things running as root, you should be pretty safe. If the application you killed gets confused and refuses to run again (or something), it isn't very well programmed and it probably was just a matter of time. Rename or edit it's (hidden) configuration files in your home directory and try again.

> So what's the story? If a GUI program is non responsive how should you end it nicely? I was told by my friend to use "ps -A" and look up the id and then use "kill <id #>" or use "killall <name>".
At that point, it really isn't possible to be much nicer than that. First try "kill <PID>". If that doesn't work do "kill -9 <PID>". The latter is less nice, but it's guaranteed to work.

---

### Post by az on 2006-09-08
> **styracosaurus said:**
> a TA said that you should not use "kill" to end a process because it is "really bad for your system." 

As a rule, that is completely false.  What are you supposed to do if you made a mistake and you wrote an endless loop?  Reboot?

There is nothing inherently dammaging about killing a process.  As stated, it depends what that process is doing, but then again, if your process has started to fill up your harddrive in an endless loop, you had better kill it before you run out of disk space and crash your system.

---

