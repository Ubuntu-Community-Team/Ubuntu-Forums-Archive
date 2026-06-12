---
title: "Dual Booting Vista Home Premium and Ubuntu 7.04"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by blent87 on 2007-05-14
Alright, I am completely new to Ubuntu and Dual Booting.  I have looked around on the forums for what I am trying to do, but have not found a definitive step by step guide.  I want to dual boot Vista and Ubuntu, without losing any of my existing data from Vista.  Right now I only have the one partition that vista is installed on.  Is there a step by step guide to show how to do this anywhere?  I found one [[COLOR="Red"]here (link),[/COLOR]]("http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx") but it only refers to using the Vista Beta DVD to freshly install vista, not keep existing information.  Please help me do this, I want to start using Ubuntu on my laptop!!!!!

Brian

---

### Post by skwishybug on 2007-05-14
Try here: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

There are a number of other good tutorials there as well including how to partition your drive and where to go after it is installed.

---

### Post by blent87 on 2007-05-14
I was under the impression from what I had read previously that the GRUB bootloader did not recognize vista and would mess it up (or is that for the previous versions of Ubuntu)?

---

### Post by bobplano on 2007-05-14
the only thing GRUB can really do is get rid of your windows mbr. as for it not recognizing vista you can add an entry to the grub list so then it should boot to vista

---

### Post by blent87 on 2007-05-14
Alright, I think the link that was given to me will help a great deal.  Hopefully I will be up and running linux before I go to bed tonight!!!!  Thanks a bunch for the help guys.

---

### Post by confused57 on 2007-05-14
Be sure to use the Vista "builtin" partitioning tool to shrink your Vista partition, don't use the Ubuntu install cd to shrink your Vista.

---

### Post by blent87 on 2007-05-14
> **confused57 said:**
> Be sure to use the Vista "builtin" partitioning tool to shrink your Vista partition, don't use the Ubuntu install cd to shrink your Vista.

That's one of the problems I'm running into.  I have 20 GB free on my laptop hard drive, but I can only shrink the partition that vista is installed on by 3 GB.  I am not sure how to get it to shrink more.

---

### Post by confused57 on 2007-05-14
You might need to defrag your Vista partition, possibly a couple of times?

---

### Post by blent87 on 2007-05-14
It's getting better.  I'm running a defrag on my drive now.  It's 30% done and now I can shrink the partition by 7 GB.

---

### Post by blent87 on 2007-05-14
> **confused57 said:**
> You might need to defrag your Vista partition, possibly a couple of times?

You beat me to it by a hair!!!!

---

