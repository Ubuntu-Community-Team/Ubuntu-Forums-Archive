---
title: "serial port error w/ wine"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by tordan on 2007-09-17
I installed "Wine" in order to operate a data collection
program for our temperature datalogger unit at work, but I'm having some
problems.

When the program ("Data Acquisition" by Extech Instruments) is booting
up it comes up with :"COM Port ERROR: Unexpected internal error" then proceeds to open the
program after I hit "OK". The only problem I can detect is that it will
not connect with the device via the motherboard's built in Serial port.  I have changed the location that the program looks for the port in (com1-com4) and still no luck finding the
device (or at least communicating with it). Is there a component of Wine
that I need to change or install to get it to recognize the port system
for Lynux?

Let me know if you need more info.

Thanks in advance.

---

### Post by JustAboutRealJAR on 2007-09-18
your serial ports are most likely in the /dev directory. This is the most common naming convention and how it relates to windows (and therefor wine)

/dev/ttyS0 - com1
/dev/ttyS1 - com2
/dev/ttyS2 - com3
/dev/ttyS3 - com4

Here's the thing: you have to make sym links in the ~/.wine/dosdevices folder like so:

```
$ ln -s /dev/ttyS0 ~/.wine/dosdevices/com1
```

I don't think you need to be root to do this... if so, just throw a sudo in at the beginning

repeat as necessary for each serial port. I have been having problems with my serial port in wine also so please let me know how this works out for you. I'm looking for more information on the topic.

---

### Post by JustAboutRealJAR on 2007-09-18
Here's a link to the thread where I posted my problem with the serial port:
[http://ubuntuforums.org/showthread.php?t=553888]("http://ubuntuforums.org/showthread.php?t=553888")

---

### Post by tordan on 2007-09-18
Thanks for the info.
I did as you suggested:
>  sudo ln -s /dev/ttyS0 ~/.wine/dosdevices/com1

There is still no communication between the device and the program. The dialog box: "COM Port ERROR: Unexpected internal error" is no longer coming up when I open the program.

Here is the output on a command another forum suggested trying. I have no idea what it is telling me:

```
user@user-desktop:~$ setserial -g /dev/ttyS[01]
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3

user@user-desktop:~$  dmesg | grep tty
[   16.065546] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.068906] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.104529]   hash matches device ttyd8
[   16.104559]   hash matches device ttyab
```

Thanks again for the help. I checked out your problem; I wish I had some input, but I got nothing.

---

### Post by JustAboutRealJAR on 2007-09-18
> /dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4

I read somewhere in my search that changing the UART to 16550 (from 16550A) solves many people's problems.

It had something to do with buffers and how devices claim to be 16550A when they don't **truely** support it.

> /dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3

I find this to be much scarier... it doesn't even know which UART is there. If you're using com2 then this is almost certainly the problem.

I would switch to com1 and/or set the UART via

```
$ sudo setserial /dev/ttyS1 uart 16550
```

---

### Post by tordan on 2007-09-18
Now I have:

```
user@user-desktop:~$ setserial -g /dev/ttyS[01]
/dev/ttyS0, UART: 16550, Port: 0x03f8, IRQ: 4
/dev/ttyS1: No such device

```

Still no communication between device and comp. I am set on Com1 in the program.

---

### Post by JustAboutRealJAR on 2007-09-18
do you have a way of testing the com port outside of wine?

if so... I would reccomend doing that to rule out a problem with the hardware or detecting/configuring the hardware

---

### Post by tordan on 2007-09-18
I don't have any other devices that use a serial port.  I can see if any one I know has something, but I cant think of anyone off hand.

---

