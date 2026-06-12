---
title: "General - Linux Filesystem"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by bravemenrun333 on 2007-08-19
I am completely new to Linux...

I have installed DOSbox via Synaptic - but where has it been installed? What is the directory of the installed application? In Windows this would be C:\Program Files\DOSbox - now what is it in Linux?

---

### Post by mikeyphi on 2007-08-19
> **bravemenrun333 said:**
> I am completely new to Linux...

I have installed DOSbox via Synaptic - but where has it been installed? What is the directory of the installed application? In Windows this would be C:\Program Files\DOSbox - now what is it in Linux?

Are you looking for an exe file to launch the program?
I haven't used this emulator but you probably should launch it using a run command.
Try Alt/F2 and enter DOSbox (or whatever term you know will launch the software)

---

### Post by bravemenrun333 on 2007-08-19
I know that it can be started by command line, but I search for the directory because I need to modify a file there... So where are applications installed to, when installing them automatically using the synaptic manager?

---

### Post by jgrabham on 2007-08-19
> **bravemenrun333 said:**
> I know that it can be started by command line, but I search for the directory because I need to modify a file there... So where are applications installed to, when installing them automatically using the synaptic manager?

Usually to /usr/bin/

---

### Post by bravemenrun333 on 2007-08-19
thanks, ok the executable is located in usr/bin/ but I still cannot find the other files which come with DOSbox (e.g. config files, readme files, etc.) - Do you have a clue where these files could have been installed to?

---

### Post by lgambett on 2007-08-19
Enter adept manager, select the package you have just installed then with right click + details you will obtain a list of every file installed, with the relevant directory.
In general, from the terminal
**sudo find / -name filename**
will show where the file named filename is.

---

### Post by bravemenrun333 on 2007-08-19
That was what I searched for.
Thanks!

---

