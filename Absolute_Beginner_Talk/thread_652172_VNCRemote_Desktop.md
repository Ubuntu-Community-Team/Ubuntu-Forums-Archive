---
title: "VNC/Remote Desktop"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by sethfc on 2007-12-28
Hey all (super noob question)

So I am familiar with remote desktop and VNC (but only on windows platform).

I was wondering, how does this all work with Ubuntu?  Is VNC built in?

I am in the process of reformatting my parents machine with Ubuntu.  I'd like to be able to VNC to them whenever they need help (from my own Ubuntu machine).  Is there a way to enable this software?  Or sudo apt-get?

I'd also like the ability to connect to my ubuntu box from work, by simply using I.E. or the browser.  Is this possible?  If so, how?

Thanks guys

-Seth

---

### Post by brennydoogles on 2007-12-28
Yes sir!! with apt-get (or Synaptic), you can install vnc-server and vnc-viewer (as well as a few others) try this code to see what is available ```
sudo apt-get install vnc [Tab] [Tab]
``` The first [Tab] will activate the built in autocomplete function, and the second will show you a list of all possible matches (all packages beginning with vnc) . Hope this helped!

---

### Post by eolson on 2007-12-28
I used it for awhile think the command was

sudo apt-get install x11vnc

no sure.  Be sure to at least require a password (a good one) because your machine is wide open.

---

### Post by sethfc on 2007-12-28
For VNC, will it matter if I'm running 64-bit and my folks have the 32-bit ubuntu?

and what about accessing my box just through I.E. or something?

-seth

---

