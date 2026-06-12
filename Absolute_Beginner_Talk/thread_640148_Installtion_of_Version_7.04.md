---
title: "Installtion of Version 7.04"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by DarkRookie on 2007-12-13
I did install version 7.04 after being told that version 7.10 won't run on my laptop.
I try to boot up and get a blank screen.
I try to start up in recovery mode and the last 5 lines it gets to before it hangs up are:

[   13.669975] ENABLING IO-APIC IRQs
[   13.670275] ...TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   13.816851] checking TSC synchronization across 2 CPUs:
[    0.000045] CPU#0 had -206 usecs TSC skew, fixed it up.
[    0.000097] CPU#1 had 206 usecs TSC skew, fixed it up.

I have a HP Pavilion dv6406nr
120 Toshiba HardDrive
1 GigaByte 533 MHz DDR2 memory
AMD Athlon 64 x2 1.8Ghz tk-53

bah thats all the hardware I can think of now

---

### Post by Nano Geek on 2007-12-14
Are you sure 7.10 won't run on your laptop? HPs are fairly well known for their Linux support. 
Since you don't have anything to lose, why not try it?

---

### Post by siciliancasanova on 2007-12-14
I second that you try 7.10.  Are you running the live cd and if so is it detecting all your hardware?

---

### Post by DarkRookie on 2007-12-14
Trust me I have tried.
Try booting to the live 7.10 CD 16 hours later still hadn't booted up
No joke.
The 7.04 works fines as long as I add the 
noapic noapci nosplash --
at the end of the boot option.
Tried that with 7.10 and also without modifying anything and still never booted up.

I believe that 7.10 would hang up at something called microcode. I don't know for sure though

I have the live CD going right now. I can see the install I made. It is name disk which is the default name I believe.
Also a little off this topic but can any point me to a post telling me how to mount a NTFS usb hard drive. I would greatly appericate that.

---

