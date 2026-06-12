---
title: "virtualbox and pre existing os installed"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by naseem on 2007-04-12
hi
do you know if it's possible to use an existing os installed to be run as guest via virtualbox, or in other words not from the creation of a folder from vb but just using the os already installed in another disk?

---

### Post by chris062689 on 2007-04-12
What you want to do is boot a VM that is also on your main computer on a different partition(for dualbooting?)  I'm not sure realy...  You'll have to wait untill someone else comes along.

---

### Post by adamklempner on 2007-04-12
From what I have heard is that you cannot currently do this with VirtualBox, but it is on the list of things they want implement.  I think VMWare might have this ability though.

---

### Post by naseem on 2007-04-12
thanks
yes I think it's not implemented yet in virtualbox

---

### Post by Patrick K on 2007-04-12
It is possible with VMServer (free). They have a virtulizer program (also free) that makes a copy of your already installed OS and this can be run in the VMServer.

---

### Post by Abdi110 on 2007-04-21
[http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition](http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition)

---

### Post by Mr. Picklesworth on 2008-01-11
This thread seems rather highly ranked on Google, so I should set the record straight before anyone gives up hope.

Virtualbox 1.5 lets you run from a physical partition!
[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

That is in the Ubuntu (7.10 / Gutsy) repositories. There is also a deb on the VirtualBox web site, which I am using right now. Still untested by me. I will post back here when I have a screenshot of how I will never need to boot into Vista without the comfort of Ubuntu *at least somewhere* again

---

