---
title: "input/output error  with setserial"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by aestr on 2007-02-01
I have been trying to get tablet support for my Gateway cx2724 laptop. Part of this requires using setserial to automatically set the serial port speed to 38400 baud.

I did a fresh install of Edgy and got setserial, but as soon as i tried to use it I got the following error:
```

kyle@Toby:~$ sudo setserial /dev/ttys0 -a
/dev/ttys0: Input/output error

```


I edited /var/lib/setserial/autoserial.conf as follows:
```

/dev/ttyS0 uart 16550A port 0x03F8 irq 4 baud_base 38400

```

And I also tried creating an /etc/serial.conf
```

/dev/ttyS0 uart 16550A port 0x03F8 irq 4

```

dmesg gives the following
```

kyle@Toby:~$ dmesg | grep tty
[17179571.172000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179602.428000] ttyS0: LSR safety check engaged!
[17179602.428000] ttyS0: LSR safety check engaged!
[17179612.176000] ttyS0: LSR safety check engaged!

```


After this I still get the same error. I am fairly new to linux, Ubuntu in particular. Any help to get my serial to automatically load with the speed given above would be greatly appreciated. Thanks for your time!

---

