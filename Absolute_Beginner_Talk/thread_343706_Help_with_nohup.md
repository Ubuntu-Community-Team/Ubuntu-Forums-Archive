---
title: "Help with nohup"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Ic3y on 2007-01-21
Hey guys
I have been trying to run a .sh file in terminal under nohup

the way I have done it is 
> nohup ./tick.sh 30

problem that I am encountering is
> nohup: appending output to `nohup.out'

is it something that I typed in wrong or is it to do with me not having nohup?

Thanks guys
Ic3y :biggrin:

---

### Post by Bachstelze on 2007-01-21
That is not a problem. Nohup is just telling you it appended the output of your script to nohup.out instead ot sending it to the stdout, which is pretty much wat it's for.

---

### Post by Ic3y on 2007-01-21
its a ticker for a planetarion clone script

friends like the game so I figured that I would create a server.

Thanks for your help 8) 

Ic3y :biggrin:

---

### Post by Ic3y on 2007-01-22
Hey again
I found the location of the nohup.out next problem is when I open the text file it contains this

> trap: 21: SIGTERM: bad trap
./tick.sh: 1: clean_up: not found


Is there anyway I can repair this or is there something that I have to install??

Thanks
Ic3y :biggrin:

---

### Post by onsy on 2007-01-22
Hi,
The nohup.txt you quoted means 2 things : 
  1. The program tick.sh was terminated (SIGTERM)
  2. The "trap" call a subroutine called clean_up which it can't find :-(

Trap is usually used to exit programs in a way you can control : thus, you can clean temp files, or remove a lock, ....

---

