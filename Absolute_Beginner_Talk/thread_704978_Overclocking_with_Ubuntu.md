---
title: "Overclocking with Ubuntu?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by gtirevo33 on 2008-02-22
I have Vista 64-bit and recently switched to Ubuntu and when I overclock with Ubuntu it does not boot. With a mild overclock from 2.6 stock to 2.8 overclocked the computer reboots itself. I have not tried updating the bios from Gigabyte but can that be the problem?

Thanks,

John

---

### Post by LowSky on 2008-02-22
if the PC is rebooting itself  you are not doing something correctly while overclocking

what kind of processor, how are you increasing the speed, front side bus, voltage...what?
Can you RAM handle the change

Did you OC in Windows?

---

### Post by wolfen69 on 2008-02-22
IMO, overclocking is pointless. especially from 2.6 to 2.8. you wont notice any difference. the problems it can create are just not worth it.

---

### Post by gtirevo33 on 2008-02-22
I overclocked in windows to numbers such as 3.6 from 2.6 stock. I ran stable at 3.2 and the ram was set around 800 which is perfect. The voltage and ram settings were set to auto and would boot extremely fine in windows. When I tried overclocking in Ubuntu the system failed to boot and would reboot back to 3.2 and I start off slow with only  2.8 overclock. The cpu I am using is a e6750 which is 2.67gb stock speed and the ram is OCZ platinum 1066 ram.

---

### Post by mbsullivan on 2008-02-22
Hi gtirevo33,

The only real difference between the two operating systems that I can think of is that Linux very aggressively uses memory for file buffers and program caches. 

Buffers are allocated by various processes to read in data, store intermediary results, etc. A large amount of the time, buffers are "file buffers", which store part of a program's output to the disk until it is written. Cache is typically frequently requested disk I/O. If multiple processes are accessing the same file, or if a file is accessed repeatedly, caching the file to RAM will speed up file access drastically.

All of this memory access may stress an overclocked bus past the point that it would remain stable otherwise. So, what I'm saying is... your system might not have been stable under Windows, it's just that you never put enough stress on the (typically fragile) memory bus to notice it.

I don't know, though... Did you ever run Prime95's memory torture tests to check whether your overclocked system was stable under Windows?  Booting into Memtest86 may also provide insight about the stability of your system.

I wouldn't say that overclocking is pointless... it's the computer equivalent to tuning up a car's engine -- no real practical application, but some enjoy it. Increasing the voltage of your memory busses further may solve your problem, but it could also end up burning out your memory, motherboard, or both =/

Mike

---

### Post by gtirevo33 on 2008-02-23
Well, I ran prime and memtest at speeds of 3.2gb and 800 ram stable. I still have to full around with different voltrage ratings but as for now my overclocked windows vista 64bit actually feels slower than my stock Ubuntu 32bit OS. Maybe its just me but I feel like Ubuntu is a lot faster.

---

### Post by mbsullivan on 2008-02-23
What kind of graphics card do you have? If it's NVIDIA, then NVClock has matured a lot over the past couple of years... you could always give overclocking your GPU a shot.

Mike

---

