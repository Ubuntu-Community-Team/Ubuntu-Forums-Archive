---
title: "Quick questions on VMWARE"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-01-20
Hi,

I need to run several windows-only apps and therefore I'm considering VMWARE. There are mayn threads on this and with all these informations I'm a bit lost. Could anyone clrif the following points please:

- is there an XP boot process when launching XP in Vmware under Ubuntu or is XP desktop immediately available? I've seen screenshot of the XP boot screen in Vmware so I assume XP must be "booted" as well. What is then the benefice of using Vmware instead of a standard dualboot if XP needs to be booted in Vmware as well???

- I've read it is not yet possible to install a current XP install in Vmware. But is it not possible to create an image of my current XP install and install this image in Vmware by some means so that I don't need to reinstall all applications? I've spent months in customizing my XP install and don't really like the idea of starting everything again....

- when running XP in Vmware under Ubuntu, do I have all the XP security flaws? Do I need to install a firewall/antivirus in XP under Vmware? Or does a linux firewall/antivirus also protects 
the computer if I access stuff from IE under Vmware??

- In XP I usually run Notebook Hardware Control software to undervolt my laptop CPU. Can I use this software under Vmware too? Will this really undervolt my CPU although I'm still in a session under linux????

- I really need to be able to use the full potential of MSExcel 2003, especially VBA stuff. I've read that Crossover Office is able to run Excel 2003 but not all features are working (I think VBA is not fully supported...). Is Vmware a better alternative than Crossover to run MSOffice?? (I really cannot stand OOffice because I need full compatibility with MSOffice and I've lots of troubles with OOCalc and Excel compatibility for advanced features).

- imagine I uninstall OO from my Ubuntu system. I then install MSOffice in XP under Vmware and create an XLS file that I save on my harddisk. I close Vmware. If I double click on the XLS file in Nautilus, will this launch Vmware and automatically open the file in MSExcel or do I need to manually launch Vmware everytime and open files by launching the appropriate program?? In other words, are file associations possible between Ubuntu and Vmware???

- What's the best in performance/features: Vmware vs Virtualbox vs Qemu vs KVM (included in 2.6.20 kernel)?????? I really like the idea of KVM because I need to patch and compile a new kernel to get undervolting with linux-phc.

Thanks

---

### Post by shareMenaPeace on 2007-01-20
Hi,
well i have no idea what you mean with VMware, but from reading i think you might refer to an emulator.

There is wine a windows emulator which can run windows software (install and run).

Than you refer to special windows software MSWord, so let me tell you this:
You dont need any widows in most cases, because you can run either a wine emulation of windows to run the special software or you can simple use other software which does the same.

Example
If you want to write text, create Presentaions or do Calculations such as Exel than you can use OpenOffice whoich i really can recommend (It supports MSOffice file types too).

So actually i been a windows user quiet some time, but after i found ubuntu i really dont see any use anymore for windows. 

Of course you can use windows and linux both on 1 HDD but recommend to use just ubuntu.

Forget windows :)


Cheers

---

### Post by kilou on 2007-01-20
VMWare is a virtualization machine to run XP inside Ubuntu for instance. Wine or Crossover are fine but not fully compatible. I cannot use OpenOffice because I need the full potential of MSExcel: OOCalc has tons of errors when openeing an xls file with dates/time formats or macros and I cannot loose time with that. I need VBA for work and I have to be 100% compatible with Excel, not just 70-80%. For Word it would be mostly OK but definitely not for Excel.

CrossOver Office (specialized Wine version for office, non free) is quite good at running Excel 2003 but there are problems with VBA too. So I really need something like a virtualization machine and I'd like to know more about VMware or others (Qemu etc). For now I'm dualbooting but if VMware is better than dualboot I'd like to give it a try.

---

### Post by shareMenaPeace on 2007-01-20
Well not sure but did you tried version 2.x of OpenOffice?
The manual states xls is compatible,  but well if you tried and cant forget exel than good luck :)

---

### Post by kilou on 2007-01-20
> **shareMenaPeace said:**
> Well not sure but did you tried version 2.x of OpenOffice?
The manual states xls is compatible,  but well if you tried and cant forget exel than good luck :)

