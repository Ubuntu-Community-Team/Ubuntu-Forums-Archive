---
title: "VMware-like app?"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-04-04
Is there a program that is for Ubuntu, that is open source, that is similar to VMware workstation? (VMWare is virtual machines, IE: Install an OS on a virtual machine)

---

### Post by FakeOutdoorsman on 2007-04-04
[VirtualBox]("http://www.virtualbox.org/") may do what you want.  It is open source.

---

### Post by hyper_ch on 2007-04-04
and VmWare Server is also available for linux for free :)

---

### Post by Peter1234123 on 2007-04-04
I have a question about this also: if my friend were to buy VMware, he also gets the source code (you buy it and they give BINS and Source) would it be legal for him to give me the source, and me to compile it?

---

### Post by hyper_ch on 2007-04-04
Peter: That depends on the licence that comes with the source code...

But as said, VmWare Server and VmWare Player are free to get from vmware. The player is in the repos and for the server you have to register yourself and then you will get serials... with the server you can then create your own virtual machines...

The alternative is virtualbox... it's also quite good although I have a few issues with it (1) usb isn't working that great there (2) it doesn't like my swiss germany keyboard layout --> but then I think virtualbox is more lightweight compared to vmware.

---

### Post by Recked on 2007-04-04
Hello,

How does a person get past the below error:

FATAL: No bootable medium found! System Halted

VirtualBox installed just fine on Feisty but even with the Dell provided XP Service Pack 2 restore disk I can't get XP to boot/install.

Any help would be appreciated.

thank you

---

### Post by hyper_ch on 2007-04-04
Well, a restore disk is not an installation disk... I tend to think that restore disks work in conjunction with hidden disk partitions... not sure....

---

### Post by xpod on 2007-04-04
I`m not sure that you can use a "restore disk" to install an XP VM but i could be wrong and you might just need to unmount your cd-rom so that virtualbox can see it instead.....

You need to then go into the VB settings to the cd-rom tab and select your cd drive from the dropdown box.

Still not sure about that restore disk though??

---

### Post by feed_sparky on 2007-04-04
I used my restore disk for my laptop (HP dv5215us)  to install XP media center edition using VirualBox, and it worked/s just fine. Even used the SP2 disk they (HP) sent me to update XP to SP2.

---

### Post by Recked on 2007-04-04
I thought I would be able to use it as it contains all the files from a normal XP install disk, but neither XP nor any other linux distro will work for me. I just tried a Pardus 2007.1 iso disk and got the same error. I checked and the cd rom is mounted and it is the first device in the boot order etc.

I am not sure exactly and the documentation is a little sparse for this type of error.

thanks

---

### Post by lapsey on 2007-04-04
i use vmware server on ubuntu all the time. it is open source.

[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

---

### Post by Recked on 2007-04-04
Oh never mind I am completely brain dead at this point. I just assume that VirtualBox saw the first installed cd drive, but it appears it does not see my Plextor and instead sees only the cd rom drive and not the cdr drive............

Oh bother..............

Pardus worked now to XP...

thanks for making me think

---

