---
title: "apt-get not working"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Muthuraman on 2007-10-24
Hi all,
           I have recently installed Ubuntu and it is working good.  I noted that the speed is not the same to which I am used to in other OS.  Being a newbie I tried Google and found some methods to improve speed (like making DMA 'ON').  I simply followed the example scripts given in those messages. I still find that the speed can be improved.  I found that if the kernel is compiled on the target computer the speed will increase and apt-get will install the new kernel . I am using AMD Athlon and a Google result showed K7 is the kernel to be used for better Ubuntu   performance. I use Ubuntu Fiesty Fawn.  When I give apt-get install  command it ssays the following message.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-k7

          Not only for kernel, for anything I tried , apt could not get the packages, same kind of messages appear.  Do I need to configure or install apt-get again?

Thanks in advance.
S.Muthuraman.

---

### Post by Hospadar on 2007-10-24
you should have a look at your software sources (Administration->Software Sources), also try browsing around in synaptic (Administration->Synaptic), oftentimes packages will have slightly different names than you might be expecting.

---

### Post by aysiu on 2007-10-24
That kernel is listed as obsolete:
[http://packages.ubuntu.com/feisty/base/linux-k7](http://packages.ubuntu.com/feisty/base/linux-k7)

---

### Post by Muthuraman on 2007-10-24
Thanks.
      I do not know why they gave K7 as AMD kernel. I tried again by keeping the install/LiveCD CDROM and giving "apt-CDROM add" (of course , Googled) . Then I issued  'apt-update', again . Apt tried to connect to a web site but it never ended up. What to do to make connect to the correct site ?

 (How to check for new Kernel with synaptic, it shows only existing kernels with Mark for delete/upgrade options only.)

Muthuraman.

---

