---
title: "Avast wont run - weird errors (using for email scan)"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-08-21
gksudo avastgui
==: unexpected operator

(process:22171): Gdk-WARNING **: locale not supported by Xlib

(process:22171): Gdk-WARNING **: can not set locale modifiers
Segmentation fault (core dumped)
philcb@philcb-desktop:~$ dpkg -l avast4workstation
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  avast4workstat 1.0.6-2        avast! antivirus

any ideas

---

### Post by oilchangeguy on 2007-08-21
a quick look around the forum and you should be able to find enough threads that show there's no need for anti-virus software in linux. even if a virus is in your email, it can do no harm to your computer.

---

### Post by philinux on 2007-08-21
Your right and I know it.

But I dont want to forward crap to my windows using friends!

---

### Post by oilchangeguy on 2007-08-21
> **philinux said:**
> Your right and I know it.

But I dont want to forward crap to my windows using friends!

most isp's now scan email for virus' before it get's to the persons inbox. and security is the responsibility of the computer user. not the person sending the email.

---

### Post by the.phantom on 2007-08-21
will it scan the home file ok?

wonder if it might be the format of t-bird email extension it can't read?
just a guess as i don't think it has e-mail scanning abilities in this version???

---

### Post by philinux on 2007-08-21
Ok update I can get the gui to show up by...

sudo avastgui
Password:
test: 95: ==: unexpected operator

(process:22682): Gdk-WARNING **: locale not supported by Xlib

(process:22682): Gdk-WARNING **: can not set locale modifiers

-----

with these warning messages

---

### Post by the.phantom on 2007-08-21
how did you install it
and is the first time you tried to make it work?

i have a shortcut to start it and i use 
gksudo avastgui

---

### Post by philinux on 2007-08-21
Tried that gksudo, same errors

uninstalled the package, cant be bothered with this. Avast is not ubuntu friendly.

Will stick to repos

Avg works but all I wanted was to scan emails.

---

### Post by gobbles414 on 2007-08-21
Hi all,

Try the instructions [here]("http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html") (works for me about 99%). It may also be worth your time to look at [this thread]("http://ubuntuforums.org/showthread.php?p=3083008"). EDIT: I run the program using *gksudo avastgui*. Also, I am able to manually scan and clean my emails in Evolution by scanning the hidden .evolution folder in my home directory. NOTE, Avast thinks that the home folder is in the root directory. Navigate to your home directory starting at (/) to find the real home directory.

---

### Post by philinux on 2007-08-21
They are the instructions I followed ](*,)

---

### Post by tashmooclam on 2007-08-21
Let your recipient bother with running Avast. 
Use Thunderbird or gmail and forget it.
Just my 2 cents.

---

### Post by the.phantom on 2007-08-21
Gobbles414


i just loaded up a test message in T-bird inbox with eiclar
and navigated to the TRUE home folder and 
ran a scan on selected file ( the full folder) and i got a hit and it said eiclar was found !!!

UPDATE:
ooops it found it on the desktop but not in t-bird ( i had downloaded it there)

---