I'm running OO 2.0.4 and have tons of errors with Calc. Compatibility is good for basic things but forget macros or specific formats....and I use these all the time for work. 

I'm considering either VMware, Qemu and I've just seen that KVM will be included in the 2.6.20 linux kernel. Would it be better to compile the vanilla 2.6.20 kernel (I want to use undervolting and will need to patch and compile a kernel anyway) and use KVM instead of Vmware?? Please also look at the questions in the first post.

Thanks

---

### Post by MrKlean on 2007-01-20
My suggestion would be to jump in and test them both.   It seems you have too many restrictions that most here can only guess at.  I have no problems with OO, but it's seems you did in the past. Soooooo, do your own testing ; )  That's the only way to know for sure ; )

---

### Post by daverave999 on 2007-01-20
I'll try and answer your questions in order.

Yes there is an XP boot process, but once booted you can suspend it rather than shut it down and it opens a lot quicker on next use. Advantages I have found are:
-if you have the hardware working in Ubuntu then it will work straight away in XP without any drivers being installed.
-you can be using both Ubuntu and XP at the same time, as XP just runs in a window (can also be fullscreened though).
-no messing about with WINE settings

No idea about transferring current XP install sorry.

I believe it will still have the XP security flaws. I believe any firewall running on the host OS should protect the virtual one as it is running 'inside' it. If you don't want the virtual machine to get viruses then I expect AV will be needed, however, if you do get a virus then you will only have to remake the virtual machine or use a backup, rather than having hosed your entire machine.

I don't think the Notebook Hardware control will work, but don't know the terminology to explain why.

If you get the 'full potential' of MSExcel 2003 in XP normally, it should be available through VMware.

Any files stored on C:/ in VMware will stay within the XP image (?? terminology again...) that is used. Easiest way to transfer I have found is setting up some kind of network share in Ubuntu and in the XP machine. Also a USB flash drive could be used. So yes, you would need to manually start VMware and open the file in there.

I have no experience of the other virtualisation/emulation options you mention.

Basically, XP in VMware should behave exactly like XP normally would, but without direct hardware access because it is accessing it though linux. It's unlikely to work well with anything graphically intensive eg. games though.

I'm no expert, these are just my experiences so regard these as opinions rather than fact. I'd recommend giving VMware a go though as I found it straightforward to set up and use. For those Windows-only apps (I use mine for poker) it can be most useful.

---

### Post by anaconda on 2007-01-20
> **daverave999 said:**
> 

No idea about transferring current XP install sorry.
I have heard it is possible, but I always made my own images by installing them to the VMWare..

> I believe it will still have the XP security flaws. I believe any firewall running on the host OS should protect the virtual one as it is running 'inside' it. If you don't want the virtual machine to get viruses then I expect AV will be needed, however, if you do get a virus then you will only have to remake the virtual machine or use a backup, rather than having hosed your entire machine.

Actually that is wrong! Linux firewall wont protect your VMWare winXP at all. It is a completely separated running OS with its own (virtual) net-connection. VMWare is actually also used by the virusprotection comppanies to "collect" viruses from the internet. Eg. having an unprotected windows in the net. (the only difference is that with VMWare you can use "recovery points", which goes back to the previous instance of the wirtual machine ..eg before the virus..)

---

### Post by kilou on 2007-01-20
Thanks for these infos :) My idea is to make a really fast XP by stopping most services and startup programs. I don't need network support in XP, I'll access email and web from linux. However I'd like to access the ext3 partitions from XP in Vmware so that I can save files made with MSOffice there and then retrieve them from Ubuntu to attach them to emails for examples. Would it be possible to install Ext2IFS in XP under Vmware so that I can save an xls on my Ubuntu partition and directly access it from Ubuntu afterwards (to attach in an email)??

Also I read that unsupported hardware in Ubuntu won't work in XP in Vmware.......my Ricoh card reader works in XP but not in Ubuntu but will it work in XP under Vmware?????

I'll try all this for sure but still want some more infos, especially because I'm considering Qemu as well.

