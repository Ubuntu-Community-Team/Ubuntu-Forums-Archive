---
title: "Running OS on Ubuntu"
date: 2006-10-20
forum: Apple PPC Users
---

### Post by tbonney on 2006-10-20
I've heard you can run OS X on Ubuntu.  I saw some instructions but, they seem to require root privledges on my computer, though I don't know why.

I'm very much a novice with Unix commands.  Can someone explain how to run OS X under Ubuntu and how to get root privledges?  Also, if anyone knows of a good Unix command guide for beginners I'd appreciate.

I'm a former PC users, very familiar with DOS, that has been using a 12" powerbook for the last three years.  

I like what I see in Ubuntu but, I'm already tire of dual booting!

Tim

---

### Post by AgenT on 2006-10-20
Ubuntu does not use root. Instead, it uses sudo. The difference is very small but has a large effect in how you use it and what it means for security (sudo is said to be more secure).

If you have directions that say something like this (root):
>  You must be root [then you access root and enter root password]. When you are root, execute the command: ```
mycommand blah blah
```Translate that whole thing as:
>  execute the command:
```
sudo mycommand blah blah
``` [enter admin password - which is your user password usually]

---

### Post by Henry Rayker on 2006-10-20
I have never seen anything about running OSX ontop of Ubuntu. I'm inclined to say it is not possible, but I'm prepared to be incorrect.

---

### Post by shadie on 2006-10-20
try here [http://www.maconlinux.org/](http://www.maconlinux.org/)


If you already have OS X installed you only have a few steps left to have OS X working from within Ubuntu, do a search for MOL on this forum.

---

### Post by techrush on 2006-10-21
mac on linux rocks! its one of the things that makes dual booting my powerbook worthwhile. along with mac on mac installed within OS X. you can access your ubuntu install from within OS X and vice versa. its great! 

it is also one of the best performing virtual machines ive ever used (compared to VMware or parallels). i think this is because it allows direct access to the hardware that the OS expects to run anyways. so not much slow emulation is actually taking place.

---

### Post by sebpayne on 2006-10-22
> **techrush said:**
> mac on linux rocks! its one of the things that makes dual booting my powerbook worthwhile. along with mac on mac installed within OS X. you can access your ubuntu install from within OS X and vice versa. its great! 

it is also one of the best performing virtual machines ive ever used (compared to VMware or parallels). i think this is because it allows direct access to the hardware that the OS expects to run anyways. so not much slow emulation is actually taking place.
I have looked into Mac on Mac - since I'd love to run Ubuntu inside of OS X but it seems dated and doesn't seem to work with OS X 10.4. Has anyone had any success or got any ideas?

Does MOL work with 10.4 inside of Ubuntu?

---

### Post by techrush on 2006-10-22
MOL works with 10.4

---

### Post by jaradronald on 2006-10-22
Even possibly cooler than mac on linux & vice versa is running Windows on PPC via Linux... Using QEMU & VGABIOS I installed Windows 98 on my Macintosh PowerBook G3. Now THAT'S some opensource cross-platform compatibility!
 
Speaking of running Linux on OSX though, VMWare is looking for beta testers for the upcoming release of their OSX Port. I've been using VMWare it to run containted Linux environments on my PC for quite some time now. Glad to see VMWare following up with OSX Support for their software. Check it out if you are an OSX/Linux geek....
 
[http://www.vmware.com/whatsnew/macsignupform.html](http://www.vmware.com/whatsnew/macsignupform.html)
 
Oh, and I think you can use VMWare to run Windows Environments as well in OSX, but don't quote me on that one.  And that might just be for Intel based Macs...  What is it that makes Apple think they have the right to tell you HOW and WHAT OS'es you can use with their processors?

---

