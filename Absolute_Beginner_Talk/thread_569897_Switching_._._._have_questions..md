---
title: "Switching . . . have questions."
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by P373 on 2007-10-07
Hello!

I've been using microsoft my whole life and have been tempted to switch to mac or linux for a while, always testing the waters. I have so far burnt three live CDs and have decided to install ubuntu.

I am running an intel based laptop with wireless built in and running with windows XP. It is a dell with dell preboot softare (including a fingerprint scanner).

I just have a few questions:

Using the live CD is there a way to install a dual bootable computer (one that will boot both my current OS and ubuntu?) without deleting my currently stored data on my hard drive?

Can I install photoshop somehow onto the ubuntu?

Thanks

---

### Post by skymera on 2007-10-07
yes, when you come to install you can install on seperate partition.
and GRUB menu lets you choose

*buntu -> Windoze


you can trey and Wine photoshop, although dosent work for me

---

### Post by kellemes on 2007-10-07
For dualboot info..
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

For Photoshop on GNU/Linux see [http://appdb.winehq.org/appview.php?appId=17]("http://appdb.winehq.org/appview.php?appId=17")
or try to use a Virtual Machine like [VirtualBox]("http://www.virtualbox.org/") to get it going.. should be working alright as far as I know.

---

### Post by Jeroen Vernooij on 2007-10-07
You need to shrink your existing windows partition to make space for a linux partition so you can install it besides windows.

Photoshop cs2 works perfectly, howto's are all over the internet.

---

### Post by HermanAB on 2007-10-07
If you have never used a Unix system before (Macintosh, Linux, Solaris...), then I suggest that you download a bunch of live CDs from various Linux distributions and try them all, before you install Linux.  Typically, if the live CD works properly, then that distribution will work properly once installed.

The safe way to do things, is to first defragment Windoze, then shrink its partition using Gparted from a live CD, then install Linux into the empty space.  Linux will then make your machine dual boot Windows/Linux.  Some distributions will do all of that for you very reliably - others won't. Ubuntu unfortunately is in the won't category, so bear that in mind - with Ubuntu, you have to manually shrink the Windoze partition before you click the install button!

Cheers,

H.

---

