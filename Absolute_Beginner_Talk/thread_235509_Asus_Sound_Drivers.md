---
title: "Asus Sound Drivers"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by d4rk on 2006-08-13
How do i innstall the asus sound drivers ?

Here is a link to the drivers that fits my motherboard (Asus K8N SLI Deluxe):
[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)

After I've downloaded the file, i extract it at my desktop, and a folder is created. I read the innstall guide, where i read the following instruction:

> The source code copy from [www.alsa-project.org](www.alsa-project.org).      ver:A2.7

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

### Post by d4rk on 2006-08-13
*Bump*
Ok, let me put my question a bit simpler. If I want to innstall a program, I use the add software tool in ubuntu. I want winRar, but it's not in the list, so I visit theyr site, and download the Linux Version of the program. When it is downloaded, I end up with a .gz file on my desktop. I know I am supposed to write something ala "sundo..." in the console. But how do I innstall these files ?

---

