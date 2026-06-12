---
title: "iMac G5 slow and fast"
date: 2007-08-13
forum: Apple PPC Users
---

### Post by anurse on 2007-08-13
I am trying to install 7.04 on a G5 iMac, about two years (give or take) old. There is a problem with the splash screen (odd colours and small) but then the live cd works just fine. It is responsive, even snappy to use. After the install, however, the system slows to a crawl, the mouse jumps around when moved instead of sliding across the screen.  In addition I get an error message on start up, re error starting  GNOME settings daemon (or something like that, sorry for the lack of exactness on this last point). What can I do to fix this?

---

### Post by ssam on 2007-08-13
if you open a terminal
Applications -> Accessories -> Terminal

and run the command
```
top
```

it will give a list of running processes, and how much cpu they are using.

if you report what the top few processes are maybe someone can help

---

### Post by anurse on 2007-08-13
Thanks for the quick response. I ran "top" and will confess that I don't understand what came up because I'd be classified as a Newbie so tell me if this is correct.  A list ran across the top that included the following: PD USER PR NI VIRT RES SHS S %CPU %MEM COMMAND. The first two items listed root as user and had the commands mouseema (the first item on the list), the second was xorg. If this is any help mouseema said it was using 98.2%CPU while xog listed 0.3%. The next item was "top" Is there more information you need?

---

### Post by tcrroadie on 2007-08-13
You are understanding the output of "top" correctly.  It looks as if the daemon "mouseemu" is what is causing your problem.  The "mouseemu" daemon has been reported many times here in the forums as hanging and causing users systems to respond slowly or hang.  

Since the "mouseemu" daemon is used to emulate mouse buttons on trackpads and you have a desktop Mac, you can simply remove the daemon from your system entirely.  

In your terminal, first kill the process within the "top" tool by pressing k on your keyboard.  Then enter the pid number for the running process for mouseemu, and press the enter key.  To exit "top" press the Q key.  

Then remove the mouseemu package by running 

```
sudo apt-get remove mouseemu
```

---

### Post by anurse on 2007-08-13
OK,  this even makes sense to me. One further problem. When I run k and gave the number (4845) the response was kill pid 4845  signal [15]: I hit enter again (assuming I can see incorrectly that that was what I should do) and the reply came up operation failed or was not permitted.  Do I need to use another terminal and kill this using sudo?

---

### Post by tcrroadie on 2007-08-13
Sorry.  The mouseemu deamon is a root process.  Run top with sudo and try again.  Should work this time.

```
sudo top
```

You can also use the "kill" command.  I believe you can simply 

```
sudo kill "pid number of running process"
```

See the man page for more information. 

```
man kill
```

---

### Post by anurse on 2007-08-13
Worked like a charm. Many thanks.

---

