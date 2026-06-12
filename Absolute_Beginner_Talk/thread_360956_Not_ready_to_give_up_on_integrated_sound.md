---
title: "Not ready to give up on integrated sound"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2007-02-13
I have a new motherboard with integrated sound. So far Ubuntu (dapper) has not detected it. I found linux drivers for the Realtek ALC655 AC97 A2.3 integrated sound and would like to install the drivers to see if the integrated sound would then be detected. Would I somehow use the apt-get command to download the drivers, or do I just click the download link, save to file, then use a command to install? What say you, Ubuntu Guru?

---

### Post by Albi on 2007-02-13
Post link to driver, what kind of file is it?

---

### Post by tronica on 2007-02-13
I've put a link to the driver you need. and it this zip file is a readme with install instructions.

[http://itransfer.ath.cx/linux_v23.zip]("http://itransfer.ath.cx/linux_v23.zip")

---

### Post by paydaydaddy on 2007-02-13
Step 2 from the above link read me file is: 

"Step 2. Turn on sound support (soundcore module, default turn on)"

how is this done?

---

### Post by sacedric on 2007-02-13
Be careful. I think I did what the drivers wnated me to do and look what happened.......
[http://ubuntuforums.org/showthread.php?t=361005](http://ubuntuforums.org/showthread.php?t=361005)

Good luck!!

---

### Post by paydaydaddy on 2007-02-13
Here is the complete "read me" file. It might as well be written in ancient hebrew for all it means to me. Can any body help me decipher this?



The source code copy from [www.alsa-project.org](www.alsa-project.org).      ver:A2.3

Linux Source Code for ALC audio codec



Installation:

This Source Code is from [www.alsa-project.org](www.alsa-project.org).

For driver installation, please follow below steps. 



Step 1. unzip source code

        tar xfvj alcsound.tar.bz2



Step 2. Turn on sound support (soundcore module, default turn on)



Step 3. Complied source code

	a. ./configure

	b. make

	c. make install

	d. ./snddevices



Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution

 	(Please refer to the attached modules.conf)



Step 5. reboot your machine



Note: 	1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt 
		in the alcsound.tar.bz2.

	2. Kernel Version must be 2.2.14 or later.

	3. All mixer channels are muted by default. You must use a native

		or OSS mixer program to unmute appropriate channels.

	4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.

	5. The driver added to support the SPDIF functoin. 	

	6. Suggest use alsamixer to control mixer function. you can find it in the alsa-utils-0.9.4 ([www.alsa-project.org)](www.alsa-project.org)).

---

### Post by paydaydaddy on 2007-02-15
Back to the top

---

