---
title: "Connecting to the internet"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by epic93 on 2007-12-24
I have a dell inspiron 7500 and I used to run windows 2000, but since my computer has such little memory, and I heard about this thing called swap space that lets you use the hard drive for memory, or something like that, I have switched to linux. Therefore I have to run ubuntu 5.10. I am trying to connect to the internet via dialup using a Xircom cardbus ethernet 100 + modem56, and my ISP is [Intergate]("http://www.intergate.com"). I tried everything I can find, including the "networking" utility and the internet connection utility in the terminal, but to no avail. All I need to know is the settings I should use, If I need to get drivers, and if I will be able to connect to the internet. Thankyou in advance.:KS:KS:KS

---

### Post by bone2006 on 2007-12-24
swap should be used after physical memory is low, how much ram do you have?  I believe the requirements for 5.10 and 7.10 are the same, in which it's 256mb of ram if I'm not mistaken.    I don't use dialup, so I might not be able to help you as well as others, but I would imagine a version that's two years newer might give you less trouble.  

If you have low memory, it's probably better to use xubuntu, minibuntu or another distro that requires less memory than an outdated version such as 5.10 in my opinion.

---

### Post by dnvikram on 2007-12-24
Yes,go ahead and use xubuntu or Fluxbuntu.They are lightweight distros designed precisely for such kind of machines with low end hardware or less memory.That doesnt mean,they run like some cheapskate distro.You gotta see to believe it.They really run amazingly well and will suit to every desktop computing need of yours.Coming to the swap doubt of yours.

First let me tell you in short what swap is used for by the linux kernel.Swap space is a disk space allocated in the hard drive ,its a separate filesystem created suring the installation .Its usually set to twice the size of available physical RAM.So that brings it to 512MB of swap space on ur 256MB ram machine.Donot give more than 700 MB max,alloting anywhere above that is not gonna anyway improve the performance and infact at times it works against the performance.Swapping takes place when a program accessing the physical memory needs more memory to complete whatever its doing and then the linux kernel swaps the memory pages in and out with the current ones from physical RAM to the hard drive.So,effectively its using the hard drive as supplement RAM.But,swapping to a point is ok.If swapping is taking place too often,then it means something is wrong and needs to be tuned immediately as swapping results in high IO and this results in the machine slowing down and the performance decreasing and also the chances of a disk failure increases by 10fold. Just remember this,

Optimal Swap Space=2 x physical RAM

Now the above formula applies to only a limit of 16GB of RAM .After which it doesnt matter or make any difference.As the size of swap space increases,the huge amounts of swapping at such huge quantities add an enormous overheads on the machine and render it ineffective.

---

