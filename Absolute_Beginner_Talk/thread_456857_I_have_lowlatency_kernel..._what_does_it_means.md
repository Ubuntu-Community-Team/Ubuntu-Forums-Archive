---
title: "I have lowlatency kernel... what does it means?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by chinaski on 2007-05-28
after upgrading kernel versions through Synaptic I run 'uname -a' and I get this:
 
> acp@central:~$ uname -a
Linux central 2.6.20-16-lowlatency #2 SMP PREEMPT Wed May 23 01:49:41 UTC 2007 i686 GNU/Linux
 
what does lowlatency means in this case?
 
is there something wrong?

---

### Post by Brynster on 2007-05-28
It simply means you are running the the 64 bit kernal.

Nothing wrong or to worry about

---

### Post by mcduck on 2007-05-28
Lowlatency kernel is part of the Ubuntustudio's audio setup. It means that the kernel is gives 95% of CPU time to currently running program, allowing audio applications to run in almost real time. Low latency kernel is good for audio recording and such tasks, but in normal desktop use I recommend choosing the normal kernel from Grub menu instead, as it handles running multiple applications at the same time better than the lowlatency version does.

edit: from wikipedia: Latency (engineering), a time delay between the moment something is initiated and the moment its first effect begins. 
Latency (audio), the time delay in digital audio systems due to analog to digital conversions, processing and conversion back to analog.

When you are doing tasks like audio recording, or live playing, you want as little latency as possible. That's why many Linux audio applications should be used with a lowlatency kernel.

---

### Post by tkjacobsen on 2007-05-28
the lowlatency kernel will make the desktop feel more responsive, all tough the overall performance will be slower.

---

### Post by chinaski on 2007-05-28
thank you all guys ;)

I commented out the lowlatency kernel lines in /boot/grub/menu.lst and I have old nice generic kernel loaded :D

cheers,
chinaski

---

### Post by DJ Wings on 2007-05-28
Low-latency is also good for gaming, as it devotes more power to the program currently running.

---

### Post by Gen2ly on 2007-05-28
> **chinaski said:**
> thank you all guys ;)

I commented out the lowlatency kernel lines in /boot/grub/menu.lst and I have old nice generic kernel loaded :D

cheers,
chinaski

uhhh

---

### Post by DJ Wings on 2007-05-28
Err... Unless you have a normal kernel installed as well, that's not going to work...

---

### Post by chinaski on 2007-05-28
> acp@central:~$ uname -a
Linux central 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686 GNU/Linux

;)

as I don't do gaming nor I am a musician (I'd installed Ubuntustudio just for curiosity) I do not need lowlatency kernel, I think

---

### Post by zettberlin on 2007-05-28
> **chinaski said:**
> ;)
 (I'd installed Ubuntustudio just for curiosity) I do not need lowlatency kernel, I think

Well, OK - but if you are curious you may want to try one or the other soundapp that comes with Ubuntustudio. The most of these soundapps need to have a lowlatency-kernel running or they will perform poor at best or do nothing at all.

BTW: I used lowlatency-kernels on about 10 different machines now and did not recocnize *any* drawbacks compared with the performance of a generic kernel. For a system, that is used typically by one user  at a time and does not provide a webserver or a mysql-daemon with dozens of users using it, it is perfectly a good choice to have a lowlat-kernel running. Only on Laptops there is some trouble for it allows the user to make the CPU work much harder and thus the batteries may be emptied earlier.
And you can run dozens of cool apps, that do not work OK with a generic kernel.

---