Thanks

---

### Post by jvc26 on 2007-01-20
Anything that doesnt work on ubuntu will not work on a VMWare PC as that is a virtual pc, running with the stuff to Ubuntu system recognises: Therefore if you have a card not recognised by Ubuntu the VMWare pc will be unable to run it.
Il

---

### Post by kilou on 2007-01-20
2 other questions before installing Vmware server:

- Can I compile a vanilla kernel and use it after having installed Vmware? I've read that vmware stopped working after updating the kernel or simply doesn't work with non-Ubuntu kernels (like vanilla ones). Is that right? If not what should I do in order to get vmware work again after compiling installing a Vanilla kernel?

- Is it possible to satisfactorily use MSN Messenger or Skype in XP under VMware to be able to make video calls to other PC with these systems? Is the sound/video/framerate acceptable or is this too slow or even not working??? (it seems there is not Linux native soft to make VIDEO calls to other Windows machine using Skype 2 or MSN Messenger)

Thanks

---

### Post by daverave999 on 2007-01-21
If you'd still like to run your current XP partition through VMware, [this]("http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm") popped up on digg.com about an hour ago. It's aimed at Gentoo users but it shows it can be done. Doesn't look like you'd need to change much to get it working on Ubuntu either.

[EDIT] Linked to mirror. Original is [http://oopsilon.com/Running-a-Windows-Partition-in-VMware](http://oopsilon.com/Running-a-Windows-Partition-in-VMware)
Or there's info from VMware for that matter [http://www.vmware.com/support/ws4/doc/disks_dualboot_ws.html#1046312](http://www.vmware.com/support/ws4/doc/disks_dualboot_ws.html#1046312)

---

### Post by kilou on 2007-01-22
Thansk Daverave999 =D>

---

### Post by 3rdalbum on 2007-01-22
Just a note: KVM requires a VT-enabled processor. Most processors don't have VT, so unless you're one of the lucky ones you will want to use Virtualbox or VMware.

I'd recommend Virtualbox myself - it comes as a .deb, so when you want to update your kernel all you've got to do is:

```
sudo apt-get install linux-image linux-headers
sudo dpkg -i VirtualBox_1.3.2_Ubuntu_Dapper_x86
```

---

### Post by PetePete on 2007-01-22
skype and msn do work for calls and webcam sessions. 

VMware is FANTASIC i'd strongly recommend it to anyone who has to run various windows reliant software. 

Although it does help if you've got a powerful PC, lots of RAM needed really. 1gb should be bare minimum. 

Your question about CPU frequency for a laptop, this wont happen in XP but your linux host will control this as it just see's the vmware as another program and will change your CPU accordingly.

---

### Post by kilou on 2007-01-24
VMware server seems to only support USB 1.1. Does this mean that my USB webcam will be too slow for an MSN session in VMware???

---

### Post by cleverselfreferentialname on 2007-01-27
Hello there. I ramble a lot here. Please excuse me.

> is there an XP boot process when launching XP in Vmware under Ubuntu or is XP desktop immediately available? I've seen screenshot of the XP boot screen in Vmware so I assume XP must be "booted" as well. What is then the benefice of using Vmware instead of a standard dualboot if XP needs to be booted in Vmware as well???

It does need to be booted, yes. My understanding though is that you can save a 'snapshot' of an OS in a particular state, so it might not be necessary. It also boots faster, in my experience, under VMware. The advantage is that you don't need to partition the hard drive to accommodate both systems. Linux can read and write to both NTFS and FAT32 filesystems, so you'd be able to read Windows partitions in Linux, but not Linux partitions in Windows, unless you installed the 3rd party driver from fs-driver.org, and that's not 100% safe. The general idea is that you store your media files on an NTFS or FAT32 partition so both operating systems can have access to them. Also, if dual-booting, put the OS on a separate partition than your files so nothing gets screwed up if you have to reinstall. It'd look something like this, on an 80GB drive:

Purpose              FS                 Size
Windows OS    NTFS            10GBs
File Storage     FAT32           55GBs
Swap               linux-swap     512MBs 
/ (Linux OS)    ext/xfs/jfs       14.5GBs

Swap is variable with the amount of RAM. I do 512 for 512, 768 for 256, and 256 for 1 gig. The old 'Three times your RAM' rule is terribly obsolete. Notice that I put ext/xfs/jfs for filesystem. JFS is easy on the processor, XFS swaps aggressively into RAM and is absurdly fast if you have a lot, but can lose data due to sudden loss of power, and ext3 is generally a good, stable choice. Ext2 for small partitions.

Unless, of course, you choose to do an install with just Linux. Your partition scheme would look like this:

Purpose            FS            Size
/boot                 ext3          512MB
swap            linux-swap    512MB
/home               ext3          64GB
/                        ext3          15GB

Now, the disadvantages to running VMware is that it makes a lot of services that eat up memory - even if you aren't running the guest OS at that moment. This is where Qemu and VirtualBox start looking a lot better.

> I've read it is not yet possible to install a current XP install in Vmware. But is it not possible to create an image of my current XP install and install this image in Vmware by some means so that I don't need to reinstall all applications? I've spent months in customizing my XP install and don't really like the idea of starting everything again....

If you spent months customizing your XP, you can spend much longer customizing your Ubuntu, and have a much better time with it :)

