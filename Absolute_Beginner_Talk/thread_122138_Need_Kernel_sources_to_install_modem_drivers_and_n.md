---
title: "Need Kernel sources to install modem drivers and no apt-get"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by alpy wright on 2006-01-26
uname -r tells me my kernel is version 2.6.12-9-386

I have been told (from the irc channel #ubuntu in freenode) that I should get my kernel sources from [www.kernel.org](www.kernel.org), then get a patch file from packages.ubuntu.org.

In looking on the web debian users say you should get your kernel direct from debian; on the irc channel they say the kernel sources are on the ubuntu install cd - I can't see them there.  I can't find the kernel sources on the ubuntu packages website.

I look on [www.kernel.org](www.kernel.org) and the closest thing I see is:

[http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.12.6.tar.gz](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.12.6.tar.gz) 

I can't understand why the kernel sources there only go up to 2.6.12.6 (no -9-386) and in fact they go up to 2.6.13.  I was going to load and install the closest one but I am such a beginner.

I want the kernel really so I can rebuild it - maybe I need to alter modules and suchlike.  By the way how do I display my kernel settings so I can make sure I have ATM and such like (will the kernel be ready configured for an ADSL) modem.  I need the sources also because the make of my adsl modem driver requests them. 

By the way I'm trying to get a conexant accessrunner ADSL pci modem working anyone who has any ideas further than whats contained here: 

[http://ubuntuforums.org/archive/index.php/t-1906.html](http://ubuntuforums.org/archive/index.php/t-1906.html) 

please tell me.

8-[

---

### Post by alpy wright on 2006-01-26
I haven't got apt-get because I can't connect yet.  I need the kernel sources to 
install the adsl modem drivers to connect.

---

### Post by Sutekh on 2006-01-26
[QUOTE=alpy wright]uname -r tells me my kernel is version 2.6.12-9-386
[/QUOTE]
I'd get it from here (Ubuntu Packages)

[Ubuntu -- linux-source-2.6.12]("http://packages.ubuntu.com/breezy/devel/linux-source-2.6.12") - For **all** 2.6.12 kernels.

and

[Ubuntu -- linux-headers-2.6.12-9-386]("http://packages.ubuntu.com/breezy/devel/linux-headers-2.6.12-9-386")

[QUOTE=alpy wright]
I want the kernel really so I can rebuild it - maybe I need to alter modules and suchlike.  By the way how do I display my kernel settings so I can make sure I have ATM and such like (will the kernel be ready configured for an ADSL) modem.  I need the sources also because the make of my adsl modem driver requests them. [/QUOTE]
In /boot, there will be a config file; like linux-2.6.12-9-386.config or similar.  Make a copy of this somewhere to read you config off (maybe print, but its probably quite long)

---

### Post by alpy wright on 2006-01-26
Thanks for the quick reply.  I will install that kernel and the headers.

Thanks for the info about the configuration also.

---

### Post by az on 2006-01-26
To compile the module, you will only need the headers.  You will need to install gcc-3.4 (which depends on gcc-3.4-base and cpp-3.4).  If you compile the full kernel, you will not need the headers.

If I were you, I would just use the precompiled kernel and use the headers to build the extra module.

In that case, just download and install those three package.  You will also need to install build-essential, but that is on the cd.

---

