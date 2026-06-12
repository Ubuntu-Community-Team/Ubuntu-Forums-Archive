---
title: "ububtu on ibm intellistation m pro"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by newlifer on 2007-08-23
a warm hello to all :)

I'm an absolute beginner in ubuntu and yestersay I tried to boot the ubuntu 7.04 live cd to check it out
my pc is an ibm intellistation m pro intel pentium 4 with the nvidia quadro fx graphics card

so when I try to boot the live cd I get the following errors:

/bin/sh: can't access tty; job control turned off
(initramfs) ata300: failed to set xfermod (err_mask=0x40)

is there a way I could get around these errors and boot the live cd?

thanks in advance

---

### Post by Inxsible on 2007-08-23
What speed did you burn the iso image? Not that this is your problem per se, but CDs burnt at high speeds often produce weird errors.

Recommended speeds are 4x or less

---

### Post by newlifer on 2007-08-23
I've tried a lot of different burns at slow speeds but this doesn't solve the problem, unfortunately

---

### Post by A3sthetix on 2007-08-23
When booting up, do you get to the options menu? (ie. Install, boot from CD, Advanced Options, etc). If you do, press F6 and add the following to the text:

> NOAPCI

Try booting into the live CD.

---

### Post by A3sthetix on 2007-08-23
Also try:

> IRQPOLL

That might get you booted. Check this thread out:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112132](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112132)

---

### Post by newlifer on 2007-08-23
thanks for the quick response

I've tried both commands and the live cd doesn't work, it gives the same errors :(

/bin/sh: can't access tty; job control turned off
(initramfs) ata300: failed to set xfermod (err_mask=0x40)

---

### Post by rickycodie on 2007-08-23
i'm having the samr problem but on a lenovo r61i laptop. i''ll continue looking.

---

### Post by newlifer on 2007-08-23
bump

---

### Post by ErusGuleilmus on 2007-08-23
I beilive the command is NOAPIC not, NOAPCI

---

### Post by rickycodie on 2007-08-23
i got it to work in bios i had to go under the config screen and set the hdd to compatible and the monitor to lcd from vga. i don't know if it will work on a desktop but good luck, i'll keep looking for you.

---

