---
title: "root fs freeze"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by theophane.weber on 2007-02-13
Hi,

I tried to get some help earlier for a mount root filesystem hang-up during boot; and i understand it's too time consuming for someone to look in detail.. So, I was wondering if I could just get some help to find how to solve it myself:
what does it mean that mount root filesystem fail? Or, more precisely, how can it fail? My ubuntu partition is the very first partition of my first disk. Sometime, ubuntu will suceed at mounting the root filesystem, and sometimes, it doesn't... So, I guess what I was wondering is the following:
a) how is it possible that the sucess of mounting the root fs is random? Without changing anything in the configuratino of anything, if i keep rebooting for fun, it will sometime go past the root fs, sometimes not. i am used to more.. "deterministic" computers.
b) what happens exactly when the root filesystem can't mount? Does it mean it can't find the hard drive? the partition? 
c) when it is stuck at "mounting root filesystem", how can i stop it from trying to mount the fs? How can I diagnose what is exactly going on?

Thanks for any help!

---

### Post by Albi on 2007-02-13
What OS are you typing this in?

Firstly, 1) Has it ever booted before?
2) Did you update grub recently?
3) Can the file system be read from the LiveCD?

---

### Post by theophane.weber on 2007-02-13
The system is Ubuntu 6.06 (Dapper), but the same thing happened when I had warty, or when i try edgy.
The system does boot; but not always. It seems completely random (say, 40% chance of booting, 60% of problem at mounting root fs, in the exact same conditions). The version i am running now has recently been installed, so grub has been installed recently...

The system boots from LiveCD.. sometimes! (i don't get an error message, but i guess it is the exact same problem)

(right now, i am typing from ubuntu; it booted after 5 trials)

thanks!

theo

---

### Post by romi7519 on 2007-02-13
I have exactly the same problem. It boots on the 1st try sometimes and sometimes it takes 4+ tries. Can anyone help as its putting me off using Linux..:(

---

### Post by theophane.weber on 2007-02-13
well, let's try to see what our system have in common, then :)
I have two culprits in mind: 
my hard drive (which is a Western Digital Raptor 150 Go), and my monitor (i know, it sounds weird...), which is a dell 24 inches. Other than that, I have a second drive (WD as well); my motherboard is a A8N32- SLI. Everything else I have is too common (I think) not to have been identified as posing problems with ubuntu (but i could be wrong... I have little clue what can go wrong during mount root fs)

-theo

---

### Post by theophane.weber on 2007-02-14
allright, I read a thread earlier with knowledgeable ubuntu users complaining about newbies not giving feedback or asking a question without checking answers... 
So, I don't know how bad it is here to bounce the thread up, but ....
Does anyone have the tiniest lead about how to diagnose a problem like this? I promise to help beginners a lot when I actually get to understand ubuntu better....

-theo

---

### Post by romi7519 on 2007-02-18
Had enough of it. Installed it using VPC on XP.

---

