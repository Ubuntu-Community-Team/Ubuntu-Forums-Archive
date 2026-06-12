---
title: "what is vmware exactly?"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by odzx on 2006-09-24
can anyone please explain to me what exactly is vmware?
can it emulate windos os or do i need to sort of install an os into it?
the reason im asking this is becaus i cant make wine work right with hebrew on FF (cant write hebrew- get gibrish). i use ibm t23 laptop with a rhather small hd (20g) and cant afford installing a very big app (space wise).
i will appreciate it if any can tell me vmware can do as an alternative for wine and if not maybe help me fix this hebrew writing problem in FF with wine (all ready installed ms fonts and my local setting is set up for hebrew)
thanx

---

### Post by whizbaby on 2006-09-24
[http://en.wikipedia.org/wiki/VMware](http://en.wikipedia.org/wiki/VMware)

---

### Post by wildseven on 2006-09-24
hey, and welcome to linux!

well vmware is the way of the future i beleive heh~ others will disagree.

well anyway, vmware lets your run a virtual machine. that meanns, it's like having another computer, inside your computer. You can have what ever OS you like on it. So if you have linux and need windows, run VMware and install whatever version of linux you choose. 

it will be on it's own separate window( window not windows ).
if you have ever tried remote desktop, it will look like that. 

if you want to run high end things, like a video game, i suggest having atleast 2 gigs of ram.

good luck mate.

-wildseven

---

### Post by chrisfay on 2006-09-24
Has anyone had good success with VMware in terms of speed? I had considered running my servers within it but found it much to slow for production. I messed with the memory options within it as well but nothing made a difference.

I don't think it was hardware related as I am running it on a computer I built with:

Processor: AMD Athlon 64 3500+ 2.2ghz  

Motherboard: Asus A8N-e

Video Card: PNY Geforce 7600GT 256MB 128-bit GDDR3 PCI Express x16

Memmory: 2gig (4 dimm x 512mb dual channel) pc3200 

Harddrive: SATA Maxtor 300gb 7200 RPM 16mb Cache

I know its not the best, but I would think its good enough to run VMware decently....Any ideas?

---

### Post by ubuntuuser on 2006-09-24
I first made the mistake of assigning too much RAM to the VMs, which caused heavy swapping and slowed everything, including the VM and my system, to a crawl.
After reducing the RAM for each VM to roughly one third of my overall RAM, my windows VM runs smoothly.

---

### Post by chrisfay on 2006-09-24
Interesting...I think I had tried setting it at 512, 768 and 1gig.

It didn't really make much difference with any of those settings which I thought strange.

---

### Post by odzx on 2006-09-24
> **wildseven said:**
> hey, and welcome to linux!

well vmware is the way of the future i beleive heh~ others will disagree.

well anyway, vmware lets your run a virtual machine. that meanns, it's like having another computer, inside your computer. You can have what ever OS you like on it. So if you have linux and need windows, run VMware and install whatever version of linux you choose. 

it will be on it's own separate window( window not windows ).
if you have ever tried remote desktop, it will look like that. 

if you want to run high end things, like a video game, i suggest having atleast 2 gigs of ram.

good luck mate.

-wildseven

thanks wildseven, for the reply.
unfortunatly my old machine does not have this much ram. it seems very interesting though. i may give it a go, even for more simple and economic (memorywize) applications. anyway just to make sure: i would actualy have to instal the windows os within vmware. is that correct?
thanx again.

---

### Post by hyper_ch on 2006-09-24
Well, if you want to run windows I'd suggest running it on a physical partition ([http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition](http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition))
Then another good thing would be a dual processor... so one can take over the VM machine and the other the host... I guess that would be the perfect setup (however I don't have that... just a AMD2400 with 1GB DDR)... for what I use windows it's ok... but Photoshop really loads slowly.

---

### Post by docshawnc on 2006-09-24
Hi -
   The first time I used VM Server, I set it up for 256 meg of memory with an 8 gig HD and installed XP Pro (running on Ubuntu 6.06 P4 hyper-threaded with 2Gig Ram).  The system was dual boot at the time (XP and Linux) and seeing how well this worked (great btw) was enough to remove Windows as a boot option.
    Since that time, I have installed XP and Vista RC1 as VMs under Ubuntu with no speed issues unless I have them both running and performing tasks.  My only gripe is that I can't really do any gaming as ATI hasn't written a VM driver yet (it's only a matter of time though as VM is getting bigger and bigger)

---

### Post by tagra123 on 2006-09-24
> **chrisfay said:**
> Has anyone had good success with VMware in terms of speed? I had considered running my servers within it but found it much to slow for production. I messed with the memory options within it as well but nothing made a difference.

I don't think it was hardware related as I am running it on a computer I built with:

Processor: AMD Athlon 64 3500+ 2.2ghz  

Motherboard: Asus A8N-e

Video Card: PNY Geforce 7600GT 256MB 128-bit GDDR3 PCI Express x16

Memmory: 2gig (4 dimm x 512mb dual channel) pc3200 

Harddrive: SATA Maxtor 300gb 7200 RPM 16mb Cache

I know its not the best, but I would think its good enough to run VMware decently....Any ideas?

I got it running great on a machine with 1750 geode processor and 630 MB RAM.

To be honest for the software I run on it I can see no difference in speed at all.

In VMWare's settings assign the recommended amount of memory, and also if the vmware tools are not install it will not run as good as it does once they are installed. Fullscreen seems just as fast as windows on a windows only machine.

---

### Post by distroman on 2006-09-24
> **ubuntuuser said:**
> I first made the mistake of assigning too much RAM to the VMs, which caused heavy swapping and slowed everything, including the VM and my system, to a crawl.
After reducing the RAM for each VM to roughly one third of my overall RAM, my windows VM runs smoothly.
That pretty much happened to me.

> **tagra123 said:**
> I got it running great on a machine with 1750 geode processor and 630 MB RAM.

To be honest for the software I run on it I can see no difference in speed at all.

In VMWare's settings assign the recommended amount of memory, and also if the vmware tools are not install it will not run as good as it does once they are installed. Fullscreen seems just as fast as windows on a windows only machine.
Could you please clue me in on how you did that, maybe a howto you used?

One thing that confused me, was that vmware was running at boot and so killing the system fast. 
Which made me remove it pretty fast. 
Is vmware suppose to run all the time by default?

I was thinking it was because I only got 768 MB RAM.
I was really thinking of either run other distribution's or maybe win98 just for fun.

---

### Post by distroman on 2006-09-24
You are allowed to ask relatively dumb questions in the beginner section, right? :D

Because I got one more. 
Can you place the “virtual harddisk” on your /home partition?

[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)
I am going to give it a go again, wish me luck.

---

### Post by hyper_ch on 2006-09-24
Sure you can place it there...

I have mine on /home/hyper/vmware :)

You can get the vmserver software for free on the vmware site.

In order to install it I had to add another few things:

sudo apt-get install linux-headers-`uname -r` build-essential xinetd

If you are on breezy you also need:

sudo apt-get install gcc-3.4

I think that's all :)

---

### Post by gruffy-06 on 2006-09-24
> **wildseven said:**
> hey, and welcome to linux!

well vmware is the way of the future i beleive heh~ others will disagree.

well anyway, vmware lets your run a virtual machine. that meanns, it's like having another computer, inside your computer. You can have what ever OS you like on it. So if you have linux and need windows, run VMware and install whatever version of linux you choose. 

it will be on it's own separate window( window not windows ).
if you have ever tried remote desktop, it will look like that. 

if you want to run high end things, like a video game, i suggest having atleast 2 gigs of ram.

good luck mate.

-wildseven

I think you might be mistaken about playing video games using VMware products. They are primarily designed for business and graphics-intensive programs won't run at all because the virtual graphics adapter does not support 3-D acceleration.

---

### Post by ubuntuuser on 2006-09-24
> **distroman said:**
> 
One thing that confused me, was that vmware was running at boot and so killing the system fast. 
Which made me remove it pretty fast. 
Is vmware suppose to run all the time by default?
VMware doesn't run all the time. When you configure it using the vmware-config script, it creates some kernel modules. These modules enable the virtual network devices that VMware uses and are loaded when you boot your system, that's all.

---

### Post by gruffy-06 on 2006-09-24
Besides, there are different types of VMware products available, but none are licenced under an open source licence, such as the GPL.

VMware Workstation is one of the top virtualization solutions, allowing you to create and share virtual appliances with other users. You can run multiple VMs under a "team" configuration, run almost any x86 guest operating system and manage a network under a secure, isolated environment. The current price for VMware Workstation 5 is $189.00 ($99 for upgrades). This product is supported by VMware.

VMware Player allows you to run virtual appliances created with VMware's main products, like Workstation. Although it is free software (as in beer), creation of virtual machines is not possible. Therefore, you will have to get somebody who owns a copy of Workstation to create a virtual machine for you or use pre-built machines from the Internet. This application comes with NO technical support, whatsoever.

Some users are migrating to Xen (a paravirtalization technique) because it is open source and generally lots faster than VMware.

:)

---

### Post by distroman on 2006-09-24
Thanks for the help so fare.
Ran in to some trouble, hope someone can help me. 

```
What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-27-386/build/include] /lib/modules/2.6.15-27-386/build/include

Extracting the sources of the vmmon module.

tar: vmmon-only: Cannot mkdir: Input/output error
tar: vmmon-only/linux: Cannot mkdir: No such file or directory
tar: vmmon-only/linux/driver.h: Cannot open: No such file or directory
tar: vmmon-only/linux/driver.c: Cannot open: No such file or directory
tar: vmmon-only/linux/hostif.c: Cannot open: No such file or directory
tar: vmmon-only/linux/vmmonInt.h: Cannot open: No such file or directory
tar: vmmon-only/linux/vmhost.h: Cannot open: No such file or directory
tar: vmmon-only/common: Cannot mkdir: No such file or directory
tar: vmmon-only/common/memtrack.c: Cannot open: No such file or directory
tar: vmmon-only/common/memtrack.h: Cannot open: No such file or directory
tar: vmmon-only/common/task.c: Cannot open: No such file or directory
tar: vmmon-only/common/task.h: Cannot open: No such file or directory
tar: vmmon-only/common/vmx86.c: Cannot open: No such file or directory
tar: vmmon-only/common/vmx86.h: Cannot open: No such file or directory
tar: vmmon-only/common/hostif.h: Cannot open: No such file or directory
tar: vmmon-only/common/hostKernel.h: Cannot open: No such file or directory
tar: vmmon-only/common/phystrack.c: Cannot open: No such file or directory
tar: vmmon-only/common/phystrack.h: Cannot open: No such file or directory
tar: vmmon-only/common/cpuid.c: Cannot open: No such file or directory
tar: vmmon-only/common/cpuid.h: Cannot open: No such file or directory
tar: vmmon-only/common/hash.c: Cannot open: No such file or directory
tar: vmmon-only/vmcore: Cannot mkdir: No such file or directory
tar: vmmon-only/vmcore/driver_vmcore.h: Cannot open: No such file or directory
tar: vmmon-only/vmcore/moduleloop.c: Cannot open: No such file or directory
tar: vmmon-only/include: Cannot mkdir: No such file or directory
tar: vmmon-only/include/initblock.h: Cannot open: No such file or directory
tar: vmmon-only/include/machine.h: Cannot open: No such file or directory
tar: vmmon-only/include/modulecall.h: Cannot open: No such file or directory
tar: vmmon-only/include/vm_asm.h: Cannot open: No such file or directory
tar: vmmon-only/include/vm_asm_x86.h: Cannot open: No such file or directory
tar: vmmon-only/include/vm_asm_x86_64.h: Cannot open: No such file or directory
tar: vmmon-only/include/vm_time.h: Cannot open: No such file or directory
tar: vmmon-only/include/vcpuset.h: Cannot open: No such file or directory
tar: vmmon-only/include/x86.h: Cannot open: No such file or directory
tar: vmmon-only/include/x86types.h: Cannot open: No such file or directory
tar: vmmon-only/include/x86desc.h: Cannot open: No such file or directory
tar: vmmon-only/include/x86apic.h: Cannot open: No such file or directory
tar: vmmon-only/include/x86vt.h: Cannot open: No such file or directory
tar: vmmon-only/include/vmm_constants.h: Cannot open: No such file or directory
tar: vmmon-only/include/contextinfo.h: Cannot open: No such file or directory
tar: vmmon-only/include/uccostTable.h: Cannot open: No such file or directory
tar: vmmon-only/include/x86cpuid.h: Cannot open: No such file or directory
tar: vmmon-only/include/speaker_reg.h: Cannot open: No such file or directory
tar: vmmon-only/include/vmware.h: Cannot open: No such file or directory
tar: vmmon-only/include/vm_assert.h: Cannot open: No such file or directory
tar: vmmon-only/include/vm_atomic.h: Cannot open: No such file or directory
tar: vmmon-only/include/vm_basic_asm.h: Cannot open: No such file or directory
tar: vmmon-only/include/vm_basic_asm_x86.h: Cannot open: No such file or directory
tar: vmmon-only/include/vm_basic_asm_x86_64.h: Cannot open: No such file or directory
tar: vmmon-only/include/vm_basic_defs.h: Cannot open: No such file or directory
tar: vmmon-only/include/vm_basic_types.h: Cannot open: No such file or directory
tar: vmmon-only/include/vcpuid.h: Cannot open: No such file or directory
tar: vmmon-only/include/iocontrols.h: Cannot open: No such file or directory
tar: vmmon-only/include/pshare_ext.h: Cannot open: No such file or directory
tar: vmmon-only/include/cpuid_info.h: Cannot open: No such file or directory
tar: vmmon-only/include/vmware_pack_init.h: Cannot open: No such file or directory
tar: vmmon-only/include/vmware_pack_begin.h: Cannot open: No such file or directory
tar: vmmon-only/include/vmware_pack_end.h: Cannot open: No such file or directory
tar: vmmon-only/include/driver-config.h: Cannot open: No such file or directory
tar: vmmon-only/include/compat_highmem.h: Cannot open: No such file or directory
tar: vmmon-only/include/compat_pgtable.h: Cannot open: No such file or directory
tar: vmmon-only/include/compat_spinlock.h: Cannot open: No such file or directory
tar: vmmon-only/include/compat_uaccess.h: Cannot open: No such file or directory
tar: vmmon-only/include/compat_mm.h: Cannot open: No such file or directory
tar: vmmon-only/include/compat_file.h: Cannot open: No such file or directory
tar: vmmon-only/include/compat_wait.h: Cannot open: No such file or directory
tar: vmmon-only/include/compat_page.h: Cannot open: No such file or directory
tar: vmmon-only/include/compat_version.h: Cannot open: No such file or directory
tar: vmmon-only/include/compat_timer.h: Cannot open: No such file or directory
tar: vmmon-only/include/compat_semaphore.h: Cannot open: No such file or directory
tar: vmmon-only/include/compat_sched.h: Cannot open: No such file or directory
tar: vmmon-only/include/compat_kernel.h: Cannot open: No such file or directory
tar: vmmon-only/include/compat_completion.h: Cannot open: No such file or directory
tar: vmmon-only/include/pgtbl.h: Cannot open: No such file or directory
tar: vmmon-only/include/hash.h: Cannot open: No such file or directory
tar: vmmon-only/include/includeCheck.h: Cannot open: No such file or directory
tar: vmmon-only/autoconf: Cannot mkdir: No such file or directory
tar: vmmon-only/autoconf/geninclude.c: Cannot open: No such file or directory
tar: vmmon-only/autoconf/nopage1.c: Cannot open: No such file or directory
tar: vmmon-only/autoconf/skas1.c: Cannot open: No such file or directory
tar: vmmon-only/autoconf/epoll.c: Cannot open: No such file or directory
tar: vmmon-only/autoconf/setnice.c: Cannot open: No such file or directory
tar: vmmon-only/Makefile.normal: Cannot open: No such file or directory
tar: vmmon-only/Makefile.kernel: Cannot open: No such file or directory
tar: vmmon-only/README: Cannot open: No such file or directory
tar: vmmon-only/Makefile: Cannot open: No such file or directory
tar: Error exit delayed from previous errors
Unable to untar the "/usr/lib/vmware/modules/source/vmmon.tar" file in the 
"/tmp/vmware-config0" directory.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

I did sudo apt-get install linux-headers-`uname -r`

I am missing something easy? 
Do I need the kernel source? 
Is it because the kernel is unsupported?

Ubuntu Dapper 
kernel-2.6.15-27-386
vmware-server-distrib
vmware-mui-distrib


[http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=1625&sliceId=SAL_Public](http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=1625&sliceId=SAL_Public)
[http://www.vmware.com/community/thread.jspa?messageID=370579&#370579](http://www.vmware.com/community/thread.jspa?messageID=370579&#370579)

---

### Post by distroman on 2006-09-24
This is the howto
```
In which directory do you want to install the application's icon?
[/usr/share/pixmaps] <-- /usr/share/pixmaps

Trying to find a suitable vmmon module for your running kernel.

The module bld-2.6.15-23-i386server-Ubuntu6.06 loads perfectly in the running
kernel.
```


This is what I get
```
In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] /usr/share/pixmaps

