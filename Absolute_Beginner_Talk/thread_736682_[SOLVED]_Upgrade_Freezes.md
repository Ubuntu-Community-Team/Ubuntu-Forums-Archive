---
title: "[SOLVED] Upgrade Freezes"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by ockron on 2008-03-26
Hi all and sorry if I ask stupid questions.

After thinking about it for a long time I finaly created a dual boot on my old XP desktop and loaded Feisty from the CD.

It worled like magic and I absolutely love Ubuntu.

I made sure that everything was updated ... AND then I hit Upgrade to Ubuntu 7.10

All went well ... no error messages untill I had to reboot.

It took about 10 minutes to boot untill there was about 1/4 of a bar left and there it got stuck ... After 30 mins I did a hard reboot.

This time it loaded like a dream, to the same place and froze there again.

HELP PLEASE!!

Thank you.

---

### Post by codeslicer on 2008-03-26
Could you switch to the terminal using Ctrl+Alt+F1?

---

### Post by codeslicer on 2008-03-26
You might have to do this as soon as you see the splash screen. Post the last thing Ubuntu tries to do...

---

### Post by ockron on 2008-03-26
> **codeslicer said:**
> Could you switch to the terminal using Ctrl+Alt+F1?

When do I try that?
When it starts booting or when it freezes?

---

### Post by codeslicer on 2008-03-26
When it starts... then when you think it froze, look at the last line on the list

---

### Post by ockron on 2008-03-26
I have tried Ctrl+Alt+F1 when it freezes without any success.

When I boot using the option "Ubuntu 7.10 kernel 2.6.22-14-generic (recovery mode)" ....
This is the last few lines of code:

> * Checking file systems...
fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005 FAT32, LFN
/dev/sda4: 4629 files, 1294028/1897754 clusters

* Mounting local filesystems...			[OK]
* Activating swapfile swap...			[OK]
$Mounting securityfs on /sys/kernel/security: done.
Loading AppArmor profiles : done.
* Checking minimum space in /tmp...			[OK]
* Configuring network interfaces...			[OK]
* Starting portmap daemon...			[OK]
* Starting NFS common utilities			[OK]
* Setting up console font and keymap...		[OK]
root@desktop:~#

---

### Post by codeslicer on 2008-03-27
Why are you booting using recovery mode? :confused:

---

### Post by PmDematagoda on 2008-03-27
> **codeslicer said:**
> Why are you booting using recovery mode? :confused:

So that he could find out where exactly Ubuntu gets stuck, of course you can do the same thing by just putting nosplash as a boot parameter but you can boot Ubuntu in Recovery Mode if you want it fast.

@ockron, when Ubuntu finishes booting in Recovery Mode can you start the X-Server successfully using:-
```
sudo startx
```

---

### Post by ockron on 2008-03-27
Thank you so very much.

At least I can now complete the boot sequence, but because I boot in recovery mode I cannot set up my wireless or any other network functions ....

Please help me fix it to boot as is should.

---

### Post by ockron on 2008-04-01
Thanx to everyone that tried to help.

I could not upgrade ... even once I got the CD.
I tried installing Gutsy but without any success.

I am back using Feisty and love it !!

---

