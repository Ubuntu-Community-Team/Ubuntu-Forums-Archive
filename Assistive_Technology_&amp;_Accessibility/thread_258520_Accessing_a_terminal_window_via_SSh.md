---
title: "Accessing a terminal window via SSh"
date: 2006-09-16
forum: Assistive Technology &amp; Accessibility
---

### Post by tobaccoman on 2006-09-16
Good morning!

First of all please note that I'm a total beginner!

I have an application that I launch via command line (./xyz) and which gives me the results in the same terminal window

This application should and is running continuously.

Now I want to see via an SSH session whether it is working ok (from a remote PC) and restart it if required

Which command line should I type in SSH to see the same terminal window?

Thanks!

Daniel

---

### Post by mitch.c on 2006-09-16
> **tobaccoman said:**
> Which command line should I type in SSH to see the same terminal window?

If you just want to know if the process is running you could use ps to check the process name:
```
ps ax | grep programname
```

> **tobaccoman said:**
> 
Now I want to see via an SSH session whether it is working ok (from a remote PC) and restart it if required
If you need to actually the program and it's output, I would suggest screen. It's a "terminal multiplexer" that will let you actually attach to a current session right where you left off. It is one of my "can't live without" programs. It is already installed in ubuntu. Here's a few handy commands:
```
screen #starts new session
screen -dRR #starts screen and attaches to already running session
<Ctrl>a c #creates new window... like a session within a session
<Ctrl>a p #switch to previous window
<Ctrl>a d #detach session... return to terminal, screen keeps running
```
I was a Gentoo user and used to start compiles in a screen window, monitor the window for silence <Ctrl>a _ (that way I knew when it was done), all while working in another screen window. It's the coolest thing.

Here's a link to a pretty good intro/tutorial: [http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

Try it!

---

### Post by kidders on 2006-09-16
Hi Daniel,

Afaik that is (quite deliberately) impossible to do. There are some more indirect solutions though.

1. Use the **ps** command to see if your utility is still running.

2. Install **screen**, a tool that, among other things, allows you to detach and re-attach terminals.

Edit: Whoops! Mitch's post is far nicer anyhow!

---

