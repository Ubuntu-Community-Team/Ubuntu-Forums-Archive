---
title: "Ubuntu doesnt start"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by fgtz on 2007-05-03
Hi,

I have just installed Ubuntu 7.04, the problem is that the system doesn't boot, it just stays at the Ubuntu splash screen, after about 5 minutes the screens shows this message:

[INDENT][FONT="Courier New"]udevd-event[1945]: run_program: '/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-3-ubuntu3) Built in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control turned off
(initramfs)
[/FONT][/INDENT]

I'm new to linux and I don't know what to do.
Thanks in advance for your help.

---

### Post by fgtz on 2007-05-03
Well, after searching I found that a lot of people is having [_this problem_]("https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964")

one solution tells to add

[INDENT]libata
pata_jmicron
ata_piix
ahci
ata_generic[/INDENT]

to /etc/initramfs-tools/modules, however I don´t  know how to do that, how can I edit the file if the system doesn´t boot, any help is welcome.

---

### Post by vishagan on 2007-05-03
i'm having the same problem as fgtz. Booting from both the alternate CD or the feisty kernel from my HDD gives the same result: 
**abnormal exit and job control turned off**. 
Theres no problem with Live CD; thats how i installed feisty on my HDD. I don't have SATA on my motherboard and i run P4 non-HT, so i think the jmicron workaround would not work for me as far as i have read on the forum [correct me if i'm wrong].
I've read [_here_]("http://ubuntuforums.org/showthread.php?t=415339&page=2&highlight=abnormal+exit") that switching the kernel to 2.6.15-28-386 from 2.6.15-28-generic solves the problem. How do i install the 386 kernel on my buggy system without using edgy? If that is possible.

Thanx for your help in advance.

---

