---
title: "Not Booting Up: I'm Getting Sick of This!"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by xshady87 on 2006-03-24
Ubuntu was installed and running (though not without it's fair share of problems) on my computer. Today however, I turned it on, and as it began to load I recieved an error message. I restarted, and got the same thing:

FATAL: Module minix not found.
mount: Mountiing /dev/sda1 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed:No such file or directory

Target filesystem doesn't have /sbin/init

BusyBox v1.00-pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)

Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control off

#



FOR AN OPERATING SYSTEM THAT IS SUPPOSED TO BE SO STABLE, LINUX HAS BEEN CRASHING MORE OFTEN THAN WIDOWS. PLEASE HELP!

---

### Post by dermotti on 2006-03-24
What kernel are you running?

---

### Post by bionnaki on 2006-03-24
what changes to your system did you make before you rebooted?

---

### Post by Horndog on 2006-03-24
Send me a round trip ticket and I'll fix it for you.

---

### Post by flarkit on 2006-03-24
Hi

I had very similar problems recently. I suspect this either happened after I added a 2nd Gig of RAM (which I doubt), or after I changed the HDD mode in my BIOS from 'Auto' to 'Large'.

The odd thing is that when I choose "Recovery Mode" in Grub, the OS will boot to the shell and I can run "startx" happily. X starts and works mostly. I've found that clicking on the majority of the menu items yields an error.

Sooo... I'm seriously considering a reinstall.

---

### Post by xshady87 on 2006-03-24
How do I find out the kernel I'm using? I didn't make any system changes other than running the Automatic Update that popped up on my screen.

---

### Post by Horndog on 2006-03-24
Maybe you should start by telling us something about your computer.

---

### Post by xshady87 on 2006-03-24
SYSTEM SPECS:

Dell Dimension 5100
Pentium 4 3.00Ghz
512 MB RAM
NVIDIA GeForce 6800 Graphics Card

---

### Post by Horndog on 2006-03-24
[QUOTE=xshady87]SYSTEM SPECS:

Dell Dimension 5100
Pentium 4 3.00Ghz
512 MB RAM
NVIDIA GeForce 6800 Graphics Card[/QUOTE]

Are you overclocking? In the grub I would run the program called Memtest86 for at least one cycle to test your ram. If that doesn't work go the the Mentest web site [here]("http://www.memtest.org/") and follow the directions.

---

### Post by pooler on 2006-03-24
Do you have low tension/frequent spikes? Maybe the file initrd.img (needed to boot the kernels that ship with most distros) is damaged. Try booting with a live cd, open a shell (that provides root access) and type:
```
mount /dev/hda1 /mnt (where hda1 is your Ubuntu partition)
chroot /mnt
mkinitrd
exit
```
Then reboot

---

### Post by xshady87 on 2006-03-26
I can't run Live CD, it just dreezes up. And, no, I'm not overclocking. Please help, I'm a real newbie and would like to make the Linux switch, but really need some support. Thanks.

---

### Post by Horndog on 2006-03-26
[QUOTE=xshady87]I can't run Live CD, it just dreezes up. And, no, I'm not overclocking. Please help, I'm a real newbie and would like to make the Linux switch, but really need some support. Thanks.[/QUOTE]

What about the results of Memtest86? This is a test for your ram. If your ram is making errors then it causes corrupt files on your hard drive. You could also have a bad hard drive. Another thing with any Linux OS is they don't like the power to be shut off or a hard reset.

When you post your results you might get more help.

---

