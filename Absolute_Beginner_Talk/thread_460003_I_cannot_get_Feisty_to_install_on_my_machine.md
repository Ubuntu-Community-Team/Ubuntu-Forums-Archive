---
title: "I cannot get Feisty to install on my machine"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-05-31
I have an HP Pavilion 753n Desktop, 2.53GHz, 1GB RAM, 80GB hard drive and I have NO external hard drive.

My BIOS setting is:-

1st CDROM
2nd Hard Disk
3rd Removable

Currently I'm running Dapper and when I try to upgrade to Feisty, with a Live CD, the installation quits within about 3 seconds of me clicking on the 'Run or Install' line.

I have been through this process many times and I have tried 2 different disks, the one I burned and a genuine Ubuntu factory disk (and they both work in other desktop machines that I have)

When burned an Edgy Live CD, it will boot up, somewhat hesitantly but it does work.

There must be something in my machine that causes this problem but I don't know enough to even think what it might be.

Is there some kind of test I could run, or lines of code I could display that might give a clue to this situation?

---

### Post by plcdfa on 2007-05-31
What do you mean by quit? Isn't there any error message?

---

### Post by L Campbell on 2007-05-31
> **plcdfa said:**
> What do you mean by quit? Isn't there any error message?

There is no error message.  The screen just goes black and the 'percolating' sound of the computer ceases.  The machine doesn't totally switch off but, to switch it off, I have to unplug the power cord.

When I'm using Dapper everything functions perfectly normally.

---

### Post by plcdfa on 2007-05-31
Can it be that only the monitor switches off? (For example because X tries to use a nonexistent resolution/refresh rate on it.) If you press ctrl+alt+F2 at this point do you get a usable text console?

---

### Post by L Campbell on 2007-05-31
> **plcdfa said:**
> Can it be that only the monitor switches off? (For example because X tries to use a nonexistent resolution/refresh rate on it.) If you press ctrl+alt+F2 at this point do you get a usable text console?

Thanks, I tried ctrl+alt+F2 but nothing happened.  I just had a black screen with a blinky cursor in the top left corner, so I removed the CD and shortly thereafter got the following messages:-

[125.564655] buffer I/O error on device FD0 logical block O 

[163.704100] buffer I/O error on device FD0 logical block O 

[240.988773] buffer I/O error on device FD0 logical block O 

(I think it was 'O', not zero but I'm not positive)

---

### Post by plcdfa on 2007-05-31
fd0? That's the floppy drive! :shock: Strange. When you hit enter on Run or Install it's supposed to display a progress bar of loading the kernel and some other messages before swithing to graphic mode (as I remember.). What is the last one you see?

---

### Post by L Campbell on 2007-05-31
> **plcdfa said:**
> fd0? That's the floppy drive! :shock: Strange. When you hit enter on Run or Install it's supposed to display a progress bar of loading the kernel and some other messages before swithing to graphic mode (as I remember.). What is the last one you see?

Oops!  The flat cord to the Floppy had become disconnected.

When I then tried the Feisty CD I initially got the same thing.  Click on 'run or install Ubuntu', the screen goes black and the machine quits 'percolating'.

This time, after several minutes it began to come back to life and I got lines of script on the screen, begining with:-

Setting preliminary keymap

(lots more lines that I didn't have time to write down)

and the last line I saw was:-

Common Unix printing.

After this the screen again went black and I got no more action.  I repeated this course of action several more times and, on the 4th try it seems like the program 'caught on' and I was able to fully load the CD into RAM.

Thinking I had achieved some significant progress, I shut the machine down and then rebooted the live CD again.  Unfortunately, even after 8 attempts, the CD would not 'catch' again, so I'm still back at square one.

Thanks again for your interest.

---

### Post by plcdfa on 2007-06-01
So once it worked without problem, but then it went wrong again? I would say it's a hardware issue (RAM or perhaps the optical drives) but if the Edgy CD works well with the same machine then this explanation also fails. I'm a bit clueless now. I'd recommend you to try the alternate install cd, if it's not a problem to download with your bandwidth. It installs the same Feisty system, but it's not a Live CD, it features the old style text-mode installer. (Not too difficult to use either.) The alternate cd was made for cases like this, and even if it won't solve your problem, it might spit out some usable error messages.

---

### Post by L Campbell on 2007-06-01
> **plcdfa said:**
> So once it worked without problem, but then it went wrong again? I would say it's a hardware issue (RAM or perhaps the optical drives) but if the Edgy CD works well with the same machine then this explanation also fails. I'm a bit clueless now. I'd recommend you to try the alternate install cd, if it's not a problem to download with your bandwidth. It installs the same Feisty system, but it's not a Live CD, it features the old style text-mode installer. (Not too difficult to use either.) The alternate cd was made for cases like this, and even if it won't solve your problem, it might spit out some usable error messages.

Thanks for your continued interest.

I am up and running with Feisty now and did, in fact, do it with an Alternate CD.  I had made the CD a few weeks ago but couldn't get it to boot up properly in several tries.  Today was a new day and it worked perfectly.

Kind regards.

---

### Post by plcdfa on 2007-06-01
I'm glad you succeded finally. It's good you haven't given up.:)

---