Couldn't open "/tmp/vmware-config0/vmware-console-uri-handler.desktop".
Unable to create the .desktop menu entry file. You must add it to your menus by
hand.
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-27-386/build/include] /lib/modules/2.6.15-27-386/build/include

Extracting the sources of the vmmon module.

tar: vmmon-only: Cannot mkdir: Input/output error
```

---

### Post by distroman on 2006-09-24
Ok, so I did it. :D
```
Unable to untar the "/usr/lib/vmware/modules/source/vmmon.tar" file in the 
"/tmp/vmware-config0" directory.
```
Anyone know how come it didn't just do it?
Anyway ill be back with more trouble :D

---

### Post by tagra123 on 2006-09-24
> **distroman said:**
> That pretty much happened to me.


Could you please clue me in on how you did that, maybe a howto you used?

One thing that confused me, was that vmware was running at boot and so killing the system fast. 
Which made me remove it pretty fast. 
Is vmware suppose to run all the time by default?

I was thinking it was because I only got 768 MB RAM.
I was really thinking of either run other distribution's or maybe win98 just for fun.

The ram is easy to adjust, but I think you already found out how to do that. Its a menu item by the way. I believe it is under settings. You can also manually edit the virtual machine's VMX file.

If you use VM Workstation it would allow you to install the vmware tools with the click of a menu item same of VM Server. I installed the VMServer because it has  several features of the workstation. Pretty much the same install as the player, but a lot more settings + it will allow VMTools to install directly.

---

### Post by distroman on 2006-09-24
Thanks all for your advise.

Ubuntu Dapper
AMD Sempron 2300+
768 MB RAM
Nvidia Geforce FX 5200 128MB

VMware Server 1.0.1
Running Ubuntu 6.10 (Edgy Eft) Knot 3 in VWware.
5 GB virtual harddisk
256 MB RAM
[[IMG]http://img61.imageshack.us/img61/5857/eftyvmwarezt8.th.png[/IMG]](http://img61.imageshack.us/my.php?image=eftyvmwarezt8.png)
Running very smooth. 
To funny. :D

ps
sorry for hijacking the thread, learned alot though.

---

### Post by LookTJ on 2006-09-24
an os installed in another os aka virtual machine ware

---

### Post by k9brand on 2006-09-24
Is vmware ok with sound stuff as well?  I'm thinking of running cuebase and some vst plugins with it.  I'm going to give it a go unless somebody says they've had insanely crazy problems with it :)

thanks!

---

### Post by hyper_ch on 2006-09-25
> **gruffy-06 said:**
> VMware Workstation is one of the top virtualization solutions, allowing you to create and share virtual appliances with other users. You can run multiple VMs under a "team" configuration, run almost any x86 guest operating system and manage a network under a secure, isolated environment. The current price for VMware Workstation 5 is $189.00 ($99 for upgrades). This product is supported by VMware.
Well, VmWare Server is free (of charge): [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

---

### Post by hyper_ch on 2006-09-25
> **distroman said:**
> This is what I get
```
In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] /usr/share/pixmaps

Couldn't open "/tmp/vmware-config0/vmware-console-uri-handler.desktop".
Unable to create the .desktop menu entry file. You must add it to your menus by
hand.
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-27-386/build/include] /lib/modules/2.6.15-27-386/build/include

Extracting the sources of the vmmon module.

tar: vmmon-only: Cannot mkdir: Input/output error
```

Did you also apt-get build-essential and xinetd? Maybe you also need gcc-3.4

---

