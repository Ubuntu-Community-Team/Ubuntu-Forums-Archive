---
title: "Can't get GUI desktop with xvncviewer, only shell"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by 01000111 on 2008-02-25
Greetings all,
Here's my setup:

Machine A: Xubuntu 7.10, 2 monitors each running 1280x1024
Machine B: Xubuntu 7.10 AMD64 connected to a HDTV running at 1920x1080

I've got Xeyphr running well (except for a screen size problem), and am now trying to get to the point where I can share a single desktop of Machine B.  

I'm running vnc4server on Machine B and I've gotten xvncviewer to work on Machine A using the command:

xvncviewer tv-pc:1 -FullColourxvncviewer 192.168.1.3:1 -FullColour

but I can't get to the desktop, only the shell.  What am I missing?  I've sifted thru the past 6 months of posts in the forum, but no luck.

TIA

01000111

---

### Post by neurostu on 2008-02-25
This might not be what you're looking for but have you ever tried window forwarding with ssh?

To do it you simply SSH from one machine to the other but add "-X" on the end. Then you can run apps on the 2nd machine but they appear on machine 1!

```

ssh <username>@<machine2> -X

```

---

### Post by 01000111 on 2008-02-25
Thanks, but what I'm looking for is a PCanywhere-type solution.  I want to be able to see and interact with the desktop that the user of Machine B is currently using.

---

