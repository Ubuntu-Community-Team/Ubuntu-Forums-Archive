---
title: "Hardware information?"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by ree on 2005-11-20
Hi there,

I'm pretty stuck trying to fix a CD-RW/DVD drive issue.  My drive is behaving a bit sluggy (ie, copying stuff off the drive is incredibly slow, about 250k/s!) and I guess it's because I'm not using the right driver for the device.  What app/command do I use to find out what my drive is, or what my system thinks it is? I'm used to using something like the device manager in Windows to check that kind of info, and have no idea what the linux equivalent is?

It's a Sony Vaio PCG-FR700 laptop, if that helps.

Would appreciate anyone that can point me in the right direction :(

---

### Post by SavageBeginner on 2005-11-20
```
sudo apt-get install hardinfo
```
```
hardinfo
```

---

### Post by ree on 2005-11-20
[QUOTE=SavageBeginner]```
sudo apt-get install hardinfo
```
```
hardinfo
```[/QUOTE]

Cool, thanks for that.  All installed:

```
ree@SPANKY:~$ hardinfo
Translation module registered.
HardInfo 0.3.6
Copyright (c) 2003 Leandro Pereira <leandro@linuxmag.com.br>

This is free software; you can modify and/or distribute it
under the terms of GNU GPL version 2. See http://www.fsf.org/
for more information.

```

.. but when I launch it from K menu, it tries to launch and then disappears.

:confused:

---

### Post by suRoot on 2005-11-20
Make sure DMA is enabled on the drive.

See this thread:  [http://ubuntuforums.org/showthread.php?t=86603&highlight=hdparm+cdrom+dma]("http://ubuntuforums.org/showthread.php?t=86603&highlight=hdparm+cdrom+dma") for details.

---

