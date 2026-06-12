---
title: "Ubuntu hanging on HP V6000"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by inverness on 2007-05-31
I am trying to use Ubuntu on a Compaq/HP Presario V6000 laptop (100 gig disc, 1028 G ram, AMD 64 Turion x2 processor, 30B7 board) that had come with Vista and numerous proprietary drivers. It goes through installation well enough, and once I made it into the actual loaded and running Ubuntu screen, but it froze. I have reinstalled several times with 7 (alternate ISO) and 6 (from the dvd attached to Keir Thomas's book), and have changed x.org (trying to get around nvidia with simpler graphics). At this point I am sure there is a problem beyond the graphics, which I was after all able to see clearly enough when they loaded, as besides the great difficulty of loading there are frequent hangings. Sometimes it makes it past the orange bar to hang in darkness, sometimes in recovery it doesn't get to the command line. I am going through Thomas' book "Beginning Ubuntu Linux" and not seeing much that both specifically looks like my problem and works. I'm new to Ubuntu, Linux and computers in general but wanted to be rid of Vista a little too early it seems.

---

### Post by pappapump on 2007-05-31
Are you using the amdx64 Ubuntu install?

---

### Post by jazzz337 on 2007-05-31
Having a very similar issue on my laptop also a hp v6000
and no I do not belive that I'm using the amdx64 install 
if this will solve my issue I will try it my laptop get past the load up every time and then the monitor go's white .

---

### Post by emperon on 2007-06-02
you should boot with noapic option. In the grub select the kernel end press 'e' to edit the line. And add noapic to the end of line

---

### Post by inverness on 2007-06-02
Sorry for tardiness; indeed I am able to sort of get it to load properly with a version noapic from Thomas' book. I am using the general 6th version from the dvd, having started with the amd64 alternate of version 7 but grown suspicious of my burn of it. 
With this setup things work somewhat stably enough to use, although not as smoothly as I'd like, and it seems there are no other problems (that is once you get to the big orange screen).
It seems to have problems with powering up and down -- it has never turned itself off except from a reboot command in recovery, all powers down have been hard. The monitor sort of goes out and then it stalls in limbo. Powering up works every eighth time. Could this be something with grub or that could be solved with amd64 alternate iso of version 7 using the noapic? (Right now I am trying to get a broadcom driver to work so that I can get some libraries for Windows media, assuming I can get it up again.)

---

### Post by emperon on 2007-06-04
I am running HP pavillion dv6000 with full success (except hibernate) in 32 bit edition. I also suggest you to go for 32 bit. 64 bit is only useful for then needs of 4GB+ ram. There is a wiki page for dv6000. Search out wiki.ubuntu.com

---

