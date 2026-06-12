---
title: "everything is slow"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by bumanie on 2007-08-31
Everything opens up slowly. I looked at system monitior during startup. Something called restricted manna zombie was running 29 processes. What is this? Is it meant to be there? If not, how do I get rid of it?

---

### Post by Dark Hornet on 2007-09-01
I am pretty positive that it is not supposed to be running---try rebooting to get rid of it, if that doesn't work, open up a terminal and type:

top

this will show you a list of all of the running process on your machine.  If you want to kill any of these process, make note of the PID number of the processes you would like to get rid of and just type "control c" (to exit out of "top"), and then type "kill and the PID number...Hope this helps.

PS--if you want more detail, open a terminal, and type "ps -axf" or "ps -af".  This will not only show you the processes running, but the location and path of each process.  This information could be very helpful if the processes you have running are malicious, etc.

---

