---
title: "What linux-header to install for Virtualbox?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by pmueller on 2007-03-19
Hi

I am trying to diagnose the problems that I am having getting Virtualbox to run. I have come across a post that seems to address my problem. For the curious, the post is at [http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html](http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html)

According to the manual for Virtualbox, I need to make sure my correct Linux-headers are installed.  Under Synaptic I find that I have no such headers installed and there are 17 choices. How do I know which is the right choice to install?

I have an AMD 1600+ XP. That is a 686 machine. Right? My menu.lst list under /boot/grub says that my kernal is :  title		 Ubuntu, kernel 2.6.17-11-386

What should I do?  There are different linux-header packages for 386 and 686 machines. I installed Edgy as an upgrade from Dapper via a CD install.

The error after I try to run a PCLinux iso file under Virtualbox is: 
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1908 VERR_VM_DRIVER_NOT_INSTALLED

Thanks,

Paul in NH

---

### Post by Kateikyoushi on 2007-03-19
Install the same headers as your kernel.
This is which kernel you use.

```
uname -a
```

---

### Post by pmueller on 2007-03-19
Oh, I just ran in terminal: uname -r.  My results were: 2.6.15-26-386. However, in Synaptic I see linux-mages2.6.15-23-386 and linux-image2.6.17-10-386 installed. so should I install linux-header-2.6.17-10-386?

What about my 686 machine?

Thanks,
Paul

---

### Post by scxtt on 2007-03-19
if you're happy using the 2.6.15 kernel, stick w/ it and install those headers, if you want to use 2.6.17 (if it's installed, you're just not running it) reboot and select using that kernel @ boot, then install the headers for it via apt-get/aptitude/synaptic ...

you should see 386 and 686 if using dapper repositories, but AFAIK, edgy uses "generic" instead of differentiating b/t the two ...

---

### Post by Kateikyoushi on 2007-03-19
Actually from edgy the official is the generic kernel because the differences between different versions are close to nothing. So the 386 kernel will do fine.

---

### Post by pmueller on 2007-03-19
Hi Again,

Synaptic does not give any "2.6.15" linux-headers as choices. There all 2.6.17-10 or 2.6.17-11. I take it that I should use the generic ones, since I think I am running Edgy, but now I am not so sure that I am really running Edgy 100%.  

I am using a multiboot system with Mepis and Suse and I am actually using Suse's boot loader. I do not seem to have a choice running good old dapper and edgy through from the boot menu. 

Perhaps my upgrade disk is a less than perfect method for an install. Should I have wiped out my old Ubuntu with a completely new Edgy install?

OK, I will try this generic linux-header for 2.6.17-11. I got dial-up. It might be slow seeing if this solves my Virtualbox problems.

Thanks For Now. I might have to report back in an hour or tomorrow.

Paul in New Hampshire

---

### Post by scxtt on 2007-03-19
yes, dapper repos will have "2.6.15" kernels and edgy repos will have "2.6.17" kernels ... you don't "have to" reinstall if your system is working satisfactorily ...

i would boot and make sure you're using (an (already?) installed) 2.6.17 kernel - then install the headers for that kernel ...

should sort you out fine :)

---

### Post by pmueller on 2007-03-19
Hi 

I saw your message and decided to stop my download of the linux-header2.6.17-11 generic and reboot. The Suse bootloader says that I am booting into 2.6.15-26. yet I do have the edgy program additions that dapper did not have like Tomboy and others..

If I should download the 2.6.15 headers, how can I see these in Synaptic? Synaptic only gives me the 2.6.17 choices (10,11, and 50)?

I am getting a bit confused. Looking down the synaptic list, I seem to have other linux 2.6.15 and 2.6.17 files installed. 

It's better to be cautious about this install. Would the wrong header cause problems?

Paul

---

### Post by scxtt on 2007-03-19
no, the wrong headers won't make much difference ... but if you start mixing and matching too much, it can get "messy" ... you basically want to make sure /usr/src/linux points to the current kernel you're running ... my /usr/src/ directory looks like this and i'm running the following kernel:
```
[font=courier]:> ll
total 908K
lrwxrwxrwx  1 root src    40 2007-03-05 22:21 linux -> /usr/src/linux-headers-2.6.17-10-generic
drwxr-xr-x  3 root src  4.0K 2007-03-06 01:31 modules
drwxr-xr-x 19 root root 4.0K 2006-10-25 10:06 linux-headers-2.6.17-10
drwxr-xr-x  4 root root 4.0K 2006-10-25 10:06 linux-headers-2.6.17-10-generic
-rw-rw-r--  1 root root 641K 2007-03-06 01:31 fglrx.tar.bz2
-rw-r--r--  1 root src  241K 2007-03-06 01:34 fglrx-kernel-2.6.17-10-generic_8.34.8-1+2.6.17-10.33_i386.deb

:> uname -r
2.6.17-10-generic[/font]
```so basically, ANY references to /usr/src/linux will point to my 2.6.17-10-generic kernel ... this is pretty standard and generally done by default ...

again, if your /etc/apt/sources.list has entries for edgy and NOT dapper, you WILL NOT SEE entries for kernel 2.6.15 (that kernel is not in the repos for edgy) ...

so you've got 2 routes:

1. change your /etc/apt/sources.list and make sure it's using the dapper repos - then make sure you get the headers for a 2.6.15 kernel
2. install, and make sure you're running, one of the 2.6.17 kernels - then get the headers for that kernel ...

---

### Post by pmueller on 2007-03-26
Hello,

It's been a while, since I had night meetings and a trip to Pennsylvania. Thank you very much for helping me use Virtualbox successfully. I tried a PCLinux iso file and I could run it.

My Suse distro for some reason did not create a Ubuntu boot for edgy by for my 0lder version of Dapper. I did not understand that the old version of dapper would still be hanging around after an edgy install. So I edited the menu.lst in the grub boot directory of Suse to get the edge kernel available to choose and eventually I got Virtualbox to work.

You all did an outstanding job helping this newby.

Paul

---

