---
title: "Problem with /etc/sudoers syntax"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by steve.horsley on 2006-05-11
I can't get sudoers to let me use a command with no password. Can anynoe help me with the syntax, please.

I am trying to allow user steve to be able to use /usr/local/bin/myprog without entering a password (it needs calling from a script). I have tried this:

> steve   ALL = NOPASSWD: /usr/local/bin/myprog

but it still prompts me for a password when I type
**sudo /usr/local/bin/myprog**

I really can't make head nor tail of the convoluted man page, and I am beginning to suspect that it's plain wrong anyway.

---

### Post by kabus on 2006-05-11
Syntax looks alright to me. 
Have you logged out and back in before trying if it works ?

---

### Post by steve.horsley on 2006-05-11
Ah - got that sorted thanks. The syntax was right, but the line below about %admin group was overriding my line so I moved my line to below.

Now I have the problem that the program says it can't find the X server. There is some kind of difference between running it sudo and entering the password, and running it sudo with nopassed. 

I am beginning to think that I will have to use a script that says 
> echo mypassword | sudo -S myprog
although I really don't like doing that.

---

### Post by cgjones on 2006-05-11
What is your program trying to do?

---

### Post by steve.horsley on 2006-05-11
You're not going to like this. 

It's a windows based remote monitoring program running under wine. Everything else we want the box to do is a PITA on Windows but easy on Linux. But thus windows app (runs as a service under windows) is proving tricky.

It has to run privileged so that it can open some low-numbered TCP and UDP service ports.

It also needs to have an X display available because it creates a "window" for inter-process messaging (there are actually 2 processes that use windows messages between them). It doesn't create a visible window, but it crashes under wine anyway if an X server isn't available.

I also need it to start if the machine reboots while unattended - like a service.

I was figuring to have GDM auto-login a low-grade user, launch the wine service and then immediately call the screensaver lock.

---

