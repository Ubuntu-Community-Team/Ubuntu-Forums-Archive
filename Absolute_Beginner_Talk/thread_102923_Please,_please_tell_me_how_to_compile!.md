---
title: "Please, please tell me how to compile!"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by rikoshay on 2005-12-13
Hi there,

I've just switched over to Ubuntu 5.10 from years of using Microsoft and I'm absolutely loving it! I'm still incredibly green but enjoying trying to use the command line and reconfiguring the system files with plenty or forum guidance.

Virtually everything worked straight away after installing the 2.6.12-10-amd64-generic kernel on my Acer Aspire 5021 WLMi *except of course* the broadcom wireless card. Ethernet is working fine and that's what I'm using now. I've had a good look through various sites and I realise I need to use ndiswrapper which I've downloaded without a problem through the synaptic package manager and I've got the correct bcwl5 driver for my card. However, it does absolutley nothing and I'm reasonably sure the problem is that I need to install a program called acer_acpi. Unfortunately it needs to be compiled and I'm having no luck managing to do it. I've trawled through loads of forums on how to compile programs but I'm just getting confused and it's failing to work.

The first two points in the install files (that's as far as I think I've got before it goes wrong) are:

1. You need the kernel sources (or kernel headers for your kernel)
installed to compile the driver.

2. Your kernel needs loadable module support with version information for
modules enabled. Usage of procfs is highly recommended.
If you want the driver to generate regular keyboard events using
kernel version 2.4 you need the input system of the kernel enabled
(Input core support AND keyboard support). In kernel version 2.6 all
needed functionality should be available by default.

I've dowloaded what I think are the relevant compiling tools using:
*sudo apt-get build essential*
I then realised I needed gcc compiler which I did from synaptic. The one I'm using is 4:4.0.1-3.
Then I tried to download the kernel sources and extract them to the correct folder using the commands:
[I]apt-get install linux-source-2.6.12
cd /usr/src
tar -xjf linux-source-2.6.12.tar.bz2[/I]

Followed by:
[I]cp /boot/config-`uname -r` /usr/src/linux-source-2.6.12/.config
cd /usr/src/linux-source-2.6.12
make oldconfig
make modules[/I]

However I note that I'm meant to ensure the link in /lib/modules/`uname -r`/build points to the /usr/src/linux-source-2.6.12 directory. It doesn't - I dont't have a file at that location called build. And I still can't compile anything.

Can anyone help out a newb and tell me where I'm going wrong.

Thanks!

---

### Post by sonny on 2005-12-13
I checked my configuration and I don't have the file you mention... but I still can compile, perhaps you went a little too far, try something simple, go to: [https://wiki.ubuntu.com/InstallingCompilers](https://wiki.ubuntu.com/InstallingCompilers) see if something there fixes your problem, after that you can just type "./configure", "make" and "sudo make install" in the directory in wich is the source. Perhaps you are having errors while compiling, dependencies or path errors, you should post the result of ./configure here in the post so people here can guide throughout all the compiling process should you have some errors.

---

### Post by rikoshay on 2005-12-14
OK, I'm clearly doing something fundamentally wrong. Here's what happens when I try ./configure:

rik@lappy:~/Desktop/acer_acpi-0.3$ ./configure
bash: ./configure: No such file or directory

I guess I haven't installed something although I have every package on [https://wiki.ubuntu.com/InstallingCompilers](https://wiki.ubuntu.com/InstallingCompilers).

Thanks for your help.

---

### Post by kaamos on 2005-12-14
./configure mean to exucute a file called "configure". So you have to be in the same folder with the sources you are trying to compile. And configure is not always needed, so there won't always be such a file. The sources almost always contain a README or an INSTALL file that will tell you what to do.

Build-essential and sometimes some specific versions of gcc are the packages that you need to use compilers. You will also sometimes need to install developement packages for some libraries, but the configure-script will inform you on this if you have something missing.

Good luck!

---

### Post by rikoshay on 2005-12-14
Thanks for clearing that up. So here's what happens when I try to use the make command.

rik@lappy:~/Desktop/acer_acpi-0.3$ make
awk: cannot open /lib/modules/2.6.12-10-amd64-generic/build/include/linux/versio n.h (No such file or directory)
gcc -I/lib/modules/`uname -r`/build/include -c -Wall -Wstrict-prototypes -Wno-tr igraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -DMODVER SIONS -DMODULE -D__KERNEL__ -o acer_acpi.o acer_acpi.c
In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/module.h:9,
                 from acer_acpi.c:41:
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h 

I realised during a previous attempt that I need the kernel sources to compile the driver so I did:

apt-get install linux-source-2.6.12
cd /usr/src
tar -xjf linux-source-2.6.12.tar.bz
cp /boot/config-`uname -r` /usr/src/linux-source-2.6.12/.config
cd /usr/src/linux-source-2.6.12
make oldconfig
make modules

but I haven't been left with a build file in my /lib/modules/2.6.12-10-amd64-generic.

Any ideas where I went wrong?

---

### Post by kaamos on 2005-12-14
I think the package you should install is headers.
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by Robocoastie on 2005-12-14
similar issue so piggy backing on this thread:

occassionally I run into a program that says something like "needs x.version but not found". And I know I have the library its asking for so along with the ./configure there's needed a ./configure with xxxx=etc.... I don't remember exactly how options like that are passed though or where the libraries hide. Usually its because I have a newer version of the lib. Is there a site with a tutorial for this kind of thing?

thanks!

---

### Post by rikoshay on 2005-12-14
Cheers kaamos! that sorted my compiling problem. Still can't get the wireless working under the 64bit kernel. I think it might be easier with the 32 bit. 

Thanks for all your help.:)

---

