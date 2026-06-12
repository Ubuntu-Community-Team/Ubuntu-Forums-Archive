---
title: "Processor?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by shakujou on 2007-08-03
Alright, this isn't quite a problem with Linux, as it is just a problem with my own knowledge of Linux and my own computer.  

The college I'm going to demands that I download a specific anti-virus program, without it I wont be able to log onto the network with my computer.  I honestly don't think Linux users should have to use this, but they just want to feel secure no matter what.  

So, I went to the site, and found the place to download the Linux software, but I have to know what processor/type of Linux I have to get the right download.  My choices are:

[img]http://img485.imageshack.us/img485/3044/screenshot1vw7.png[/img]

I installed the standard release of Feisty Fawn, and I use an [Intel Pentium 4 processor](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116004).

---

### Post by p_quarles on 2007-08-03
Your links didn't work for me, but it looks like the options are between Intel architecture and AMD architecture. Only you know which kind of processor you have.

That said, no, you don't need an anti-virus program for Linux. Linux is not 100% bulletproof, but it's nearly invulnerable to viruses. What's more, I doubt that the network you want to log onto will even be able to scan your system for a specific program -- Linux systems don't tend to cooperate with requests like that.

I think you have two options here: 1) Try to reason with the know-nothings who wrote this policy, and explain that your choice to use Linux actually means that you are less of a security risk to their network; or 2) Install Windows. Neither are very appealing, I know, but based on your description I don't see any other way. Sorry.

---

### Post by rohan000 on 2007-08-03
If you have an Intel processor then it's one of the first two choices, not the third. I imagine the different between those two is what version of libc6 is installed. Maybe you can try one and if it doesn't work try the other?

---

### Post by asmoore82 on 2007-08-03
Rule #1: do not install an AntiVirus for linux.

Rule #2: EVEN IF YOUR LIFE DEPENDS ON IT; DO NOT install an AntiVirus on Ubuntu
that does not come from the official Ubuntu software depos

---

### Post by pacsum on 2007-08-03
install just a firewall like firestarter

---

### Post by p_quarles on 2007-08-03
>  Rule #2: EVEN IF YOU LIFE DEPENDS ON IT; DO NOT install an AntiVirus on Ubuntu
that does not come from the official Ubuntu software depos
Agreed, but I would stipulate that rule #2 depends upon how well the gun is aimed at your head. Just from a practical standpoint. :)

AVs in Linux actually add more vulnerabilities than they close. 

> install just a firewall like firestarter
First of all, the poster's problem was not with security, but with inept network admins. Second, Firestarter is NOT a firewall -- it's a firewall configuration utility.

---

### Post by shakujou on 2007-08-03
To p_quarles, the first three "links" was just a screenshot I took, and then posted on here, sorry about the confusion.  The second link, which was really a link, was my exact processor as shown on Newegg.  

I was thinking that since I was using Linux, I'd really pose no threat to their network at all, as far as viruses go.  Plus, when I was running on XP, I had the exact same program installed in preparation for college, and I noticed a considerable amount of lag on my system, trying to run this thing.  So, if my computer doesn't agree, and tries to bypass their check for this program, I'd be more than happy.  

To rohan000, I know I downloaded the first option of ubuntu, not the AMD64 version, so I know there was no problem there at all.  When I read the documentation, I determined that it was probably the 2nd file that I needed.  But they compressed the file using some strange format.  It's a .tar.z file, I've seen .tar.gz but not the former before.  What can I use to extract the files?

---

### Post by rohan000 on 2007-08-03
[ftp://garbo.uwasa.fi/unix/ts/tarzfaq.txt](ftp://garbo.uwasa.fi/unix/ts/tarzfaq.txt)

---

### Post by p_quarles on 2007-08-04
> I was thinking that since I was using Linux, I'd really pose no threat to their network at all, as far as viruses go. Plus, when I was running on XP, I had the exact same program installed in preparation for college, and I noticed a considerable amount of lag on my system, trying to run this thing. So, if my computer doesn't agree, and tries to bypass their check for this program, I'd be more than happy.
You are, of course, absolutely right. A computer running Linux is far less of a threat to the college's network than a computer running WinXP. My concern, though, is that you may not be able to authenticate on their network if you can't "prove" you're running whatever bloated anti-virus software they're looking for. By all means give it a try, but keep your XP disks around in case you need to dual-boot.

---

### Post by shakujou on 2007-08-04
I installed gzip, which was supposed to be able to uncompress .z files, but I'm still unable to get it to work.  I get this message when I try to access the files within:

> Could not open
"linux.intel.libc6.glibc.2.2.tar.Z"

Archive type not supported.

---

