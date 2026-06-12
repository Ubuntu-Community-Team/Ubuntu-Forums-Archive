---
title: "openoffice failed to open"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by sabitha on 2005-12-24
i have a problem with my ubuntu hoary 5.04.
everytime i open the OOo it closed self.
than i tried to open from terminal and i get this messenges :

> client@client-05:~$ openoffice -writer
OpenOffice.org lockfile found (/home/client/.openoffice/1.1.3/.lock)
Using existing OpenOffice.org
sh: crash_report: command not found

Fatal exception: Signal 11
Stack:
/usr/lib/openoffice/program/libsal.so.3[0x411a375a]
/usr/lib/openoffice/program/libsal.so.3[0x411a38ea]
/usr/lib/openoffice/program/libsal.so.3[0x411a39b5]
[0xffffe420]
/usr/lib/openoffice/program/libsal.so.3[0x4119881f]
/lib/tls/i686/cmov/libpthread.so.0[0x4116eae0]
/lib/tls/i686/cmov/libc.so.6(__clone+0x5a)[0x410eac9a]
Aborted

i dont understand what is that mean. anybody can help me because OOo -writer is very important to me since i dont use windows

---

### Post by bscbrit on 2005-12-25
A quick browse found this:

The Sig11 FAQ

QUESTION
Signal 11, what does that mean?
ANSWER
Signal 11, or officially know as "segmentation fault", means that the program accessed a memory location that was not assigned. That's usually a bug in the program. So if you're writing your own program, that's the most likely cause. However, this FAQ will concentrate on the possibilities besides that.
QUESTION
My program crashes with

      some kind of error - got fatal signal 11

What is wrong with the program? Which version of the program do I need? Is there something wrong with the kernel?
ANSWER
Most likely there is nothing wrong with your installation, your compiler or kernel. It very likely has something to do with your hardware. There are a variety of subsystems that can be wrong, and there are a variety of ways to fix it. You could be running low on virtual memory.

However, to remove the lock, type the following in a terminal:

sudo rm -f /home/client/.openoffice/1.1.3/.lock

It will ask for your usual, log on password.

This is one of those _rare_ occasions when I would do a system reboot and try again, simply to rule out an Operating System corruption.

Let us know if this solves the problem.

Link: [http://www.bitwizard.nl/sig11/](http://www.bitwizard.nl/sig11/)

---

### Post by bscbrit on 2005-12-25
Its been seen before, but I am still looking for a cure.

[http://clug.ca/pipermail/clug-talk_clug.ca/2005-July/003499.html](http://clug.ca/pipermail/clug-talk_clug.ca/2005-July/003499.html)

---

### Post by sabitha on 2005-12-25
then how i can fix that ?

---

### Post by bscbrit on 2005-12-25
I take it that you did a reboot like I suggested?  What happened?  Do you get exactly the same fault as you did before?

And as I said in my previous post - I am still looking for a cure to your problem.  Have you looked for a cure?  What have you found?  Today, is a big holiday in my country with all my family are gathered together but, even so, I have spent some time looking for an answer to your problem.  When I find one, I will be back here to let you know.

You could try to remove OpenOffice and then to re-install it again.  You might have removed something that it needs by mistake.  Reinstalling it might repair that problem.  But it looks as though it could be a hardware problem.  Perhaps the memory you are using is not quite up to the speed that you are using it.  Perhaps there is a fault on your motherboard.  I am trying to find a way to test all of these things to solve your problem.

Try rebooting and, in the Grub menu, selecting the memory test option - I have it in mine but I cannot remember whether it was a default setting.If you haven't got it, install memtest and we can try to use that.

---

### Post by sabitha on 2005-12-25
ok thanks for the quick replay.....
after reboot it still have the same problem
then i reinstall the OOo, but the same problem i,ve got
then i decided to install OO0-2 that solves my problem
i dont know what is wrong with OO0-1... but i think ooo-2 take too much memory and geting slow on my machine but it's ok
btw.... i want to thank you for your help me understand what the problem 
sorry for my english :p

---

