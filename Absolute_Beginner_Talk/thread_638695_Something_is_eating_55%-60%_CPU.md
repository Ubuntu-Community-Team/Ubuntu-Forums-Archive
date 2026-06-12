---
title: "Something is eating 55%-60% CPU"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by WebEyeX on 2007-12-12
Hi,
I am facing very strange problem for last two to three hours.Something is eating 55%-60% CPU continuously.My system performing really very slow because of this.I have checked System Monitor.Every process is sleeping.Only system monitor is consuming 3-4%.If no process is running than who is eating my 50% CPU??? Plz help me.

I also noticed that my system is taking more time to boot.My system configuration is as follows..

Intel 945GCNL board
Intel Pentium D 3.0 Processor
2 GB RAM
LG DVD RW


----------------------------

---

### Post by Flyingjester on 2007-12-12
open a terminal and type in TOP , what is the highest consuming process?

---

### Post by Anicka on 2007-12-12
Which version of Ubuntu are you using? Was it a clean install or an update from an earlier version?

---

### Post by WebEyeX on 2007-12-12
I have checked with 'top' command and it is kacpid(eating 85%) and kacpi_notify(eating 20%)
of CPU.Plz tell me how can i kill these processes.What is these all about??By the way i am using Ubuntu 7.10 and my system was running well just few hours ago.

---

### Post by WebEyeX on 2007-12-12
> **Anicka said:**
> Which version of Ubuntu are you using? Was it a clean install or an update from an earlier version?

It is a clean install.Dual boot with Win XP(first Installed).

---

### Post by natehall on 2007-12-12
Notte the process number of the offending program. Type in q to get back to the prompt in the terminal. The process number can also be revealed by typing in cp .  Just type in kill and then the process number. Of course your computer may act strange after that because you just killed something it needed.

---

### Post by WebEyeX on 2007-12-12
Solved this poblem.Just add 'acpi=off apm=off' boot parameters in grub menu list with 'kernel'.
I do this
$ sudo gedit /boot/grub/menu.lst  [Press Enter]
Grub menu list will be open in gedit.Now look for Kernel and add 'acpi=off apm=off' after 'ro'. 

Every thing is working fine.But i can not use acpi features now.

Thanks any way for your support.

---

