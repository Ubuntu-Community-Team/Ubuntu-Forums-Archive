---
title: "amilo L7300 install problem"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by geemcd on 2008-03-10
Hi there, 

I have this old laptop which was a gift from a friend. It came with XP which I'm frankly sick of but wish to keep on it's own 20Gb partition. I'm trying to install Ubuntu on the other 20Gb partition but keep running into errors along the lines of SMPtable errors detected, bios bugs and MP table error, then get send to a prompt saying intramf$:

I get this problem wether trying to install from live cd (ubuntu 7.4, 6.06 LTS, and Kubuntu 6.06), via a network and via an installer that works from within windows called wubi. All these methods give the same result.

Now I do have a working familiarity with ubuntu but only as a user - surfing the net and the like, but none of the command line stuff.. I'd like to know if anyone can help me sort this out even if it requires technical stuff as I'd like to learn about Linux and how to use it properly.

Just hoping I haven't picked the only laptop in the world that is Linux proof.

Thanks in advance for any advice.

Glenn

---

### Post by bren on 2008-03-11
Glenn

I'm no expert but....

1) if its old then then amount of RAM may be limited so use an "alternate CD" to install
I believe 256MB is minimum requirement for 7.04 LIVE CD install...you can check actual via <sysinfo> in XP

2) If SMPtable means Something Master Partition Table then I can recommend a small utiltiy called Testdisk as good for sorting these types of problems out

Search for System Rescue Live CD and Testdisk and you will find it

Don't give up yet.....somebody with better info than me will come along soon

bren

---

### Post by geemcd on 2008-03-11
Bren,

The system has 512Mb RAM so it's not that. I have also tried the alternate install CD to no avail.

Testdisk comes back all present and correct, but it did help me fix a flash stick that had mysteriously shrunk from 1Gb to 712Mb...

What is the system rescue live CD exactly and can I find it on bittorrent?

Thanks for the advice.

Glenn

---

### Post by geemcd on 2008-03-12
Ok I've been trying something called knoppix software collection. It starts fine from the dvd and gets to a screen with a penguin and

boot:

so I type knoppix like it says and get this

loading linux.......
kernel 2.6.24
total memory 448064
enabling dma accelaration hda
enabling dma acellaration hdc
can't find knoppix filesystem
dumping you to busybox
/static/ash: cant access tty; job control turned off

and the prompt

/#

is this information any good?

Glenn

edit: I'm assuming hdc is the dvd drive so maybe dma accelaration is the issue and maybe there's a way to switch it off??

---

