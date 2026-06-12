---
title: "URGENT: entire PC dead after attempted change of acces rights"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Riotstarter on 2007-08-29
It all startet with me being unable to use my second partition of the HDD as well as anything else except my "personal folder"

I tried to solve this by logging in as root, marking my whole directories, going to properties and giving "read and write" rights to root and my normal username.


After this, ubuntu crashed and never came back. When booting the system, it gives me the following error message:

"/bin/sh: can't access tty; job control turned off"

and below this some strange console command line "initramfs"

what should I do now? Is there a way to save my ubuntu install without killing all my files and customizations I have done since I got this OS?

---

### Post by Hobo Joe on 2007-08-29
Sounds like you MAY have a harddrive failure.

---

### Post by Riotstarter on 2007-08-29
You mean damaged hardware? would be great, that thing is a laptop :(

---

### Post by punx45 on 2007-08-29
"/bin/sh: can't access tty; job control turned off"

doesnt really sound like a HDD problem type message.

   Unless you fell like retracing your steps and undoing exactly everything you did your easiest solution at this point is probably a reinstall, chalk it up as a lesson learned, and from now on respect the power and responsibility of root :)

im not sure how the GUI version of access control works out, but since you say you gave "read and write" permissions and didnt mention  "execute," I'm wondering if maybe you accidentally switched off execute for everything?

---

### Post by Riotstarter on 2007-08-29
well I dont know for sure, but I thought "read" includes "execute" ;-)

all I wanted is to have my whole PC available for me because  don't like it when my PC is telling me I don't have access rights because I'm not me, is that a crime? :confused:

any Idea how tocopy my personal folder to safety before reinstalling?l

---

### Post by punx45 on 2007-08-29
nope. read, write, and execute are three separate entities.   read means you can see the contents of the file.   execute means you can tell the file to do what it is meant to do.   that would include all the scripts that load up the various parts of the OS, of which, [initramfs]("https://wiki.ubuntu.com/Initramfs") appears to be ](*,)

you should be able to do some sort of rescue operation with a live CD.   you could use either an Ubuntu one, or maybe find a live distribution that is designed for rescue. (I think there is a knoppix based one.   consult the google)   then in conjunction with that and a USB drive or some other writable media, you can save your files.

then you can reinstall, and go read up on permissions :)

---

### Post by Riotstarter on 2007-08-29
OK, now a really dumb question:

how do I boot ubuntu from CD with root rights.

because I can't do anything in this demo mode and my user accounts and PWs don't work in switch user screen.

---

### Post by punx45 on 2007-08-30
unfortunately, I can't help you there as I have no experience using the live CD.   But I am sure there are tons of discussions on it here in the ubuntu forums.   you will probably be able to find an answer to your question in a few minutes of searching.

---

### Post by Riotstarter on 2007-08-30
OK found it out myself, ill now try permitting execution on the folders I madechanges before, maybe that   will help

---

