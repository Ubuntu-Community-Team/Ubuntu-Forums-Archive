---
title: "Installed Ubuntu server (i386) and it cant see the pci ethernet card"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by amc on 2006-08-28
Hi, I am totally green with linux. I have just installed Ubuntu server (i386) and it cant see the pci ethernet card. It didnt detect it on install and i dont know how to get it to see it. I have checked the forums and done a few things like include auto eth0 etc.etc. in the interfaces file but nothing has worked it just sees the loopback interface.Like i said im am totally green but i am willing to try anything.:oops:  Can you point me in the right direction please.

---

### Post by halfvolle melk on 2006-08-28
What do
```
lspci
```
and
```
lsmod
```
tell you?

---

### Post by Iowan on 2006-08-28
What kind of card - it may need a to have a driver installed.

---

### Post by nemin on 2006-08-28
You must type the commands 'halfvolle melk' mentions in the terminal (Applications -> System Tools -> Termina). Please post the line that sais something about 'ethernet', or post the full output if you don't know which line it is.

---

### Post by amc on 2006-08-28
lspci gives me nothing :-k 
lsmod i havent tried yet ill check it out 
the card is an intel pro 100s desktop adapter
stay tuned for lsmod output :)

---

### Post by Bachstelze on 2006-08-28
> **amc said:**
> lspci gives me nothing :-k 


You might have set a record here :p the one and only computer in the world on which lspci outputs nothing :D

---

### Post by amc on 2006-08-28
> You might have set a record here  the one and only computer in the world on which lspci outputs nothing 


Heh well it is an IBM Eserver what can i say....
lsmod puts out a whole lot of stuff, what should i be looking for specifically??

---

### Post by NeoGreen on 2006-08-28
I had the same problem.  I had to find the driver and run ndiswrapper.  I think that is what it is called.:-k

---

