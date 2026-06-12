---
title: "XP in VMWare on Ubuntu on Dual Disks- Partition/Installation Help"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by tikbjamin on 2007-03-09
Hi Guys,
I want to install XP on VMWare on my Dell Dimension 4550, P4, 2.4 GHz, 1.5 GB RAM, 80 GB/30 GB Disks.  I want the VM Installation to be on its own physical drive.  I will install Samba to gain access from Linux to the few shared files in XP.

I will appreciate any advice/help in setting partitions and making the VM installation.  Also, I will need to get the nvidia-glx drivers since this a dual monitor set-up.

Thanks,
TBJ

---

### Post by Delvien on 2007-03-10
> **tikbjamin said:**
> Hi Guys,
I want to install XP on VMWare on my Dell Dimension 4550, P4, 2.4 GHz, 1.5 GB RAM, 80 GB/30 GB Disks.  I want the VM Installation to be on its own physical drive.  I will install Samba to gain access from Linux to the few shared files in XP.

I will appreciate any advice/help in setting partitions and making the VM installation.  Also, I will need to get the nvidia-glx drivers since this a dual monitor set-up.

Thanks,
TBJ

you cannot use VMWare player/workstation to be pulled frrom a physical drive. It will be a file on the hdd itself.

Within VMware you can set up the file to be shared with the VMware, and then network the MS windows computer with your samba, kind of difficult, but its possible.

---

### Post by tikbjamin on 2007-03-10
Delvien:
Thanks for your reply.  I am not sure we understand each other.  I do not plan to have a Windows computer.  I have two separate physical drives in the one computer.  I wanted to place the VMWare on which I will install XP, on my faster 80 GB hard drive.  It appears that you are saying that it is not possible to place the VMWare files on this drive.  Am I understanding you clearly?  If so, Is there some way to achieve something even remotely close to this?

Thanks for your help.

TBJ

> **Delvien said:**
> you cannot use VMWare player/workstation to be pulled frrom a physical drive. It will be a file on the hdd itself.

Within VMware you can set up the file to be shared with the VMware, and then network the MS windows computer with your samba, kind of difficult, but its possible.

---

### Post by Delvien on 2007-03-10
> **tikbjamin said:**
> Delvien:
Thanks for your reply.  I am not sure we understand each other.  I do not plan to have a Windows computer.  I have two separate physical drives in the one computer.  I wanted to place the VMWare on which I will install XP, on my faster 80 GB hard drive.  It appears that you are saying that it is not possible to place the VMWare files on this drive.  Am I understanding you clearly?  If so, Is there some way to achieve something even remotely close to this?

Thanks for your help.

TBJ


No not at all.

Im saying theres no way for your VMware to write to the drive as though it had complete control of the drive itself, all VMware does is write to a folder which has the VMX files ( your virtual machine data. ) 

VMware ws/player does not mount a hard drive, instead uses a HDD that is mounted on the host (your Ubuntu) to write the files to.

Maybe its better if we speak by phone, i sent you a PM with my phone number.

---

### Post by tikbjamin on 2007-03-12
Delvien,
I have been away a little bit.  Don't know if this does anything but I had read that the vm's are to be stored in the /var folder so I just placed my /var and /home folders on the 80 GB drive.   Installation was without event.  The system files are on the smaller drive.   XP on VM is working fine; just need to fix my screen resolution in the vm now.

Thanks,
TBJ

---

