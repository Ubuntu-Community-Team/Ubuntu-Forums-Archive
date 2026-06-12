---
title: "Ubuntu hangs right after grub"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by chrisdee on 2007-07-29
Hello. Now I need help. Im running mail, web and backup(via samba) on my Ubuntu 6.0.6 and it has worked fine for months. Im only running Ubuntu, no dualboot.

But now its crisis. Ubuntu hangs during boot right after Grub and I get the following message : 

Booting `Ubuntu, Kernel 2.6.15-28-386`
root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
Kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/sda1 ro quiet splash
[Linux-bzImage, setup=01c00, size=0x157a47]


What does this mean, and what can I do to fix it ?

---

### Post by 505 on 2007-07-29
You always get that message. It just is a message that the Linux kernel is being loaded. To see the actual error message (or where is hangs), edit Grub. When Grub loads press 'e', then edit the second line and remove 'quiet slash'. Then press 'b' to boot. You now should see a lot of text, and you can diagnose where is halts.

---

### Post by Koybe on 2007-07-29
If you have multiple kernel on grub try booting an older one to check.

What's strange is I cannot see any error... You got nothing else?

---

### Post by chrisdee on 2007-07-29
Thank for answer. Iv tried what you said, but it still hangs at the same place.
I can se in the grub setup that I have 3 different versions/kernels + 3 different versions of recovery mode.

Im afraid non of them work. I manage to enter schell/text modus from the grub menu.
is there anything I can do from here ?

What do I do now ?

---

### Post by Koybe on 2007-07-29
505 had a good idea, did you tried it? Does it give more information?

---

### Post by chrisdee on 2007-07-29
Yes. I tried to remove the quiet slash, and then push b for boot, but
It still hangs on the same place. What do I do ?

---

### Post by chrisdee on 2007-07-29
Any ideas anybody.

---

### Post by chrisdee on 2007-07-29
Now I actually managed to remove the line ro quiet slash,  and push b for boot.
I got a lot of text running so fast over the screen that I couldnt read everything.

How do I determin if there are errormessages ?
Is there a log somewhere ?

---

### Post by Koybe on 2007-07-29
You said texte is going quick. But if your system does not start it should block at a moment. Then what's on screen at that moment.

Logs are int /var/log/syslog and /var/log/dmesg but if you cannot access your system, it won't help.

---

### Post by chrisdee on 2007-07-29
In some strange way my ubuntu server started. I dont understand anything.
Now am afraid to restartet again if it hangs.

---

