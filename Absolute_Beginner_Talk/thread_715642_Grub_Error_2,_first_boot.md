---
title: "Grub: Error 2, first boot"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by ttchandra on 2008-03-05
Hello,
I have just tried to install Ubuntu onto a friends' Dell, but I keep getting an Error 2 message at GRUB loading stage 1.5. My intention was to install Ubuntu on the D drive and keep XP on the C drive, and so I selected "sda" on the installation screen instead of "sdb" (which contains Windows) and "sdc" (I don't know what that is). All of these drives were the same size, 232 MB or so.  I got this information from reading a few message boards.
While the installation went smoothly, I am now unable to boot either Ubuntu or Windows XP. Here is some information I think is pertinent:

I have something called 'Raid" on my computer, and when I go into its setup during the boot mode, I can only see one drive that is huge, a total of 450+ megabytes and when I hit enter to get details, it is made up of SATA0 and SATA1 which are 232.83 MB each. 

Now from doing a little digging, I think I have a theory about what is wrong: GRUB is looking for a partition to boot from which contains Ubuntu, but due to this RAID thing it looks like their is only one drive and so GRUB is confused. Of course, I'm not a computer person so I could be way off, haha!

I tried messing around with the BIOS settings as suggested on some other message boards, but there are only a few options there: Boot from utility partition (which can no longer be found), Hard Drive Diagnostic (everything comes up good) and Setup (which just confuses me). PLus the list of things to boot from, including the (1) hard disk and CD drive.

It is a very expensive computer, and I don't want to have to tell my friend that I screwed it up irreparably, so if someone could help me get Ubuntu running I would really appreciate it. Also, forgive me if I'm slow on the uptake.

---

### Post by ttchandra on 2008-03-05
Please help, this is a lab computer. If this is not the right place to find help can someone please direct me to another form of support? I'm feeling a little desperate.

---

### Post by criskat777 on 2008-03-05
1 What happens when you boot does it goes  to windows or the error comes up ?
2 can you boot to windows at all? 
3 have you tried to install grub (boot loader) with a Super Grub CD ?

---

### Post by logos34 on 2008-03-05
also, boot from the live cd and post the output from

sudo fdisk -l

---

### Post by ttchandra on 2008-03-05
1) When I boot, it won't go into Windows at all, it hangs on the GRUB error
2) I can't boot to Windows at all
3) I haven't. Where can I get the GRUB boot CD and what do I need to do to use it?

Here is the output from the Live CD

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29262   235046983+  83  Linux
/dev/sda2           29263       30394     9092790    5  Extended
/dev/sda5           29263       30394     9092758+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30393   244131741    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

---

### Post by logos34 on 2008-03-05
Grub apparently overwrote the windows bootloader on sdb or sdc, but because they're raid volumes got the bios location of the linux root partition wrong.

Try restoring the XP bootloader using [Super Grub Disk ]("http://supergrub.forjamari.linex.org/") (dl and burn to cd) or windows XP install cd (>**fixmbr**).  Then reinstall Grub, but this time write it to the MBR of sda, the linux disk (grub goes by default to whatever hard disk is the bios boot drive--hd0--at the time of installation).  Then see if you can boot to each separately by toggling the bios boot order.  
If you get to the grub menu screen, it will probably give you an error when you try to boot the ubuntu entry--press 'e' to edit and 'e' again on the 'root' line and change to (hd**0**,0).  If it works make the change permanent:

**gksudo gedit /boot/grub/menu.lst**

Change the 'groot' and root line to match.

---

### Post by adrian15 on 2008-03-07
> **ttchandra said:**
> 
Now from doing a little digging, I think I have a theory about what is wrong: GRUB is looking for a partition to boot from which contains Ubuntu, but due to this RAID thing it looks like their is only one drive and so GRUB is confused. Of course, I'm not a computer person so I could be way off, haha!


RAID!!!

Let's see. Can you please check somehow if it is a: [RAID 0]("http://en.wikipedia.org/wiki/RAID_0") or a: [RAID 1]("http://en.wikipedia.org/wiki/RAID_1")

If it is a RAID 0 I think you have a big problem. I actually do not know how a RAID 0 can be fixed but maybe you can fix it from a live cd.

