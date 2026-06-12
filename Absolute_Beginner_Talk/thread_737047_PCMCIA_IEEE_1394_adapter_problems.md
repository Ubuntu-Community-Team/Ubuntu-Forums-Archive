---
title: "PCMCIA IEEE 1394 adapter problems"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2008-03-27
Hello there! I'm trying to get my VIA PCMCIA 1394 cardbus adapter work on my ubuntu 7.1. It's a working card as I've already tested it on a windows machine.

I read these topics : [http://ubuntuforums.org/showthread.php?t=336511]("http://ubuntuforums.org/showthread.php?t=336511")
[http://ubuntuforums.org/showthread.php?t=40039]("http://ubuntuforums.org/showthread.php?t=40039")

which help me a bit, but did not solve the problem.  When I plug the device, dmesg does not display anything, it seems that its not being loaded at all.

gscanbus prints the following:

couldn't get handle: Permission denied
This probably means that you don't have raw1394 support in the kernel or that
you haven't loaded the raw1394 module.

 ls -l /dev/raw1394
crw-rw---- 1 root disk 171, 0 2008-03-27 09:29 /dev/raw1394

 lsmod | grep 1394
raw1394                31096  0 
ieee1394               96312  1 raw1394


That's all information I got. Could someone help me out on this?

Regards

---

### Post by PCFascist on 2008-03-30
Quote:

Do you have write access to /dev/raw1394 ? Try ls -l /dev/raw1394 If it belongs to user "root" and group "disk", you probably don't. In this case:
sudo chmod 777 /dev/raw1394 or even
sudo chown name-of-your-user /dev/raw1394 Then try your firewire again.

[http://ubuntuforums.org/archive/index.php/t-200546.html](http://ubuntuforums.org/archive/index.php/t-200546.html)

---

