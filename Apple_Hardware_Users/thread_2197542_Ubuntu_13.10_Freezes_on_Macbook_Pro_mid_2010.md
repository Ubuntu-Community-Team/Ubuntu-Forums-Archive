---
title: "Ubuntu 13.10 Freezes on Macbook Pro mid 2010"
date: 2014-01-04
forum: Apple Hardware Users
---

### Post by samialafar on 2014-01-04
Hi everyone, I'm completely new at Ubuntu. 

I need some help to get my Ubuntu installed on a partitioned 1TB HDD on Macbook Pro mid 2010: 
**Processor**  2,4 GHz Intel Core 2 Duo
**Memory**  4 GB 1067 MHz DDR3
**Graphics**  NVIDIA GeForce 320M 256 MB
**Software**  OS X 10.9.1 (13B42)

Your Mac contains 2 memory slots, each of which accepts
a 1067 MHz DDR3 memory module.

So as you can see I got installed the latest OSX on my Mac, I made a partition dedicating 750GB to OSX HDD and 250GB to Ubuntu HDD, I used rEFIt to start up as a Dual boot. Everything went great, installed Ubuntu Linux 13.10 on Ubuntu specific partition, went great too.. Installed, with power connected, internet connected, everything was checked green and OK. 

After installation, Ubuntu after 3, 10 minutes freezes completely, display errors also...

Well, I installed VirtualBox on OSX, and then installed the same Ubuntu there, it went all great, without having no problems, but as you all know, is pretty much slower than installing it on the HDD. 

Could anyone help me please on my wrong process to boot up correctly Ubuntu? 

Will appreciate any help!

P.S: I don't have Kernel, well, in fact, i don't completely figure out what it is and what should I do whit it.

Thank you very much.

---

### Post by ZippyUbu on 2014-01-08
Hi - Have you installed any additional software after the initial Ubuntu install?
> After installation, Ubuntu after 3, 10 minutes freezes completely, display errors also...
Please post the error messages.

--
Zu

---

### Post by zircon_34 on 2014-01-08
Have a look at thread [http://ubuntuforums.org/showthread.php?t=1046568](http://ubuntuforums.org/showthread.php?t=1046568)
[COLOR=#000000][FONT=Comic Sans MS][SIZE=3][COLOR=Blue]
I installed, but Ubuntu won't boot / says "no bootable devices" / has a blinking cursor![/COLOR][/SIZE][/FONT][/COLOR]
[I](keywords: bug, installer, mbr, gpt, partition tables, no operating system)
There is and has been for a long time, [a bug in the Ubuntu installer]("https://bugs.launchpad.net/mactel-support/+bug/222126") that leaves your system unbootable after installing Ubuntu. It is easily repairable.
[Syncing Partition Tables]("http://ubuntuforums.org/showthread.php?t=767677")
[Reinstalling GRUB]("http://ubuntuforums.org/showpost.php?p=3303463&postcount=11")
[Supporting Technical Data for Bug]("http://ubuntuforums.org/showthread.php?t=980938")

[/I]I would try the option "syncing partition tables" in rEFit menu. If this works, I might also finally try to install and dual boot my mid 2010 macbook with Ubuntu!

I already tried to install Ubuntu on a Macbook air mid 2011 and couldn't boot anymore, so abandoned quickly this project... although I would be keen on running Ubuntu as dual boot instead a virtual machine...

---