If it is RAID 1 then I suppose (I am not sure of it) that you should install LINUX the same way (same partitioning) in all of the hard disk or the RAID so that it is the same thing in each hard disk.

Maybe if it is RAID 1 you can with dd (be careful about this command) clone your Linux disk and put it in the other disk (the one which does not have Linux yet).

I am not expert on RAID and I am not expert on RAID on Linux. If we suppose that your RAID setup is a RAID 1 then I can recommend you to try to boot your Windows from Super Grub Disk.

Try
```

Super Grub Disk With Help -> Windows -> Boot Windows

```
and:
```

Super Grub Disk With Help -> Windows -> Boot Windows from 2nd Hard Disk

```

If Windows is smart enough it will try to fix the RAID with the most updated copy (the linux one) or maybe with the RAID's most updated copy (not the linux one).

adrian15

P.S.: Maybe yours RAID is a hardware RAID... I do not know how they work :(

---

### Post by adrian15 on 2008-03-07
> **adrian15 said:**
> RAID!!!
Let's see. Can you please check somehow if it is a: [RAID 0]("http://en.wikipedia.org/wiki/RAID_0") or a: [RAID 1]("http://en.wikipedia.org/wiki/RAID_1")


If you boot from a Ubuntu Live CD can you enter into the different hard disk and read its partitions data? You just have to go to Places -> My PC (or something like this).

adrian15

---

### Post by ttchandra on 2008-03-09
I'm starting to get scared!

Here is what the details of my RAID array look like:
Array 1: NVIDIA STRIPE 465.66G
RAID MODE: Striped
Stripe width: 2
Stripe Block: 64K
Port SATA 0 Index 0 Capacity 232.83G
Port SATA 1 Index 1 Capacity 232.83G

Can you tell if it's a RAID 0 or a RAID 1 from this information?

I also tried to boot SuperGrub from a USB device, but when trying to install it onto the pendrive after untarring like this:
sudo grub grub>
device (hd3) /dev/sdc grub>
root (hd3,0) grub>
setup (hd3) grub> (this is where I encountered a problem, it said "Error 11: unrecognized device string". I tried the command "setup (hd3)" alone and it came back "Error 17: Cannot mount selected parition")
quit $ sync
And it returned "Probing devices to guess BIOS drives. This may take a long time."

After rebooting, I couldn't boot from the USB drive. I will try burning the CD instead to see if I have better luck, and let you know how that goes.

Also,  I can't find the contents of /boot/grub/menu.lst? I open terminal and type cat /boot/grub/menu.lst and it comes back "no such file or directory"

---

### Post by rabbit2502 on 2008-03-09
I'm pretty new to this but after reading your entire post thread this is what I think may ahve happened. Fromm what I've read in these forums UBUNTU would use sda for what windows calls the C: drive sdb would be the D: drive and sdc would be E:
It is possible when you installed UBUNTU the first time on sda you wiped windows out. hope I'm wrong but you may have to start from scratch. as for the raid thing I would open the box and find the primary hdd and disconect the others power cables temporarily.

---

### Post by adrian15 on 2008-03-11
> **ttchandra said:**
> I'm starting to get scared!

Here is what the details of my RAID array look like:
Array 1: NVIDIA STRIPE 465.66G
RAID MODE: Striped
Stripe width: 2
Stripe Block: 64K
Port SATA 0 Index 0 Capacity 232.83G
Port SATA 1 Index 1 Capacity 232.83G

Can you tell if it's a RAID 0 or a RAID 1 from this information?

If we trust wikipedia:
> **wikipedia]
A RAID 0 (also known as a stripe set or striped volume) 
[/quote]
then it is a RAID0 and you have a problem or THE problem.
[QUOTE=ttchandra said:**
> 
I also tried to boot SuperGrub from a USB device, but when trying to install it onto the pendrive after untarring like this:
sudo grub grub>
device (hd3) /dev/sdc grub>

Is /dev/sdc your USB device?
> **ttchandra said:**
> 
root (hd3,0) grub>
setup (hd3) grub> (this is where I encountered a problem, it said "Error 11: unrecognized device string". I tried the command "setup (hd3)" alone and it came back "Error 17: Cannot mount selected parition")
quit $ sync
And it returned "Probing devices to guess BIOS drives. This may take a long time."

Do you write:
```

root (hd3,0)

``` which it is ok or

```

root (hd3,0) grub>

``` which it is not ok.

> **ttchandra said:**
> 
After rebooting, I couldn't boot from the USB drive. I will try burning the CD instead to see if I have better luck, and let you know how that goes.

The CD is easier.
> **ttchandra said:**
> 
Also,  I can't find the contents of /boot/grub/menu.lst? I open terminal and type cat /boot/grub/menu.lst and it comes back "no such file or directory"
From the live cd you mean? It makes no sense you should boot with SGD and try its ** Linux -> Boot Linux** options, although it seems to be a RAID 0 I might be wrong and you might be lucky.

If you boot from the SGD CDROM do not forget to try the ** Windows -> Boot Windows from 2nd Hard Disk** option to see what does happen.

adrian15

---

### Post by ttchandra on 2008-03-11
I booted the SuperGrub CD, and I was unable to boot either Linux or Windows.  I played around with it extensively and continually got Error 15s or Error 17s.

When looking at my partitions, hda(hd0 in Grub)  shows a Linux OS hdb (hd1) shows a Windows OS, and hdC(hd2) is empty.

Right now I would just like to be able to boot anything. Will reinstalling Windows work? What is the next step?

---

### Post by adrian15 on 2008-03-11
> **ttchandra said:**
> I booted the SuperGrub CD, and I was unable to boot either Linux or Windows.  I played around with it extensively and continually got Error 15s or Error 17s.

When looking at my partitions, hda(hd0 in Grub)  shows a Linux OS hdb (hd1) shows a Windows OS, and hdC(hd2) is empty.

Right now I would just like to be able to boot anything. Will reinstalling Windows work? What is the next step?

If you still think that you can save your system (I do not think so from reading your last post) you should search some forums focused at RAIDs and ask there.

adrian15

---

### Post by ttchandra on 2008-03-11
Any help would be appreciated, any at all. Surely trying to install Linux on this computer hasn't *irreparably* damaged it, right?

Edit: There was nothing important on the computer, so recovering data is not a concern. I just need to be able to boot it with either OS

---

### Post by ibgeorgeb on 2008-03-11
It may be the MBR (Master Boot Record) is affected. I got the error 17 and when I tried to go past the install of Ubuntu or Windows the computer stalled with the error message. 

I put my Recovery CD in and copied MBR.exe to Q: then ran it. Afterwards, I got an error 22. 

Then I put the Ubuntu installation CD in and it ran Ubuntu. The install Unbuntu icon was on the desktop, I clicked it and got a clean install or Ubuntu. 

I lost my WindowsXP though. NO loss really. My seemingly dead computer is now happy in Ubuntu land again.

Hope this helps.

---

### Post by ibgeorgeb on 2008-03-11
Oops. I mean I copied the mbr.exe from my computer's recovery cd in Q:\ 

to

C:\


and then ran mbr.exe from C:\.

Rough day.

---

### Post by ttchandra on 2008-03-11
Ok. This would be a fine solution for me, the most important thing is that I didn't destroy this computer.

What is a recovery CD? I don't think we have one. Can I get one?

---

### Post by ibgeorgeb on 2008-03-11
The RECOVERY CD I used came with my laptop. It re-installs the computer to factory Windows install -- kinda like the day you first turned on you computer when you brought it home from the store.

I thought my computer was an electrical brick for two days. When I applied the "fix" it began to respond and didn't hang up at the "error 17" when powered-up.

If you don't have a recovery CD I wouldn't know where you could get one.

---

### Post by adrian15 on 2008-03-12
> **ttchandra said:**
> Any help would be appreciated, any at all. Surely trying to install Linux on this computer hasn't *irreparably* damaged it, right?

Edit: There was nothing important on the computer, so recovering data is not a concern. I just need to be able to boot it with either OS

Ok, if data recovery is not important.

I would try to disable RAID from the RAID utility and install ubuntu again.

adrian15

---

