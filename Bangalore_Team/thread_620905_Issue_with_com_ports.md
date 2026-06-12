---
title: "Issue with com ports"
date: 2007-11-23
forum: Bangalore Team
---

### Post by SrikanthG on 2007-11-23
Hi,

I am facing a strange issue, with Ubuntu 6.10 and 7.04, most of the com ports are not getting detected on my CPU. I have around 10 comports but only 4 were detected. Strangely 6.06 detected all the ports.
Can any one help me in solving the issue.

 
iris@MAICAB02:~$ dmesg | grep ttyS
[   31.728750] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.729218] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   31.729623] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[   31.730014] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[   31.730863] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.731477] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   31.732079] 00:0b: ttyS2 at I/O 0x3e8 (irq = 11) is a 16550A
[   31.732765] 00:0c: ttyS3 at I/O 0x2e8 (irq = 10) is a 16550A
iris@MAICAB02:~$

Thanks,
Srikanth
[email]srikanthgandu@gmail.com[/email]

---

