---
title: "Serious cups problem."
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by sesstreets on 2006-01-14
So after my nightmare trying to share my ubuntu attached printer to my windows xp machine over the network. I thought, hell I give up, so I just attached the hp 1350 to the winxp machine, so then i said "i can just share it from there". So i go to system>administration>printing and i get this:

[IMG]http://img244.imageshack.us/img244/32/untitled3ty.gif[/IMG]

So now what? I tried uninstalling everything that came up in synaptic that had cups in the name :P and still nothing?

What do i do?

YEAH IM A NOOB!

---

### Post by sesstreets on 2006-01-14
O come on...is it that simple that nobodys cool enough to answer it?

---

### Post by AndyCooll on 2006-01-14
Just browsing around the forums I came across this thread:

[http://www.ubuntuforums.org/showthread.php?t=101084]("http://www.ubuntuforums.org/showthread.php?t=101084")

Any use?

:cool:

---

### Post by bscbrit on 2006-01-14
You could always try starting the cups server....?

System -> Administration -> Services

and make sure that cupsys is activated.

---

### Post by sesstreets on 2006-01-14
Nothing...still cant access it...i heard there was a way to do this using localhost:678 or something like that? how would i do that...

all i want to do is connect to my winxp machines hp...is it TOo much to ask?
BTW localhost thingy gives me user name and password query to which i have no idea what the answers are!

---

### Post by bscbrit on 2006-01-15
Ok, lets start tracking this one down.

Do you have samba set up?  Can you see your windows machine from your linux box? (i.e. can you share files but not your printer, or not even access your windows machine?)  How have you set up the printer sharing?  Do you have any other printers installed 1. on your linux box, 2. elsewhere on the network?  Do you have firewalls installed on _either_ computer?

EDIT:  Have you set up the connection to the printer using the GUI in System -> Administration -> Printing, and have you selected it as a network printer using Windows/smb?
EDIT2: Disregard EDIT - that is how this problem started.....!  I'm getting confused with other threads....

---

### Post by bscbrit on 2006-01-15
Can you also please confirm that you have read the link provided by AndyCooll (#3) and that there is nothing there that applies to your installation.

---

### Post by bscbrit on 2006-01-15
And check out #1 on this thread [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Although it is not specifically for your problem, it does show an easy way of confirming that you are starting cupsys at boot time.

---

### Post by kenweill on 2006-01-15
It could be a BUG.

This is what I have observed.

During a fresh install of Ubuntu Breezy, installing printers doesn't produce errors. Never experience that kind of error.

But after downloading UPDATES, I have received the same error.

---

### Post by bscbrit on 2006-01-15
Yes, it could be.  But I've got to rule out all of the other possibilities first, and then try to find a work-around. (And I suppose issue a bug report if necessary:p )

Sesstreets did have problems trying to install his printer under linux, and it is possible that CUPS became corrupted during that period.

---

