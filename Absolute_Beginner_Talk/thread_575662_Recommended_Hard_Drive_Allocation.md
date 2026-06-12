---
title: "Recommended Hard Drive Allocation?"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by ajunta.pall on 2007-10-14
I'm looking to install either Ubuntu or Kubuntu on a virtual machine, but hard drive space is a slight issue. (56 Gigs available, but being that its a new laptop, that will decrease quickly.)  Can anybody recommend how much hard drive space I should allocate for each?  (I intend to have some graphic editing programs, a few games, any music editing software out there, Openoffice or Koffice, and whatever else can help me become a better Linux user.) :guitar:

Also, any advice on which I should install would be MOST appreciated.

Thanks,
Brian

---

### Post by jdong on 2007-10-14
Both utilize a bit over 2GB by default install, but for breathing room I'd recommend at least 3GB for the OS, plus any space you need to store personal files, so probaby 5GB for the average user?

---

### Post by vanadium on 2007-10-14
For a laptop, and in particular with limited drive space, I would recommend no else than just one single root partition containing all the data (including /home) and a swap.

---

### Post by jdong on 2007-10-14
> **vanadium said:**
> For a laptop, and in particular with limited drive space, I would recommend no else than just one single root partition containing all the data (including /home) and a swap.


He is planning to do an install in a virtual machine, which probably won't even need swap. But you are correct, he should be using a single / partition. Worst comes to worst and he realizes he needs swap, he can always create a loopback swap file.

---

### Post by deserthowler on 2007-10-14
> **ajunta.pall said:**
> I'm looking to install either Ubuntu or Kubuntu on a virtual machine, but hard drive space is a slight issue. (56 Gigs available, but being that its a new laptop, that will decrease quickly.)  Can anybody recommend how much hard drive space I should allocate for each?  (I intend to have some graphic editing programs, a few games, any music editing software out there, Openoffice or Koffice, and whatever else can help me become a better Linux user.) Brian

I used Virtual Box.  It allows dynamically allocation or something like that.  The virtual drive expands until it fits the allocated space but won't use any more space than needed.  This way I can set large partitions (total is larger than hard drive) and not really worry about them all eating up the drive.  My Win2K partition, for example, has 10 GB allotted but uses only about 2 GB unless I start adding things.  With the programs I added, it's up to about 2.5 GB added.

I use Ubuntu but make money solving Windows problems.  I work on Windows versions enough to know I don't want it for my personal/production work.

Earl

---

### Post by jdong on 2007-10-14
Most virtualization software out there behave the same way (sparse files) but it's still a good idea to set a maximum cap that's representative of how much space you expect the OS to use, to prevent a denial-of-service issue to the host of the guest manages to misbehave for some reason.

---

