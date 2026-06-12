---
title: "My computer starts to work without my permission"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Rome tour on 2007-04-26
Hi to everyone,
it's one month that my PC starts to do things I don't understand by himself,without I touch anything.
I begin to be desesperated.
How can I fix this?
Thank you

---

### Post by justleen on 2007-04-26
what kind things of this does it do on its accord?

---

### Post by Parmenion on 2007-04-26
What is your box actually doing?

---

### Post by Rome tour on 2007-04-26
Hi everybody,
my programs run very slow and a green light is continuous on almost ten times a day.
I try to close the program with ctrl+alt+canc but it says "the prog doesn't answer",try later or sthing like that.I'm getting upset....

---

### Post by eentonig on 2007-04-26
Start by having an open terminal on your desktop and run 'top', this will show you which program is eating your CPU. 

Once you have that identified, you could assign a higer 'nice' value to it, to prevent that process from blocking you to work. I experienced the exact same thing under XP btw.

---

### Post by rillip on 2007-04-26
What green light is on? The HDD LED?  Network adapter light?  Some sort of graphic on your screen?  A pixel on the screen? Something else?

What programs are running slowly?  What program is not responding?

If you're getting a message like that, it's blocking the termination signal.  I don't know how you would do it from a GUI side, but if you go to the terminal you can run sudo kill -9 [process id] or sudo killall -9 [proccess name]

The 9 flag makes it so that the program cannot block the call, and sudo makes it run as root, so there's no possible way to stop the termination.  As an example, kill -9 -1 will force system restart. Sudo kill -9 -1... will probably cause a complete system shut down, or something of the like (maybe leave you at a blank screen, as it's not going to run the shut down steps).

With some more information we might be able to better help

---

