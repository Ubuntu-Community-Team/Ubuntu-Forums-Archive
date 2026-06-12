---
title: "opening serial port"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by jsdranger on 2007-11-06
I am attempting to open the serial port on my desktop for use.  I want the serial port to be used and not the VGA and keyboard ports, i have a tool that will convert the signal port so that i can use the keyboard and mouse but am unable to do what i need

I have done the following to date

dmesg | grep tty

setserial -g /dev/ttyS0

when i enter open /dev/ttyS0 i get the following message

unable to open vt 7:  permission denied

why am i getting the above message and what can i do to resolve this

Thanks you

---

### Post by jsdranger on 2007-11-06
one small detail i failed to mention, 

I am using ubuntu 7.0.4

---

### Post by dwblas on 2007-11-06
> unable to open vt 7: permission deniedProbably means you have to be root.

---

### Post by jsdranger on 2007-11-07
how would i go about getting to be root?

---

### Post by aPaSv5 on 2007-11-07
Just precede your command with 'sudo'; by root dwblas means the 'root user', a user reserved for administrative tasks. In ubuntu, you can't go about logging in as root, rather, you use sudo (or one of its many flavors- namely 'su' or the GTK graphical version, 'gksu') to act as another user- by default this is root.

Note that you must have administrative priviliges to use root for that purpose- for more, I would reccomend that you would read the manual page for sudo. Just type 'man sudo' (without the quotes, I might add).

---

