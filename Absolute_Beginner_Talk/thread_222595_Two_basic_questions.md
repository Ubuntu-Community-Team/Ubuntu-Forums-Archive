---
title: "Two basic questions"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by jmilane on 2006-07-25
Hi, 

I have two questions that are probably quite easy, but they are important in my understanding of Ubuntu.

1. Can someone tell me the criterion that determine what programs are available for adding and removing in add/remove programs versus which require the package tool for addition and removal? I know that it has something to do with dependencies, but I am not entirely clear on it. 

2. When I installed Ubuntu, I split my already small 13 MB drive into two 6.5 MB partitions. I dont know why I did this besides that it was the default configuration. Can I remove the partition without messing everything up? A related question: how hard would it be for me to mount an additional hard drive? Windows is (essentially) plug and play. Is Linux the same in this regard or am I looking at an unfamiliar process that I should consider more seriously?

Thank you!!!

JD

---

### Post by halfvolle melk on 2006-07-25
Hi,

If a program is in one of the [repositories](https://help.ubuntu.com/community/Repositories) you can add/remove them with the tools provided by Ubuntu. It will fix dependencies for you. If you download a <package>.deb it can be installed with dpkg. It does not check for dependencies. The first method is the prefered one.

I think you mean 13GB (?). If the second partition is empty it can be removed and the empty space can then be added to the first partition using Gparted from the live cd, or [mount your /home directory on it](http://psychocats.net/ubuntu/separatehome.html). Leave swap as it is.

Adding an extra drive can be done by [mounting](https://help.ubuntu.com/community/Mount) it. This can be done [automatically](https://help.ubuntu.com/community/AutomaticallyMountPartitions) using /etc/fstab as mentioned in the previous link.

Hope this helps.

---

