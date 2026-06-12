---
title: "Error 18 problem"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by jindalee on 2007-05-04
Hi Everyone,
I have just installed ubuntu 6.06 onto a new HD 350 Gb . The system won't boot and gives me an error 18 message. I have searched and know that this means the HD is too big for the bios .

From what I have read it seems that I will need to reinstall 6.06 and manually partition the HD so I have a seperate boot  partition with the kernel and grub files. When I get to the part of the installation where I need to manually partition I don't know what I should do. 

 So far I cannot find any simple step by step instructions on how to go about this, there are dozens on how to dual boot, but I don't want to do that, I only want to run ubuntu. I am totally new with ubuntu and I am hoping someone can send me to a site where I can find simple instructions.

Many thanks

---

### Post by confused57 on 2007-05-04
Here's a couple of excellent guides:
Desktop cd:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Alternate cd:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

What you should be able to do is select "Manual Partition", make a small primary partition of approx. 200 Mb at the very beginning of the hard drive, format as ext3, set the mountpoint as /boot...then make another primary partition of approximately 20 Gb, format as ext3, set the mountpoint as root(/)...make another partition, you might want to make it a logical partition of 1-2 Gb, set the mountpoint as swap, format as swap...then make a logical partition for the rest of the hard drive, format as ext3, set the mountpoint as /home.  If you don't want a separate  /home partition, you can make the root partition all but 1-2 Gb, but I think you'll have better results on such a large hard drive by having a separate home and a smaller root partition.

I always use the alternate install cd, so I'm not sure exactly what the screen selections are with the live cd, but this should give you some idea of what you need to do...especially after checking out the links above.
You might want to wait on someone else more experienced with partitioning, but thought I'd offer my 2 cents.

---

### Post by jindalee on 2007-05-06
Hi, 
Thanks very much for your reply and help, much appreciated.

---

