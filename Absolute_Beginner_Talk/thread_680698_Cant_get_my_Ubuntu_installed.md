---
title: "Cant get my Ubuntu installed"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by cooltrigger on 2008-01-28
hi guys,
i cannot install my Ubuntu. Whenever i start to click on the installation after booting from the CD after the indication bar is running some 20 seconds it will end in the shell command line with following message and blinking cursour: udevd-event[2326]:run program: '/sbin/modprobe' abnormal exit. i have already done following:
downloaded ISO file as torrent, burned ISO file correctly as an image, verified the file with md5sum and its ok (of course before i burned it)
checked that my boot sequence is only on CD ROM (any other boot devices disabled)
i also tried to start from the CD with the 'start ubuntu in safe graphics mode'
nothings works guys. what the heck i am doing wrong :-)
i am totally new to linux i have to mention.

---

### Post by philinux on 2008-01-28
Post your system specs. It could be the graphics card. There is an alternative text based installer that allows you to install then sort out the graphics driver. There's a tick box on the download screen to get this cd. It's not live though, just an installer.

---

### Post by njparton on 2008-01-28
What sort of hardware are you trying to install it on?

CPU, GPU, RAM, motherboard and hard drive(s) info please :)

---

### Post by bumanie on 2008-01-28
these two links are a bit technical, but they may be of help
[https://bugs.launchpad.net/ubuntu/+s...22/+bug/156428](https://bugs.launchpad.net/ubuntu/+s...22/+bug/156428)
[https://bugs.launchpad.net/ubuntu/+s...22/+bug/154591](https://bugs.launchpad.net/ubuntu/+s...22/+bug/154591)
looks as though there is a problem with seagate drives with some kernels.

---

### Post by philinux on 2008-01-28
Error page not found on both links.

---

### Post by cooltrigger on 2008-01-28
hi guys,
i have a AMD Athlon XP 2500+ (1.83Ghz), 512 Mb RAM and a NVIDIA Geforce4 MX 440 with AGP8x and 1x 80GB seagate and 1x 40GB seagate.

---

### Post by bumanie on 2008-01-28
> **philinux said:**
> Error page not found on both links.

If you were talking about my post, I just read both pages prior to posting them, that's how I knew it pertained to seagate drives.

---

### Post by philinux on 2008-01-28
If you are 100% sure on installing then I'd get the alternate text based installer and sort out the nvidia graphics after the os is installed.

---

### Post by cooltrigger on 2008-01-28
> **bumanie said:**
> If you were talking about my post, I just read both pages prior to posting them, that's how I knew it pertained to seagate drives.

hi bumanie,
thanks!! that seems to be the problem. but unfortunately both of your links are not working when i opened them. do you have any other links where i can find help on that problem?

---

### Post by philinux on 2008-01-28
Odd.  :(

---

### Post by bumanie on 2008-01-28
You're right they are not working from here for some reason??? Go to this link and they seem to open
[http://ubuntuforums.org/showthread.php?t=294773&page=2](http://ubuntuforums.org/showthread.php?t=294773&page=2)

---

