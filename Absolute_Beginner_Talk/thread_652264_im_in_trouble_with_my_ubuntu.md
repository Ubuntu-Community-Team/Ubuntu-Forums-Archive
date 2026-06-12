---
title: "im in trouble with my ubuntu"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by iatebe on 2007-12-28
i have a problem with my ubuntu, im running something (play music, ...) suddenly its unable to click on anywhere on desktop :(, and the keyboard, too, its unable to press anything, but everything still running. Then i must press the reset button to reboot my pc :(
can anyone explain for me ??? :(

---

### Post by skymera on 2007-12-28
what Ubuntu version are you using?

and also your pc specs?

---

### Post by iatebe on 2007-12-28
i use ubuntu 7.10

CPU : pent IV 2,26 GHz
RAM : 384
GVA : NVIDIA GeFore 4000 128 MB

---

### Post by sailor2001 on 2007-12-28
you have small ram.. for 7:10 minimum 512

---

### Post by iatebe on 2007-12-28
> **sailor2001 said:**
> you have small ram.. for 7:10 minimum 512

:( ... so dont have any solution else :(

---

### Post by akopacsi on 2007-12-28
I had similar problems. ( First off, make a back-up copy of your xorg.conf file. ) Then...
try to add this line into its [modules] section:

Disable "dri"

It solved such hard-freeze problems for me.

---

### Post by Chayak on 2007-12-28
Well with that little ram I'd take a serious look at Xubuntu to help cut down on the memory usage.
If that doesn't work look at DSL or Puppy.

---

### Post by candtalan on 2007-12-28
> **sailor2001 said:**
> you have small ram.. for 7:10 minimum 512

Ubuntu 7.10 Release Notes
System Requirements
The minimum memory requirement for Ubuntu 7.10 is 384MB of memory for desktop CDs, and 256MB for other installation methods. (Note that some of your system's memory may be unavailable due to being used for the graphics card.)

With only the minimum amount of memory available, the installation process will take longer than normal, but will complete successfully, and the system will perform adequately once installed. Low-memory systems may be able to use the desktop CD to install by adding the only-ubiquity boot option to run just the installer rather than the whole desktop.

hth

---

### Post by tech9 on 2007-12-28
> **iatebe said:**
> i use ubuntu 7.10

CPU : pent IV 2,26 GHz
RAM : 384
GVA : NVIDIA GeFore 4000 128 MB

1GB of RAM is recommended

---

### Post by cjm5229 on 2007-12-28
> **tech9 said:**
> 1GB of RAM is recommended

This isn't Vista, I've had this running on machines with as low as 128MB without a problem. I would bet that it is a Graphics card configuration problem. Make sure you have the right driver for your card, and do as akopacsi said and disable "dri" Search the forums for info on your particular Card. 
Good Luck.

---

### Post by ingram on 2007-12-28
> **cjm5229 said:**
> This isn't Vista, I've had this running on machines with as low as 128MB without a problem. I would bet that it is a Graphics card configuration problem. Make sure you have the right driver for your card, and do as akopacsi said and disable "dri" Search the forums for info on your particular Card. 
Good Luck.

I have seen similar problems to the one described. The windows that are open will go grey or just lock up. Music and such will continue to play and I have never seen that as a result of too little on ram.

---

### Post by tech9 on 2007-12-28
> **cjm5229 said:**
> This isn't Vista, I've had this running on machines with as low as 128MB without a problem. I would bet that it is a Graphics card configuration problem. Make sure you have the right driver for your card, and do as akopacsi said and disable "dri" Search the forums for info on your particular Card. 
Good Luck.

I know that.. whats with the attitude? 

The more RAM, the better!

---

### Post by Vadi on 2007-12-28
I run with 512 ram just fine.

But yes, I'd recommend that you use xubuntu (same ubuntu, but with an X, and looks a bit different. But better for your machine).

And try the dri option as suggested.

---

### Post by tech9 on 2007-12-28
> **Vadi said:**
> I run with 512 ram just fine.

But yes, I'd recommend that you use xubuntu (same ubuntu, but with an X, and looks a bit different. But better for your machine).

And try the dri option as suggested.

I am running 512MB on one of my other boxes... it works fine, but my main box that has 1GB performs better.

---

### Post by iatebe on 2007-12-29
thank u all ... perhaps i have to upgrade my RAM :)

---

### Post by iatebe on 2007-12-29
> **akopacsi said:**
> I had similar problems. ( First off, make a back-up copy of your xorg.conf file. ) Then...
try to add this line into its [modules] section:

Disable "dri"

It solved such hard-freeze problems for me.

i will try this first :)

---

### Post by thamood on 2007-12-29
i had the same problem the disktop went repond...i think the problem is with nuatlis (may the spelling is wrong) ...but what i do is go to the "task manager" and kill the "natulas" process and it's restarts and the desktop is responding again.......why does this happen? i dont know

---

### Post by iatebe on 2007-12-29
> **thamood said:**
> i had the same problem the disktop went repond...i think the problem is with nuatlis (may the spelling is wrong) ...but what i do is go to the "task manager" and kill the "natulas" process and it's restarts and the desktop is responding again.......why does this happen? i dont know

but how do u go to "task manager" and kill it. i even cant do anything :(

---

### Post by thamood on 2007-12-29
when that problem happen i sed to go to the "system->adminisrative->task manager".

can you open the menus? or are thet frozen as well?????

try alt+ctrl+back space to restart X <---this is something like alt+ctrl+del in windoz

---

### Post by iatebe on 2007-12-29
> **thamood said:**
> when that problem happen i sed to go to the "system->adminisrative->task manager".

can you open the menus? or are thet frozen as well?????

try alt+ctrl+back space to restart X <---this is something like alt+ctrl+del in windoz

i tried but nothing happen

---

### Post by thamood on 2007-12-29
even the "alt+ctrl+back space"??

---

### Post by iatebe on 2007-12-29
> **thamood said:**
> even the "alt+ctrl+back space"??

yep :(

---

### Post by atomkarinca on 2007-12-29
You can try using more leightweight alternatives. For example Thunar instead of Nautilus, Epiphany instead of Firefox, Exaile instead of Amarok. If you have the desktop effects on, you can try turning it off.

By the way I had Feisty installed on 256 mb of ram with no porblem (even with the effects on). If the processes are still running it may be a graphics card problem.

---

