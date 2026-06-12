---
title: "Can I install Ubuntu on a MAC OS X Server 10.4.11?"
date: 2013-09-06
forum: Apple Hardware Users
---

### Post by n41076jem on 2013-09-06
I have OS server that  has a Dual-Core intel Xeon proceessor  and I have a need to run ubuntu native.

 What image do I use?


Jim Moore

---

### Post by n41076jem on 2013-09-06
The fun thing is I can boot from a clonezilla live USB stick and make a back up image.  I trying to build a ubuntu image with tuxboot set to custom

---

### Post by sanderj on 2013-09-06
> **n41076jem said:**
> I have OS server that  has a Dual-Core intel Xeon proceessor  and I have a need to run ubuntu native.

 What image do I use?


Which Xeon? How much RAM? From which year is your Mac Server? 

Probably Ubuntu 12.04. And: 32-bit will always work. The 64-bit version ("AMD64") will probably work too (assuming your Xeon is not from 1998 or so).

---

### Post by n41076jem on 2013-09-06
1 GB ram, two [FONT=Verdana, sans-serif][COLOR=#000000] 2.0 GHz Dual Core Intel Xeon 5130 processors, purchased in 2009[/COLOR][/FONT]

---

### Post by CharlesA on 2013-09-06
That CPU supports 64-bit, but you might want to install the 32-bit version of Ubuntu server (or even Debian Wheezy) if you are going to be running on something with 1GB of RAM.

What are you going to be using it for?

---

### Post by n41076jem on 2013-09-09
I am administrator for a small primary school. We want to run a package called schooltools. SchoolTool is a full stack web application. That is, it comes with its own web server and database. To make sure all the necessary components are installed correctly,  it is distribute to users as packages, primarily through Ubuntu Linux. This gives users a simple &#8220;app store&#8221; one-click installation experience.


------------------------------------

The  problem seem to be that EFI on the MAC Server. I did an install on same age IMAC without any issue. Used clone zilla to transfer the image to  the server. No joy the server would not boot

---

### Post by CharlesA on 2013-09-09
EFI is a problem. I thought 12.04.3 had support for it, but I'm not sure as my server doesn't use UEFI and I don't run Ubuntu on it.

You might have to try one of the 13.04 and then bump up to 14.04 when it is out.

---

