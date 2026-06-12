---
title: "virtualize vista off of a partition?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by myddewji13 on 2008-03-09
Hi,
I love ubuntu but i simply cannot use openoffice. Don't get me wrong... i love the program i just seem to be able to use office 07 a lot more productively....anyway....recently i've been thinking about running a windows virtual machine within ubuntu....during the course of my research i came across people using a partition on their harddrive to boot windows.... but i dont noe how to do this... my current situation is:

-dual booting vista w/ ubuntu 7.10
-2gb ram , 1.6ghz core duo processor

-want to run office 2007 within ubuntu ... 

is there anyway i can run vista off of my partition within ubuntu? ..or is my best bet installing windows within virtualbox or vmware player... on that note..whats better for the beginner/person in my situation vmware or virtualbox..?

---

### Post by smartboyathome on 2008-03-09
The only virtualization software that I know of that will do this is VMWare, and I don't know exactly how.

---

### Post by saj0577 on 2008-03-09
Office 2007 not work in wine so you will have to use Virtualbox which is a bit more resource greedy but worth it.

Saj

---

### Post by saj0577 on 2008-03-09
Virtual machine runs the whole os in a windowed program. The virtual machine thinks it is a normal boot but it is not and you can restrict its use of resources.

Saj

---

### Post by myddewji13 on 2008-03-09
so do i need to do a clean install of a new windows os...or can i somehow hack it to think its running my installed os?

---

### Post by ghost_ryder35 on 2008-03-09
> **myddewji13 said:**
> Hi,
I love ubuntu but i simply cannot use openoffice. Don't get me wrong... i love the program i just seem to be able to use office 07 a lot more productively....anyway....recently i've been thinking about running a windows virtual machine within ubuntu....during the course of my research i came across people using a partition on their harddrive to boot windows.... but i dont noe how to do this... my current situation is:

-dual booting vista w/ ubuntu 7.10
-2gb ram , 1.6ghz core duo processor

-want to run office 2007 within ubuntu ... 

is there anyway i can run vista off of my partition within ubuntu? ..or is my best bet installing windows within virtualbox or vmware player... on that note..whats better for the beginner/person in my situation vmware or virtualbox..?

VMware still has issues with using Vista from a partition but I know that XP works perfect.  
To set it up you go through the exact same setup procedure as normal except instead of creating a virtual hard drive you say "use physical disk"

---

### Post by myddewji13 on 2008-03-09
is there a how to for this anywhere?

---