Now, in terms of actually answering your question, you could make a raw image of the partition. I'm not sure if VMware will read one of those, but Qemu can. Qemu is yet another virtualization solution. There are quite a few out there now. If you have a virtualization-compliant processor (probably not) you can run other OSes in Xen with little overhead. Same with KVM. If you don't have a virtualization-compliant processor, you could always do VirtualBox, my personal favorite software for this: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

I know for a fact that Qemu can do raw images. It might even be able to convert them into the VMware format. And maybe VMware is compatible with Qemu's format too (doubt it).

> when running XP in Vmware under Ubuntu, do I have all the XP security flaws? Do I need to install a firewall/antivirus in XP under Vmware? Or does a linux firewall/antivirus also protects 
the computer if I access stuff from IE under Vmware??

A firewall may or may not protect you in Linux. iptables (enabled by default in ubuntu, sudo apt-get install firestarter to get the frontend to iptables for easier configuration) will only protect you from malware executed inside of Windows if you tell it to filter outgoing traffic too. I'd advise using a firewall inside of Windows too. 

And yes, since VMs are mostly independent, you will need some sort of Antivirus. 
[http://force.coresecurity.com/](http://force.coresecurity.com/) < Let me plug my favorite windows firewall. Open source and ported from the paranoid-security-oriented OpenBSD.

>  In XP I usually run Notebook Hardware Control software to undervolt my laptop CPU. Can I use this software under Vmware too? Will this really undervolt my CPU although I'm still in a session under linux???? 

Undervolting is possible with Linux-PHC, and no, you probably won't be able to use the software in VMware.

>  I really need to be able to use the full potential of MSExcel 2003, especially VBA stuff. I've read that Crossover Office is able to run Excel 2003 but not all features are working (I think VBA is not fully supported...). Is Vmware a better alternative than Crossover to run MSOffice?? (I really cannot stand OOffice because I need full compatibility with MSOffice and I've lots of troubles with OOCalc and Excel compatibility for advanced features).

There are problems with cxoffice and some more advanced features of Office, yeah... You should run them in a VM, for sure.

>  imagine I uninstall OO from my Ubuntu system. I then install MSOffice in XP under Vmware and create an XLS file that I save on my harddisk. I close Vmware. If I double click on the XLS file in Nautilus, will this launch Vmware and automatically open the file in MSExcel or do I need to manually launch Vmware everytime and open files by launching the appropriate program?? In other words, are file associations possible between Ubuntu and Vmware??? 

