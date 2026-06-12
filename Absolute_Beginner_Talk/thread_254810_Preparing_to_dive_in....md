---
title: "Preparing to dive in..."
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2006-09-10
Hi!  Over the past few months, and more recently in the past few days, I have been asking questions on here to figure out how Ubuntu will work in my situation.  I just roasted (thanks to some help a fresh Dapper disk, and I was reasured that Ubuntu is the distro. for me.

I've spoken to my professors, and apparently from the second year of CS on, it is all Unix based stuff.  For this semester, though, we are using Visual C++ .NET Express Edition, and we are going to study C++ from the stand-point of building Windows programs (so, no  Ubuntu this semester).  Apparently next semester might be the same, but then Java starts being used at some point, and that is totally multi-platform.

By Christmas or Thanksgiving, I would like to have Ubuntu installed so that I can become acustom enough to it that doing class work isn't terrible in the way of learning too many new things.  I need to do this over vacation, because if I  botch it, the recovery will take forever (16 disks).

Here is how my system is set-up:
1. It is an HP Pavailion a1530y.
2. ~127 Gb of free disk space
3. 3.0 Ghz Pentium 4 processor
4. 1 Gb of RAM.
5. An ATI Raedon Express graphics card.

Here is my plan of action:
1. Boot the LiveCD, and select "Install".
2. Allow Ubuntu to partion the hard-drive and do its thing.
3. Download and run "Easy Ubuntu" so that it downloads and enables the correct ATI drivers (among other things).

...And here are the concerns that I have:
1. Will Ubuntu automatically boot generic graphics drivers when I install it like it does when I run the LiveCD, or will I be in trouble?

2. Like all HP computers, mine comes with the HP "boot optimizer", some quirky recovery stuff, and a recovery partition.  If let Ubuntu auto-partition the hard-drive, will it be able to navigate these difficulties?

3. Will installing Grub be safe on my HP computer (safe for my windows install, I mean)?

4. Will running EasyUbuntu really install the drivers and stuff that I need?

5. Should the drivers fail to work, could someone give me detailed instructions on how to revert to the pre-Easy Ubuntu stage (bear in mind that I know nothing about using the terminal)?

Thanks. :D

---

### Post by Najand on 2006-09-10
> **Darklighter137 said:**
> 

...And here are the concerns that I have:
1. Will Ubuntu automatically boot generic graphics drivers when I install it like it does when I run the LiveCD, or will I be in trouble?

They are identical... So there won't be any problem, I believe. Ubuntu can detect even ntfs which Fedora does not support.
> 
2. Like all HP computers, mine comes with the HP "boot optimizer", some quirky recovery stuff, and a recovery partition.  If let Ubuntu auto-partition the hard-drive, will it be able to navigate these difficulties?

It will not delete the recovery partition.
> 
3. Will installing Grub be safe on my HP computer (safe for my windows install, I mean)?

Grub is safe. It won't hurt your windows and even if it cannot detect your Windows Partition (which is very unlikely) it is very easy to edit it to detect it.
> 
4. Will running EasyUbuntu really install the drivers and stuff that I need?
Hmm, better to  check it with the documentations. Usually ubuntu can detect almost all common drives.... Some which even Windows cannot detect... So better to  check it up if they work or notbefore installing Easy Ubuntu. 
> 

5. Should the drivers fail to work, could someone give me detailed instructions on how to revert to the pre-Easy Ubuntu stage (bear in mind that I know nothing about using the terminal)?

Thanks. :D
People here are always kindly help eachother... Don't hesitate to ask anything you wanna know.

---

### Post by Darklighter137 on 2006-09-10
Okay, thanks! ^_^

---

