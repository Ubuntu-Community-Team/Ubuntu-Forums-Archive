---
title: "Where is Install app?"
date: 2005-09-10
forum: Absolute Beginner Talk
---

### Post by martiniano on 2005-09-10
I'm losing my mind. I love Ubuntu. I've installed it on my old Gateway Solo 5300 and it runs great. But installing it on my beige G3 is driving me crazy. 

Why isn't there just an "Install" application? Why do I have to yaboot this, bootx that and toss quik in between? What the hell is miBoot? vmlinux and vmlinuz and .gz and .tar and .crap? I just want to plug the CD in, run an install or setup program and answer questions. Why is to so freakin' difficult?

Pardon my frustration, but I have litterally spent 100 hours trying to install Ubuntu on this system and everytime I solve a problem 5 more pop up.

---

### Post by aysiu on 2005-09-10
According to [these instructions](https://wiki.ubuntu.com/Installation/PowerPC), it is just answering some questions. You really need to deal with Yaboot and vmlinuz and all that if you're trying to repartition and do a dual-boot.

---

### Post by N'Jal on 2005-09-11
.tar and .gz are compressed fiels. Akin to .sit

---

### Post by N'Jal on 2005-09-11
Right now i have more time to post. There is no install.app for Linux, it is closer to the way windows handles packages, however in a more secure way. You will need a few things.

The file you wish to install in .deb format
The root password
The commandline

Right if you are from the Mac word the command line is identical its the same program, it's called bash.

So lets make a few assumptions here, you have open the commandline, and you have your .deb file in your home directory, not in any subfolders etc.

All you type is ```
sudo dpkg -i <packagename>.deb
``` and that should be it.

Alternativly all the software written for ubuntu has been put on a server that you can access and download from, open synaptic search for any package you want, right click it, check install then click the apply button

---

### Post by aysiu on 2005-09-11
My impression was that martiniano was talking about installing Ubuntu, not installing applications. If it's installing applications, you can just use Synaptic:

[http://www.psychocats.net/essays/winuxinstall.php](http://www.psychocats.net/essays/winuxinstall.php)

---

### Post by N'Jal on 2005-09-11
oh sorry then.

---

