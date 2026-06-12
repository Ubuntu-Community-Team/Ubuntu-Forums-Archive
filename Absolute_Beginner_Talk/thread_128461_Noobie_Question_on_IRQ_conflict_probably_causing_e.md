---
title: "Noobie Question on IRQ conflict probably causing extremely slow internet"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by SigMtnDawg on 2006-02-11
I have looked and looked for an appropriate thread to solve my problem, but I just haven't found one.  If there is one, and I missed it, I apologize for the duplicate.  As the title suggests, I am very much a noobie to Linux.  I actually have several problems with the install to workout, but I am trying to go one at a time.  I'm starting with this one, because without decent internet access on the Linux box, the other problems are more difficult.

To the problem.  I can connect to the internet, but the speed is so slow that it took well over a minute to load the Google page (probably pushing two mins).  When I look at a command window, I keep seeing variations of the following:

irq 3: nobody cared (try booting with the "irqpoll" option.
handlers:
[<caa7428e>] (ei_irq_wrapper+0x0/0x2d [pcnet_cs])
Disabling IRQ #3

then that message repeats.  there are a bunch of numbers before each line, too.

What in the world am i doing wrong?  and, how can i stop these messages?  they seem to absolutely hog the machine.

thanks in advance for your help.

---

