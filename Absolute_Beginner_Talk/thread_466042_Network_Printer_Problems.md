---
title: "Network Printer Problems"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by dodgerwv on 2007-06-06
I've taken an old office computer and turned it into a dual boot machine.  It's now the fastest computer in the office, but I'm having trouble trying to set up a network printer.

The network is set up on a local network, but I get nothing when I try to set up the Ubuntu machine.  I'm entering the IP address as the URL.    I get no response when I try to print a test page.  I would assume that I would get some sort of gibberish if it were a driver problem after making a connection to the printer.

By the way, the printer is a copier/printer Lanier 5622.  The computer is connected through a net gear router.

Am I missing something here?  Thanks in advance for the help and we're going to set up at least one other cpu in the office on Ubuntu once we figure out the printing.

---

### Post by lazyart on 2007-06-06
Can you ping the printer?

As a network printer have you tried it as TCP/Socket instead of IPP (default)?

---

### Post by dodgerwv on 2007-06-06
TCP/Socket did the trick.  Up and running with the printer.  Will probably make all three of the older machines in the office dual boot.  Can't believe the performance difference on the old cpus.  As a long time Mac user, it's nice to get away from Windows.:popcorn:

---

### Post by niceguy123 on 2008-01-24
> **lazyart said:**
> Can you ping the printer?

As a network printer have you tried it as TCP/Socket instead of IPP (default)?

1. How do I go about pinging the printer?

2. How do i go about TCP/Socket instead of IPP?

Thanks,

I have three computers networked (two Ubuntu on winxp) and a Brother HL5150D on one of the Ubuntus, at one point I had the printer configured and running on the network on all machines. But the box with the printer crashed and after a reinstalled Ubuntu I can't figure out how to get the printing system working again. The network is working, I can share files between all three.

---

### Post by niceguy123 on 2008-02-13
Hi,

I'm still stuck here. I've now tried following this [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_print_on_remote_Ubuntu_machine_from_another_Ubuntu_machine](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_print_on_remote_Ubuntu_machine_from_another_Ubuntu_machine)
and got as far as:

    * Client configuration 

```
 sudo cp /etc/cups/client.conf /etc/cups/client.conf.backup
 gksudo gedit /etc/cups/client.conf
```

It at first try wouldn't open anything and 2nd try opened an empty file,To which I added the line  ```
 ServerName 192.168.0.1
```

After that I can't even open administration>printing

Help.

Thanks.

---

