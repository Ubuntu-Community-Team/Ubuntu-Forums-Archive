---
title: "Installation failed - GRUB error 15"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by RogerD on 2007-03-02
Hi

Tale of woe here.

I'm trying to instal 6.06 on a new PC. At first all went well. The live CD worked fine, so I opted for install - this is a linux-only system. About 80% of the way through the installation, I got the message, "We're sorry, but the installation has failed" - never had that before. I had another go, but got the same result. I thought, maybe there was a fault on the installation CD, so I tried the DVD that comes with Ubuntu. Not a good idea. The end result was the message:

GRUB Loading stage 1.5
GRUB loading, please wait..
Error 15


When had tried the installation CD, I now get the same result.

I love using Ubuntu, but this is a real downer.

Can anybody suggest how I might get my lovely new PC up and running?

Regards

Roger D

---

### Post by mahiyar on 2007-03-02
Can you give me some more details like what mobo, harddisks (pata/sata), your installation options (where did u ask your grub to load). Error 15 in stage 1.5 is this [B]
15[/B] : **"Error while parsing number"** This error is returned if GRUB was expecting to read a numbur and encountered bad data. (Like file not found etc)

---

### Post by Sitix on 2007-03-02
An important thing is: is the hd still new, isn't it damaged, demagnetized, etc.?

I had the same problem, a long time ago, on a really old computer. Check the following things: are there more hard disks than one in the computer? Is the hd's well functioning? Did you configure your BIOS properly, let it auto configure your harddrives if possible. By checking those things, I found out that there was a configuration error. And even later, I found out the hd was almost at the end of its life.

---

### Post by RogerD on 2007-03-02
You asked
Can you give me some more details like what mobo, harddisks (pata/sata), your installation options (where did u ask your grub to load)?

This is a new PC. The motherboard is an Asus M2NPV-VM, and the harddisk is sata.

I don't remember being asked to install grub in any particular location. I thought it automatically went into the master boot recordd

Hope this helps

Roger D

---

### Post by webofunni on 2007-03-02
roger do you have windows or any other operating s/m in your pc then check your harddisk for errors

---

### Post by n3gbz on 2007-03-02
All my grub errors have come down to a defective 

/boot/grub/menu.lst 

file in my Ubuntu partition.   I usually boot up with my Knoppix disk and manually edit the menu.lst file. 

Make sure the menu.lst file exists and is readable. If you post it here, we can look for possible errors.  

A list of grub errors is available here:

[http://orgs.man.ac.uk/documentation/grub/grub_14.html#SEC109](http://orgs.man.ac.uk/documentation/grub/grub_14.html#SEC109)

---

### Post by RogerD on 2007-03-02
I don't have another OS - trying to move away from the dual boot system I've used to date, and I don't have A Knoppix disk.

---

### Post by n3gbz on 2007-03-02
I use Knoppix because I am familiar with it and have used it as a rescue tool many, many times. 

Using the liveCD, you should be able to mount your Ubuntu partition and view /boot/grub/menu.lst which Should look something like this. 

> 
#comment
title		Ubuntu, kernel 2.6.20-9-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-9-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-9-generic
quiet
savedefault

---

### Post by RogerD on 2007-03-03
Trouble is, I can't use the liveCD anymore. When I insert the liveCD in my DVD drive, my system goes straight to the error 15 message. I assume that I've got a partial, faulty installation on my hard disk, so my system tries to boot from that.

I really appreciate your interest in my problem.

Best regards

Roger D

---

### Post by confused57 on 2007-03-03
> **RogerD said:**
> Trouble is, I can't use the liveCD anymore. When I insert the liveCD in my DVD drive, my system goes straight to the error 15 message. I assume that I've got a partial, faulty installation on my hard disk, so my system tries to boot from that.

I really appreciate your interest in my problem.

Best regards

Roger D
You've probably already done this, but make sure your cd/dvd drive is set in bios to boot before your hard drive...on a newly built pc, with no os, the cd drive would probably boot even if the hard drive was set to boot before the cd drive.
Also, if you have access to another pc, download & burn a copy of the Super Grub Disk(500 kb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
the SGD "may" be able to boot your Linux, if it installed properly, other than a grub failure.

---

### Post by RogerD on 2007-03-03
Good advice

I've changed my BIOS setting so that, as you suggest, the cd/dvd has boot priority over the HD. The goods news is that LiveCD is now working again, and, given that the installation starts by erasing the entire HD, I've probably sorted out the GRUB problem.

The bad news is that, my installation is still failing. It happens shortly after the 'copying files' stage, and this is the message I get:

We're sorry; the installer crashed. Please file a new bug report at [https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug) (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/installer/syslog, /var/log/syslog


Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 264, in run
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 553, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code 1; see /var/log/installer/syslog and /var/log/syslog

I've sent the requested files off as requested, but I find it hard to believe this is a fault with the installer software - more likely something amiss with the way my PC has been set-up.

You've been very helpful and encouraging so far. Do you have any suggestions?

Best regards

Roger D

---

### Post by confused57 on 2007-03-03
You might want to download the alternate install cd, it "may" work.

Also, you could boot up the live cd, open a terminal, check the output of:
```
sudo fdisk -l
```

---

### Post by RogerD on 2007-03-03
The alternate install CD looks a bit of a last resort, but I may yet give it a go. In the meantime, here's the output of sudo fdisk -l. Doesn't mean much to me, but nothing seems amiss.
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19092   153356458+  83  Linux
/dev/sda2           19093       19457     2931862+   5  Extended
/dev/sda5           19093       19457     2931831   82  Linux swap / Solaris

Disk /dev/sdb: 32 MB, 32768000 bytes
3 heads, 32 sectors/track, 666 cylinders
Units = cylinders of 96 * 512 = 49152 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         667       31983    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(1000, 2, 32) logical=(666, 1, 30)
ubuntu@ubuntu:~$

---

### Post by confused57 on 2007-03-03
I mentioned the alternate cd, because it looks like there are some problems with the live cd ubiquity installer, which the alternate cd doesn't use...the alternate installer is really quite easy and you actually have more control of the installation.
Here's some excellent screenshots of the alternate cd:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

You "sudo fdisk -l" shows that Ubuntu "appears" to be installed on sda...maybe you could try reinstalling grub with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

What is sdb listed in the output you posted?

---

### Post by RogerD on 2007-03-03
OK

I'll give the alternate CD a try, but what's wrong with Ubuntu appearing to be installed on sda?

Should I try and reinstall grub before trying the alternate CD?

---

### Post by RogerD on 2007-03-03
OK
I've tried re-installing grub. This is what I got:

    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found

grub>

Which does make a sort of sense. When my installation first failed, Error 15 is what I got.

I've also made a copy of the alternate CD. It's getting late here, in the UK, and I'm going to leave giving this a go until tomorrow, Sunday. If it works, won't that solve my GRUB problem? As I understand things, the installation starts by erasing all my HD, including the bit that holds GRUB.

I'm hopeful that I'll crack this tomorrow. Many thanks for all your help up till now.

Best regards

Roger D

---

