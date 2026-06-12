---
title: "Ubuntu as a virtual machine?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by K'Jev on 2007-03-09
Hello,

I've never used any form of Linux before, but here's what I am attempting:

I want to run Ubuntu as a virtual machine on an XP Home system. The idea is to use it as a virtual server to test PHP scripts on my websites. I'd rather just post them on the internet, but I don't have access at the moment.

I have virtual Machine installed. I've downloaded Ubuntu, but I have no clue where to go from there. Can anyone help me?

K'Jev

---

### Post by etank on 2007-03-09
> I have virtual Machine installed.
Not sure what virtual machine software you are running here. Is it VMWare, Virtualbox, other. Really no matter what it is you should be able to put the Ubuntu CD in the drive and power on the VM. The VM will then boot to the Ubuntu CD. If you are using the LiveCD version of Ubuntu then once it boots there is an icon on the desktop that says install. Click on it and it will walk you through the steps needed to complete the install.

---

### Post by K'Jev on 2007-03-13
I'm running VMware. I had Ubuntu downloaded with a jump drive and simply copied the install files to my hard drive. I will try to get it burned to a CD but I have no burner.

Thanks for the advice

K'Jev

---

### Post by Ooops.at on 2007-03-13
> **K'Jev said:**
> I'm running VMware. I had Ubuntu downloaded with a jump drive and simply copied the install files to my hard drive. I will try to get it burned to a CD but I have no burner.

Thanks for the advice

K'Jev

If you have an iso or if you can make an iso out of your ubuntu install files then you can simply create a new virtual machine (not with vm-player, though) and go to the settings (VM->Settings). There you direct the CD-ROM drive of this virtual machine to the iso and you are rdy to go, no need to burn anything physically to a cd...

hope this helps (I happen to be doing this right now, just waiting for the download to finish)

PS: I dunno what VMware you are using exactly and which Ubuntu you want to install. I went for 6.06 since my VMware (5.5.3) supports 6.10 only experimentally... (I found reports on the net that 6.10 should work as well, but I don't want to run into too much trouble since I am a complete Linux-noob...)

---

### Post by Strider42 on 2007-03-14
I run 6.10 and have an XP Pro virtual machine.  99% perfect I think - there is an issue with 6.10 and USB.  Odd stuff happens and the only way I can get my USB devices recognized is if I plug in a USB memory stick, and then everything else fires up.  I don't believe this is an issue in 6.06

---

### Post by FredB on 2007-03-14
VMWare is - in some points - the best software for virtual machines. I used VMWare 6 beta with Ubuntu 6.10 in order to test Ubuntu Feisty before moving to feisty for my everyday OS.

---

### Post by hyper_ch on 2007-03-14
If you just want to run php scripts at home then you are better off installing apache2, php4/5 in your windows environment... there's no real reason to have a vm running for that task.

However if you want to explore Linux / Ubuntu then go ahead :)

---

### Post by richbarna on 2007-07-26
> **FredB said:**
> VMWare is - in some points - the best software for virtual machines. I used VMWare 6 beta with Ubuntu 6.10 in order to test Ubuntu Feisty before moving to feisty for my everyday OS.

Hi FredB ! Long time no see, I thought you went over to BSD ?

By the way, here is a link to some good VMware howto's written by Resa. [http://modfree.org/index.php?board=25.0](http://modfree.org/index.php?board=25.0)

---

### Post by rich.bradshaw on 2007-07-26
I would just use xampp in Windows.

[http://www.apachefriends.org/en/xampp-windows.html](http://www.apachefriends.org/en/xampp-windows.html)

Just install, run it and turn apache on.

Website files go in C:\xampp\htdocs

Easy!

---

### Post by be4truth on 2007-07-26
Virtual box is free of charge. VM Ware - onloy the limited version is free (no USB, file sharing and sound).
I have Ubuntu running as a guest as well as host with vitual box. Runs fine.

---

### Post by hyper_ch on 2007-07-26
VmWare hast USB support.. at least the server edition, which is free, has... and also filesharing and sound :)

---

### Post by popch on 2007-07-26
You can use VMWare Workstation or Vmware Player for your purpose. Workstation costs some money and is probably way too powerful for what you have in mind. Vmware Player is free.

There are several ways to install Ubuntu in a virtual machine. 

Since you only want to run a LAMP server, the most obvious solution I can see consists of downloading a LAMP 'virtual appliance' from the VMWare Web Site. Virtual appliances are pre-configured ready-to-run virtual machines. You download it, move it to the proper directory and run it, preferably with the free VMWare Player.

---