File associations will not be handled like that. Sorry. cxoffice will do that for you, but it's not suitable for your tasks otherwise, so it looks like you'll be doing that manually :(

> What's the best in performance/features: Vmware vs Virtualbox vs Qemu vs KVM (included in 2.6.20 kernel)?????? I really like the idea of KVM because I need to patch and compile a new kernel to get undervolting with linux-phc.
I have not seen benchmarks for all of these, but KQemu + Qemu (that's a bitch to set up, at least it was for me) is as about as fast as VirtualBox is out of the box. Xen is fastest, but I think KVM (a very young project) will eventually overtake it, but, again, KVM and VirtualBox are only for VT-compliant processors.

> VMware server seems to only support USB 1.1. Does this mean that my USB webcam will be too slow for an MSN session in VMware??? 

Possibly, and perhaps your USB devices won't be seen at all, like what happened with my printer. But, don't worry, MSN Messenger 9 with webcam support works under Wine, and Mercury Messenger, a native Linux program, supports it too. It's just a question of how well your webcam works under Linux.

>  Can I compile a vanilla kernel and use it after having installed Vmware? I've read that vmware stopped working after updating the kernel or simply doesn't work with non-Ubuntu kernels (like vanilla ones). Is that right? If not what should I do in order to get vmware work again after compiling installing a Vanilla kernel? 
Yes and no. You have to compile a kernel that was compiled with the same version of gcc as the modules for VMware were. I don't know which that is, but I imagine it's gcc-4.0/gcc-4.1. Find out first and keep that in mind while compiling your kernel.

> Is it possible to satisfactorily use MSN Messenger or Skype in XP under VMware to be able to make video calls to other PC with these systems? Is the sound/video/framerate acceptable or is this too slow or even not working??? (it seems there is not Linux native soft to make VIDEO calls to other Windows machine using Skype 2 or MSN Messenger)  

Skype has a proprietary client for Linux. I think you can get it from the Canonical commercial repo.

> Thanks for these infos My idea is to make a really fast XP by stopping most services and startup programs. I don't need network support in XP, I'll access email and web from linux. However I'd like to access the ext3 partitions from XP in Vmware so that I can save files made with MSOffice there and then retrieve them from Ubuntu to attach them to emails for examples. Would it be possible to install Ext2IFS in XP under Vmware so that I can save an xls on my Ubuntu partition and directly access it from Ubuntu afterwards (to attach in an email)??

You need to set up services to access your files as though they were a network share. You need some form of networking in XP to do this. VMware should handle this for you with trivial configuration.

Good luck,
Paul

---

### Post by kvonb on 2007-01-27
> cleverselfreferentialname: But, don't worry, MSN Messenger 9 with webcam support works under Wine

Hmm, can you point me in the direction of where to download MSN9, and maybe also instructions for installing under WINE successfully?  I tried but I just got the "Live" version and it failed to install :confused:.

Thanks, KEv :)

---

### Post by kilou on 2007-01-27
Thanks Paul for this beautiful reply =D> I've finally decided to go with VirtualBox and it seems to work quite fine. However I did some tests with Skype and MSN Live install on the XP guest and I get 100%CPU usage with a laggy webcam. Skype exists for Linux but it has no webcam support. Otherwise I'm looking into Ekiga but most Windows users have Skype or MSN, not SIP.

Anyway VirtualBox seems the way to go for me now. You said that it is possible to create a virtual machine from a raw image of a partition in QEMU. I think that VirtualBox is based on QEMU so dou you know if it is possible to do that with VirtualBox as well??? I can't find anything about it, it seems VirtualBox only opens vdi files... The very best for me would be to have VirtualBox use my existing XP install as a virtual machine, like VMWare is able to do, because I think it is not yet time for me to get completely rid of Windows. I'll still need the dualboot for some time. But if I can at least built a virtual machine from a raw image of my XP install with VirtualBox, that'd be good. Do you know anything about it?

---

### Post by scfcpe on 2007-02-09
> **daverave999 said:**
> I'll try and answer your questions in order.

-you can be using both Ubuntu and XP at the same time, as XP just runs in a window (can also be fullscreened though).


Hi, I installed Windows XP with Vmware, and it´s working very well.

My only problem so far is that I can´t get the vmware Window to go fullscreen, when I click in the maximize button, it only maximizes the vmware Window, but the Virtual machine (Windows XP) remains the same size. 

Can some one please tell me how to fullscreen the WinXP virtual machine??

---

