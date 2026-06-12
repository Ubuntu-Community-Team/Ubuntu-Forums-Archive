---
title: "Tablet PC wont work"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by bullethead67 on 2007-07-30
I have been trying to get my fujitsu stylistic 5020D to work with Ubuntu. So far I have installed Ubuntu but I cant get the touchscreen to work. I dont know muckh about how to do this so im having a lot of trouble. I read this:
Wacom
[I]Configuring the serial port: Add set serial Setting up the system to use the pen was very easy. I found on the Internet that the port number is 0x220. To ensure that this is set on boot edit /etc/serial.conf and add the line:

/dev/ttyS2 irq 4 port 0x220 autoconfig.[/I]

I dont have a file named serial.conf in etc/

so what do I do? I like ubuntu but I really like my pen so i keep using windows more than i like.

---

### Post by Rocket2DMn on 2007-07-30
Have you followed any guides to set it up.  If so, which ones?
[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) sounds like a good place to start.
Also note that the directory is /etc/ not etc/
the initial / denotes the root of the file system whereas simply putting in etc/ looks for the folder "etc" in the current directory.

---

### Post by bullethead67 on 2007-07-31
That doest seem to doanything either.
I tried the live CD on my wifes tablet and it works fine. hers is a 5010 and mine is a 5020D they are almost identical so I dont understand why mine doesnt want to work. especially since it is newer.

---

### Post by bcw on 2007-08-01
I just posted my howto for a ST5032D.  Perhaps the hardware is similar enough?

[http://ubuntuforums.org/showthread.php?t=514842]("http://ubuntuforums.org/showthread.php?t=514842")

---

