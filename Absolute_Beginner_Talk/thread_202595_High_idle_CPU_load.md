---
title: "High idle CPU load"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by sternael on 2006-06-23
Downloaded and tried the Kubuntu Live CD - everything works fine, but looking with ksysguard the CPU idles at about 20 %. My computer is quite old (PII 400, 256 MB RAM, 32X CD-ROM), so maybe this is completely natural, or maybe my computer has some strange setup, or maybe ksysguard nibbles away from the CPU, I don't know.

In Windows 2000, the system idles at about 1 % - with antivirus and firewall activated.

Should I install Kubuntu anyway, download Ubuntu instead, switch to another Linux distro, keep my Windows, or recycle the metal?

---

### Post by niteblind on 2006-06-23
I am seeing something kinda similar but with memory usage. on my laptop i got 512mb with 128 shared to the graphics and the memory iis constantly running at about 420mb!

i never checked it when i had ubuntu on there but the kde interface seems ALOT slower on boot than the gnome one did.

any thoughts anyone???

niteblind

---

### Post by Bartender on 2006-06-23
stern -
I'm not in front of my Linux PC (in sig) so can't verify CPU usage but it does seem like the CPU's busier in Breezy than W2K.  Seems contrary to everything we hear about Ubuntu running just fine on older machinery, doesn't it?  20% doesn't sound out of range...

---

### Post by sternael on 2006-06-24
Maybe this is why all Linux servers do not use a GUI... =D

---

### Post by Kurt` on 2006-06-24
Well, linux in general handles memory much differently than Windows.

Your ram usage will almost always be "high", but that memory isn't actually being used by programs. For example, here is a shot from phpsysinfo running on my server:

[img]http://xs302.xs.to/xs302/06256/memoryusage.png[/img]

Note that I am at 99% usage, but 78% of that is just "cached" programs/files. That stuff will be unloaded instantly if a program needs the memory. I am only really using about 100mb of ram. :)

---

### Post by OkeyuL on 2007-12-26
Hi try this, it worked for me:

The problem is that in idle, one of the CPU is at about 30% all the time.
This is comming from **ksoftirqd**.

Solution (found on the internet, not mine):
 - edit boot options:
   **sudo nano /boot/grub/menu.lst**

 - add at line that starts with "# kopt=":
   **nohz=off**

 - close and save

 - update configuration with:
   **sudo update-grub**

 - reboot

PS: Ubuntu 7.10 64bit, proc Intel

---

### Post by LeDechaine on 2008-02-11
err.. do you exactly know what the **nohz=off** thing does?

I couldn't find any info on it via the man pages, and saw on some forums that this was disabling (i think) the.. "tickless" kernel mode, and this was useful when the clock was running too fast/slow on another linux distro... *scratches head*
Sounds useless for me until now anyway..

I'm asking this because my **ksoftirqd** is now using ~20% of my CPU.
Saw some **ksoftirqd** info which was quite vague (for me ;)), but nothing related to **nohz**...

**Ok. Just found by searching more. It's a bug**. had to unload the cx8800 module.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153195](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153195)

---

### Post by Christmas on 2008-02-11
You configuration is old, so the CPU usage might be normal, and you use Kubuntu Live CD. You can try to install it and see how it works. It should be extremely slow, but the CPU shouldn't stay at 20% in my opinion. Also, Kubuntu was released in 2007 and is destined to more powerful machines with at least 512 RAM, while Windows 2000 was released 8 years ago so you get the point.

---

### Post by skymera on 2008-02-11
type ```
 top 
``` into the terminal to see what is using the most processor usage

---

