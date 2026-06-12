---
title: "Hmmmm...How can I get to Ubuntu GUI after a fresh install?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Sliphorn on 2007-06-22
Hey there,

Total neophyte here.  I have a HP DV9000 laptop upon which I'm trying to install Ubuntu.  I think I've installed it, but have never got as far as a GUI resembling any screenshots I've seen.  I'm happy to learn about the command line and all of that good stuff, but I suppose I need confirmation that something hasn't gone terribly, terribly wrong.  Here are a few details that might help:

1. Immediately upon starting the machine, I get a choice of operating systems.  I get:
   a. Ubuntu, kernel 2.6.20-15-server
   b. Ubuntu, kernel 2.6.20-15-server (recovery mode)
   c. Ubuntu, memtest86+
   d. Other operating systems: Microsoft Windows XP Professional

That is fine, I think.  So I select option a: I get a little error about failing to allocate mem resource...is this terrible?  Because I still get to a login prompt.  It accepts both my username and password.  I get a disclaimer about how Ubuntu comes with absolutely NO WARRANTY, etc.  Got it.

Finally, I get to a prompt which says:

SLIPHORN@UBUNTU:~$ _

the above underscore symbolizes a blinking cursor.  What now?  I have typed "help" and some other little things, but essentially got nowhere.  What's the next step?

If it changes anything, The laptop has a wireless connection which wasn't properly detected/set up during installation.

Any help would be swell, Isabel, swell.](*,)

---

### Post by diatribe on 2007-06-22
you installed the server edition which doesn't come with a gui, use

sudo apt-get install ubuntu-deksktop

and you will be cool

---

### Post by Sliphorn on 2007-06-22
Whoa, really?  I was planning on installing this during a server build.  I guess I'm not ready for that yet.  Thanks for the heads-up!

---

