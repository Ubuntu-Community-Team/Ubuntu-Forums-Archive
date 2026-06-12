---
title: "Maybe do I need to change distribution for serial management  or.."
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by lucat on 2007-10-15
... is it better to change the user (myself)?

I have this system on my laptop:
xubuntu-6.06.1-alternate-i386.iso

and these other packages installed:
minicom_2.2-5_i386.deb
setserial_2.17-43_i386.deb

I get the following output:

root@ubuntu:~# dmesg | grep tty
[   25.190490] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.203543] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   55.656688] ttyLTM0 at I/O 0x1c00 (irq = 3) is a Lucent/Agere Modem

root@ubuntu:~# setserial -g -a /dev/ttyS0
/dev/ttyS0, Line 0, UART: 16550A, Port: 0x03f8, IRQ: 4
        Baud_base: 115200, close_delay: 50, divisor: 0
        closing_wait: 3000
        Flags: spd_normal skip_test

Furthermore I think I installed  minicom correctly , a GSM module is connected to the serial port COM1 (it should be ttyS0), BUT if I dial AT and then I press Enter in the minicom window, after I launched minicom -s and set the parameters - nothing succeeds. I have connected also the serial port of my laptop toshiba with xubuntu distribution to another desktop PC running PortMon freeware tool, on windows, to monitor if there are some data out of the COM1 port. Nothing. What do I have to do to see OK answer to AT^M ? What do I have to do to see any data present on serial port if I manage minicom?

I selected Xubuntu because it seemed a good distribtuion for my laptop with 64 MB of RAM, but for serial management I needed to download more packages and without success (maybe for my absence of exeperience). Anyhow I think that I'll try to download the fedora core supporting 64 MB only for text and I hope in a different result (otherwise I'll know which was the reason of fault :-)...but if someone could help me also for xubuntu, thanks in advance

---

