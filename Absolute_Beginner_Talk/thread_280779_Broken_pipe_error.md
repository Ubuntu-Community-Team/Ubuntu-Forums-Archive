---
title: "Broken pipe error"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by MarcinM on 2006-10-20
Hi folks,

First off, I tried to follow all of the self-help links and found little. Google turned me into very specific issues or for-pay sites like experts exchange etc. So...I'm here :)

Here's the sitrep:

I've been running my Ubuntu box for a while. I switched the initial Gnome to KDE (seems to run faster on my ancient laptop), I put PHP, mySQL and Apache2 on it, all runs great. So I get ambitious.

I run Dominions 3 ([www.shrapnelgames.com](www.shrapnelgames.com)) on it. All runs well, I write a little parser to display the game status, and use a shell script to email the players once a turn is complete. All seems fine until all of a sudden I'm getting:

send: Broken Pipe

errors in my output. There doesn't appear to be any other info about this. 

Help! I have no idea what this even means. Where do I go to look for an error log, or more detail on this? What's the most likely cause of this? Insufficient ram, badly configured network...I mean 'send: broken pipe' is really a broken error message :D It doesn't even give me a hint as to where to start looking.

Thanks in advance for any help :)

M.](*,)

---

### Post by Arndt on 2006-10-20
> **MarcinM said:**
> Hi folks,

First off, I tried to follow all of the self-help links and found little. Google turned me into very specific issues or for-pay sites like experts exchange etc. So...I'm here :)

Here's the sitrep:

I've been running my Ubuntu box for a while. I switched the initial Gnome to KDE (seems to run faster on my ancient laptop), I put PHP, mySQL and Apache2 on it, all runs great. So I get ambitious.

I run Dominions 3 ([www.shrapnelgames.com](www.shrapnelgames.com)) on it. All runs well, I write a little parser to display the game status, and use a shell script to email the players once a turn is complete. All seems fine until all of a sudden I'm getting:

send: Broken Pipe

errors in my output. There doesn't appear to be any other info about this. 

Help! I have no idea what this even means. Where do I go to look for an error log, or more detail on this? What's the most likely cause of this? Insufficient ram, badly configured network...I mean 'send: broken pipe' is really a broken error message :D It doesn't even give me a hint as to where to start looking.

Thanks in advance for any help :)

M.](*,)

"Broken pipe" usually means that one process A was in the process of writing data to process B through a pipe, and B closed its end of the pipe before A was done writing. Often it is because B crashed, or was simply done with its job and didn't need more input, but A wasn't prepared for that situation.

A pipe is what you get when you chain several processes like this:

```
grep Customer *.data | wc -l
```

The '|' creates a pipe. You can of course create them programmatically from within a program too. The same condition may occur when writing to sockets.  Actually, that may be what your programs are doing: "send" is a socket system call. I agree that the error message might have included at least the name of the program.

"man 2 write" says this about EPIPE:

 >      EPIPE  fd is connected to a pipe or socket whose reading end is closed.
              When this happens the writing process will also receive  a  SIG&#8208;
              PIPE  signal.  (Thus, the write return value is seen only if the
              program catches, blocks or ignores this signal.)


---

