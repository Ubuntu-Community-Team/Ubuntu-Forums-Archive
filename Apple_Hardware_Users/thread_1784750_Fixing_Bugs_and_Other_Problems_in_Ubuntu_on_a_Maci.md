---
title: "Fixing Bugs and Other Problems in Ubuntu on a Macintosh"
date: 2011-06-17
forum: Apple Hardware Users
---

### Post by MacHackers on 2011-06-17
Hey Guys.....
 
I've noticed some bugs with Ubuntu on a PPC Mac. This thread is for Bug finding and how to fix them if possible. So, I run an eMac with Ubuntu 10.04 LTS. Here's the bugs I've noticed....

[LIST]
[*]If your listening to music or a DVD on a server and you turn to volume up, It **distorts** and it's hard to understand... I'm afraid it may cause speaker damage.
[*]Flash doesn't have support at all. I've seen some alternatives, but I can't figure out how to install them. One of the most popular alternatives doesn't even work like it says.
[*]Brightness keys don't work at all.
[*]When you eject the Disk Drive (I use the Super-Combo Drive), it will eject like it supposed to, but after like two seconds or so, it goes retracts back into the computer.
[*]Software Sources and Expositories are sending back HTML 404 errors when you use the terminal (sudo apt-get update). Are the Expositories not maintained?
[*]Wireless doesn't work until you install a Broadcom Driver (B43).
[/LIST]I need help with these... However, Wireless is working. I need help.. And again, I run an eMac with 1.0 GHz Speed with a G4 processor. I also run Ubuntu 10.04. These bugs are annoying and some of them take the 'fun' out of the internet and Ubuntu. I need these fixed as soon as possible, so if you have any bugs, or can help, **PLEASE** reply to these posts in this thread...

---

### Post by avtolle on 2011-06-17
On the repository issue, please post your /etc/apt/sources.list for review. I was running 10.04 on a G4 Cube until this morning, and did not have the 404 problems you describe. If I was going to post the sources.list file, I would do it by first creating a text file, ```
cat /etc/apt/sources.list > ~/Desktop/sources.txt
``` then copying and pasting it, placing it between code tags for easier reading (or add it as an attachment).

---

### Post by MacHackers on 2011-06-19
> **avtolle said:**
> On the repository issue, please post your /etc/apt/sources.list for review. I was running 10.04 on a G4 Cube until this morning, and did not have the 404 problems you describe. If I was going to post the sources.list file, I would do it by first creating a text file, ```
cat /etc/apt/sources.list > ~/Desktop/sources.txt
``` then copying and pasting it, placing it between code tags for easier reading (or add it as an attachment).
Okay... I'm not near my computer right now, but when I get to it, I will post the list for you.. Run that command in Terminal, right? Are you wanting me to post the WHOLE sources.list?

---

### Post by avtolle on 2011-06-20
Yes, run in terminal. Yes, the entire list; that's why I suggested use of code tags.

---

### Post by avtolle on 2011-06-20
I have the same problem with eject on the Cubes. I try to be quick in "grabbing" the CD-R so it doesn't have a chance to retract; sometimes, I'm successful. :-)

---

### Post by pauljwells on 2011-06-24
DVD eject issue is known and an easy fix

[http://ubuntuforums.org/showthread.php?t=1737898]("http://ubuntuforums.org/showthread.php?t=1737898")

---

